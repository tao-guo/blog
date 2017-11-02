---
layout: post
title: BoltDB Review
categories: oss
published: true
author: Tao
---

<!-- TOC -->

- [Architecture](#architecture)
- [Data Structures](#data-structures)
    - [DB](#db)
    - [meta page](#meta-page)
    - [freelist](#freelist)
    - [leafpage](#leafpage)
    - [bucket](#bucket)
    - [nodes & inodes](#nodes--inodes)
    - [cursor](#cursor)
- [IO Path](#io-path)
- [Transactions](#transactions)
- [Limitations](#limitations)
- [Further Readings](#further-readings)

<!-- /TOC -->

## Architecture

[Bolt-db](https://github.com/boltdb/bolt) is a minimal kv DB with MVCC and transactions, 4K golang LOC, based on [lmdb](http://www.lmdb.tech/doc/). It is being used in Shopify and Heruko production systems.

The architecture is like below, based on my own understanding:

![boltdb]({{site.baseurl}}/img/boltdb.svg)

## Data Structures

### DB

```go
// DB represents a collection of buckets persisted to a file on disk.
type DB struct {
	meta0    *meta
	meta1    *meta
	rwtx     *Tx
	txs      []*Tx
	freelist *freelist

	batchMu sync.Mutex
	batch   *batch

	rwlock   sync.Mutex   // Allows only one writer at a time.
	metalock sync.Mutex   // Protects meta page access.
	mmaplock sync.RWMutex // Protects mmap access during remapping.
  ...
}
```

### meta page
  - Two roots: page 0 and page 1
  - The page with higer txid wins

  ```go
  type page struct {
    id       pgid --> prevent mis-directed writes, similar to RAID
    flags    uint16
    count    uint16 --> items, means different things for different types
    overflow uint32 --> count-1, so it can hold big keys
    ptr      uintptr --> point to meta
  }
  ```

  ```go
  type meta struct {
    magic    uint32
    version  uint32
    pageSize uint32
    flags    uint32 --> 0x04

    root     bucket --> root+sequence 16bytes, seq for bucket uniq id

    freelist pgid
    pgid     pgid --> last available pgid
    txid     txid
    checksum uint64
  }
  ```

### freelist
  - page, flags: 0x10
  - mem:

  ```go
  // freelist represents a list of all pages that are available for allocation.
  // It also tracks pages that have been freed but are still in use by open transactions.
  type freelist struct {
      ids     []pgid          // all free and available free page ids.
      pending map[txid][]pgid // mapping of soon-to-be free page ids by tx.
      cache   map[pgid]bool   // fast lookup of all free and pending page ids. --> for reporting and checking
  }
  ```
  - on disk:
    - p.count: # of pgids
    - pgids: uint64[] -- sorted
    - or 0xFFFF, first as count

### leafpage
  - page, flags: 0x02
  - p.count: keyN

  ```go
  // leafPageElement represents a node on a leaf page.
  type leafPageElement struct {
      flags uint32
      pos   uint32
      ksize uint32  0x08--"MyBucket"
      vsize uint32  0x20-- 32?
  }
  ```

### bucket
  - leafPageElement
  - vsize: bucket

  ```go
  type bucket struct {
    root     pgid   // page id of the bucket's root-level page
    sequence uint64 // monotonically incrementing, used by NextSequence()
  }
  ```

### nodes & inodes

  ```go
  // node represents an in-memory, deserialized page.
  type node struct {
      bucket     *Bucket
      isLeaf     bool
      unbalanced bool
      spilled    bool
      key        []byte
      pgid       pgid
      parent     *node
      children   nodes
      inodes     inodes
  }

  // inode represents an internal node inside of a node.
  // It can be used to point to elements in a page or point
  // to an element which hasn't been added to a page yet.
  type inode struct { //--> not the same as file system's inode
      flags uint32
      pgid  pgid
      key   []byte
      value []byte
  }
  ```

  - bucket is a b+tree
    - node level, in memeory
    - reblance, spill, split during tx commit

### cursor

```go
// Cursor represents an iterator that can traverse over all key/value pairs in
// a bucket in sorted order.
//
// Keys and values returned from the cursor are only valid for the life of the
// transaction.
//
// Changing data while traversing with a cursor may cause it to be invalidated
// and return unexpected keys and/or values. You must reposition your cursor
// after mutating data.
type Cursor struct {
    bucket *Bucket
    stack  []elemRef
}
```

  - `stack []elemRef` to record btree path to peticular node
  - `bucket` is similar to file directory

## IO Path

From Howard Chu's [slides](https://www.slideshare.net/InfoQ/ldap-at-lightning-speed):

<div style = "text-align: center;">
  <img src = "{{site.baseurl}}/img/btree-0.png" alt = "" style = "display: inline-block; width:45%">
  <img src = "{{site.baseurl}}/img/btree-1.png" alt = "" style = "display: inline-block; width:45%">
  <img src = "{{site.baseurl}}/img/btree-2.png" alt = "" style = "display: inline-block; width:45%">
  <img src = "{{site.baseurl}}/img/btree-3.png" alt = "" style = "display: inline-block; width:45%">
</div>

- read/write
  - read with mmap, buf-->unsafe pointer-->go structure
  - write:
      - write data pages, writeAt
      - write meta page, writeAt
      - fdatasync
- space management
  - allocate pages (tx --> db)
      1. from freelist --> array of free pages (lmdb is using another b+tree)
      1. from db end: [ meta.pgid, count ]
  - free pages
      - freelist's pending list
      - read pages still being used by read transactions
        - so avoid long-lived read transactions
  - freelist pages also needs to be managed
  - no gc or compaction
- dbfile remap
  - grow file size and remap
  - during page allocating
- crash/recovery
  - due to COW, no need to do log undo/redo 
  - only needs to fine the right meta page
- check
  - space free/allocated
  - node path links

## Transactions
- two ping-pong b+trees, similar to `software update`
- only one write transaction makes it easy to manage
- copying data from page to node
  - not like jbd2, which is tricky
  - jbd2 is sharing buffer-head and page cache
  - jbd2 use jbd-header or page flag to indicate sharing 

## Limitations
- concurrent writes
  - batch writes alleviate a little bit
- nvm optimization
  - using dax?
  - no need to do full page copy
  - utilize compare-and-swap instructions

## Further Readings
- <https://www.slideshare.net/InfoQ/ldap-at-lightning-speed>
  - better than BDB in all aspects
  - solving caching problems
  - lmdb support `reserve mode`, similar to fs allocation
  - `fixed mapping`
- mmap makes cache management easier
  - without it, it should still be fine, like in kernel
  - but need to implement readPage() and LRU by db itself
