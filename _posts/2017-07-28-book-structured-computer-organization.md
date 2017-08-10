---
layout: post
title: Reading Notes -- 《Structured Computer Organization》
categories: computer
published: true
author: Tao
---

## 0. PREFACE

- core idea: computer = a hierarchy of levels
  - *digital logic level* -- Memory
  - microarchitecture level -- CPU-internal
  - *instruction set architecture level* -- CPU-external
  - operating-system machine level -- Virtualized (Mem,CPU, I/O)
  - assembly language level -- App
- what's new in sixth:
  - up to date
    - Intel Core i7: X86-based CPU, laptops, desktops and server machines 2008-code-name Nehalem
    - Texas Instrument OMAP4430: ARM-based CPU, smartphones and tablets
    - Atmel ATmegal68: AVR-based microcontroller, clock radios to microwave ovens
      - number much bigger than i3, i5, i7
      - in Arduino single-board embedded computer (pizza dinner cost)
  - assembly language programming
    - 8088, on website vs 6502
    - could try on laptop, with tools
  - longer (443-769 pages)
- chapter-by-chapter rundown, and also changes from fifth
  - ch1: history, with more to cover: FPGAs, smartphones, tablets ...
  - ch2: with GPUs, flash-based storage devices, game controllers, touch screens
  - ch3: FPGAs
  - ch4: with new CPUs
  - ch5: ARM and AVR ISAs
  - ch6: windows7
  - ch7: no change
  - ch8: i7 multiprocessor, NVIDIA Fermi GPU, BlueGene, Red Storm
  - ch9: gone, suggested readings moved to website
    - <http://www.pearsonhighered.com/tanenbaum>
      - assembler/tracer software
      - ch4 graphical simulator
      - suggested readings

## 1. INTRODUCTION

- program, machine language, structured computer organization

### 1.1 STRUCTURED COMPUTER ORGANIZATION 2

#### 1.1.1 Languages, Levels, and Virtual Machines 2
- translation vs. interpretation
- levels, cost

#### 1.1.2 Contemporary Multilevel Machines 5
- L0: gates from transistors
  - below: solid-state physics, CMOS
  - register

  > Hardware and software are logically equivalent.
- L5: high level languages like python, java, C++ ...
- Computer architecture vs. computer organization
  - one layer vs. more parts
  - mostly the same

#### 1.1.3 Evolution of Multilevel Machines 8
- Two levels at first: ISA and digital logic level
- Hardware: rather than **abstract ideas**, algorithms, or instructions.
- inventions
  - microprogramming: to make hardware design simple
    - two levels --> three levels
  - OS: reduce manual processes, keep it running all the time
    - FMS(Fortune Monitor): compile and read data
        - only run two programs at first
        - then I/O calls, system calls
        - batch systems --> timesharing, terminal
        - this book only focus on differences from ISA
    - As library: system calls
    - Timesharing
    - Like a society, it finally formed a goverment
  - The Migration of Functionality to Microcode
      - more microprograms: INC, MUL, STR ...
      - more features: relocation, interrupt, switching
  - the elimination of microprograms
      - mordern processors still do translation to internal microcode

        > Today’s software may be
        > tomorrow’s hardware, and vice versa. Furthermore, the boundaries between the
        > various levels are also fluid. From the programmer’s point of view, how an instruc-
        > tion is actually implemented is unimportant (except perhaps for its speed). A per-
        > son programming at the ISA level can use its multiply instruction as though it were
        > a hardware instruction without having to worry about it, or even be aware of
        > whether it really is a hardware instruction. One person’s hardware is another per-
        > son’s software.

#### 1.2 MILESTONES IN COMPUTER ARCHITECTURE 13
- brief sketch of some of the key historical developments
- Potrit book: <https://archive.org/details/wizardstheirwonder00morg>

#### 1.2.1 The Zeroth Generation–Mechanical Computers (1642—1945) 13
- Pascal (1623–1662) at age 19: with gears and crank, to do add/substraction
- Leibniz (1646–1716): multiply and divide, [four-function pocket calculator](http://www.computerhistory.org/revolution/calculators/1/49)
- Babbage (1792–1871)
  - difference engine: one algorithm for naval navigation
  - analytical engine:
    - the store (memory)
    - the mill (computation unit)
    - the input section (punched-card reader)
    - the output section (punched and printed output)
    - Ada as the first programmer
- Konrad Zuse 1930
  - engineering student
  - automatic calculating machines using electromagnetic relays
- Shannon 1938 master thesis: A Symbolic Analysis of Relay and Switching Circuits
- John Vincent Atanasoff at Iowa State College and Stibbitz at Bell Labs 1940
  - binary arithmetic, capacitors for memory (refresh like DRAM)

#### 1.2.2 The First Generation–Vacuum Tubes (1945—1955) 16
- ENIGMA vs. COLOSSUS
- ENIAC, not finished (1943-1946), summer school, decimal 
- EDVAC, unisys corp.
- von Neumann: program in the computer’s memory
  - EDSAC, the first stored-program computer, with Goldstine
  - The von Neumann machine
  - accumulator
- MIT IAS
  - real-time control
  - magnetic core memory
- IBM 701 (1953), 704

#### 1.2.3 The Second Generation–Transistors (1955—1965) 19
- Bell Labs in 1948 by John Bardeen, Walter Brattain, and William Shockley
- TX-0: first transistorized computer was built at M.I.T.’s Lincoln Laboratory
- DEC
  - PDP-1
  - [PDP-8](https://en.wikipedia.org/wiki/PDP-8): **bus**, **DMA**, minicomputer
- CDC 6600, 1964 - with small computers
  - Seymour Cray: buying car algorithm
- Burroughs B5000: in algol 60

#### 1.2.4 The Third Generation–Integrated Circuits (1965—1980) 21
- IBM System/360
  - compatible
  - multiprogramming
  - emulate(simulate) old systems: Wilkes's microprogramming
  - huge address space 2^24, but still requires upgrade later
- DEC's PDP-11

#### 1.2.5 The Fourth Generation–Very Large Scale Integration (1980—?) 23
- VLSI (Very Large Scale Integration), PC era
- used for word processing, spreadsheets, and numerous highly interactive applications (such as games)
- Intel 8080, some cables, a power supply, and perhaps an 8-inch floppy disk
  - CP/M operating system
- Apple
  - later with GUI
- IBM: quite uncharacteristic
  - bag of money to build PC
  - published the complete plans, including all the circuit diagrams only caused *clones*
  - helped Intel and Microsoft
- RISC in mid-1980
  - superscalar CPUs
- FPGA in mid-1980
  - Ross Freeman at Xilinx
  - hardware malleable as software
- DEC 1992
  - 64-bit Alpha, a true 64-bit RISC machine
- slow down
  - architects were running out of tricks to make programs faster
  - the processors were getting too expensive to cool
  - turning toward parallel architectures
  - in 2001 IBM introduced the POWER4 dual-core architecture
  - require programmers to explicitly parallelize programs, which is a difficult and error-prone task.

#### 1.2.6 The Fifth Generation–Low-Power and Invisible Computers 26
- Japanese: based on artificial intelligence and represent a quantum leap
  - failed and was quietly abandoned
  - a visionary idea but so far ahead of its time
- PDAs, smartphones
- "invisible" computers
  - *codesign* software and hardware
  - paradigm shift
  - ubiquitous computing, but the term *pervasive computing*
    - not too much information in this book
    - <https://zhuanlan.zhihu.com/p/22965003>

#### 1.3 THE COMPUTER ZOO 28

#### 1.3.1 Technological and Economic Forces 28
- Moore’s law and virtuous circle
- Nathan’s first law of software
- telecommunication and networking

#### 1.3.2 The Computer Spectrum 30
#### 1.3.3 Disposable Computers 31
- RFID chip
  - powered by the incoming radio signal long enough to transmit their number back to the antenna
  - applications
    - removing bar codes from products
    - identify the specific item
    - vehicle tracking    
    - Airline baggage systems and others
    - can contain permanent storage
    - not only passive

#### 1.3.4 Microcontrollers 33
- cars with 50 microcontrollers easily
- complete computer
- in real time
- physical constraints
- cheap: Arduino system, open-source
  - programming language called Wiring
  - example: a moisture detector that sends email when a plant needs to be watered

#### 1.3.5 Mobile and Game Computers 35
#### 1.3.6 Personal Computers 36
#### 1.3.7 Servers 36
- clusters
  - consist of standard server-class systems connected by gigabit/sec networks
  - running special software that allow all the machines to work together on a single problem
  - often in business, science or engineering.
- cloud computing, which is mainframe computing V2.0
- new revolution?

#### 1.3.8 Mainframes 38
- e-commerce transactions per second, particularly in businesses with huge databases.
- supercomputers

  > in recent years, data centers constructed from commodity components
  > have come to offer as much computing power at much lower prices, and the true
  > supercomputers are now a dying breed.

#### 1.4 EXAMPLE COMPUTER FAMILIES 39
#### 1.4.1 Introduction to the x86 Architecture 39
#### 1.4.2 Introduction to the ARM Architecture 45
- Nvidia Tegra 2

#### 1.4.3 Introduction to the AVR Architecture 47
- an 8-bit CPU, basic digital I/O support, and analog input support
- with flash, EEPROM, and RAM
  - Flash memory is programmable using an external interface and high voltages
    - store program code and data
  - EEPROM: user configuration information

#### 1.5 METRIC UNITS 49
#### 1.6 OUTLINE OF THIS BOOK 50

## 2. COMPUTER SYSTEMS ORGANIZATION

### 2.1 PROCESSORS 55
- Program Counter (PC)
- Instruction Register (IR)

### 2.1.1 CPU Organization 56
- data path
- ALU (Arithmetic Logic Unit)
- instructions
  - register-memory or register-register
  - fast: data path cycle

### 2.1.2 Instruction Execution 58
- fetch-decode-execute cycle
- interpreter was popular
  - DEC VAX: 200 ways, fatal
  - fast read-only memories, called control stores

### 2.1.3 RISC versus CISC 62
- RISC
  - David Patterson, 1980
  - John Hennessy, MIPS, 1984
- battle not won?
  - backward compatibility
  - hybrid approach

### 2.1.4 Design Principles for Modern Computers 63
- All Instructions Are Directly Executed by Hardware
- Maximize the Rate at Which Instructions Are Issued
- Instructions Should Be Easy to Decode
- Only Loads and Stores Should Reference Memory
- Provide Plenty of Registers

### 2.1.5 Instruction-Level Parallelism 65
- instruction-level parallelism and processor-level parallelism
- pipelining
  - fetching of instructions from memory is a major bottleneck
  - prefetch buffer
  - five stages
  - trade-off between latency and processor bandwidth
- Superscalar Architectures
  - either the compiler must guarantee this situation to hold
  - or conflicts must be detected and eliminated during execution using extra hardware
  - Intel
    - 486 learned from RISC: one pipeline
    - Pentium: two pipeline
  - single pipeline but give it multiple functional units
    - superscalar: multiple instructions in a single clock
    - speedup S4, multiple ALUs

### 2.1.6 Processor-Level Parallelism 69
- Data parallel computers
  - loops and arrays
  - SIMD processors
    - ILLIAC IV, UIUC 1972
    - GPUs: 512 operations per cycle
  - vector processors: extension to single processor
    - Cray 1974
    - vector register
    - Intel SSE
  - Multiprocessors
    - more than one CPU sharing a common memory
    - coordinate memory access
    - with local cache
    - easier to program
  - Multicomputers
    - private memory, loosely coupled
    - communicate by sending each other messages
    - IBM’s Blue Gene
    - easier to build
  - hybrid systems: illusion of shared memory

### 2.2 PRIMARY MEMORY 73
### 2.2.1 Bits 74
### 2.2.2 Memory Addresses 74
- bit, byte, word
- most instructions operate on entire word

### 2.2.3 Byte Ordering 76
- little endian, small edian

### 2.2.4 Error-Correcting Codes 78
- ECC, codeword
- **Hamming distance**
  - to correct d single-bit errors, you need a distance 2d + 1 code
  - 2^n for correct bits

### 2.2.5 Cache Memory 82
- compiler is forced to insert NOP
- having a small amount of fast memory or a large amount of slow memory
- locality principle
- hit ratio/ miss ratio
- caches are divided up into fixed-size blocks: cache lines
- performance
  1. cache size
  2. cache line size
  3. how to organize?
  4. unified cache or split cache
  5. number of caches

### 2.2.6 Memory Packaging and Types 85
- SIMM, DIMM, SO-DIMM (laptop)

### 2.3 SECONDARYMEMORY 86
### 2.3.1 Memory Hierarchies 86
### 2.3.2 Magnetic Disks 87
- ECC or RS code, 15%
- preambles
- disk controller, a chip that controls the drive
- Some controllers also handle
  - buffering of multiple sectors
  - caching sectors read for potential future use
  - remapping bad sectors

### 2.3.3 IDE Disks 91
- LBA, ATA, SATA

### 2.3.4 SCSI Disks 92
- SCSI (Small Computer System Interface)
- SCSI controllers and peripherals can operate either as initiators or as targets.
- SAS: Serial SCSI
  - expander
  - layers

### 2.3.5 RAID 94
- Thinking Machines CM-2: 38-bit Hamming word

### 2.3.6 Solid-State Disks 97
- transistors slowly wear out as they are used
- Fujio Masuoka 1980, flash memory
- wear leveling
- multilevel flash cells
  - typical: four charge levels, yielding two bits per flash cell

### 2.3.7 CD-ROMs 99
- distributing software
- making backups of hard disks

### 2.3.8 CD-Recordables 103
### 2.3.9 CD-Rewritables 105
- CD-R cannot be accidentally erased is a feature, not a bug

### 2.3.10 DVD 106
### 2.3.11 Blu-ray 108
### 2.4 INPUT/OUTPUT 108
### 2.4.1 Buses 108
- Each I/O device consists of two parts
  - controller
  - I/O device itself
- DMA
  - bypass CPU
  - interrupt handler
- bus arbiter
  - cycle stealing
- PCI bus
  - designed by Intel, opened
  - seperate from memory bus
- PCIe
  - not even a bus at all. It is point-to-point network using bit-serial lines and packet switching
  - Similar to SAS
  - avoid skew issue
  - wire pairs, called lanes
  - PCIe 3.0: 16GB/s
  - point to point: use PCIe switch

### 2.4.2 Terminals 113
- keyboard, screens

### 2.4.3 Mice 118
### 2.4.4 Game Controllers 120
- Kinet: based on a depth camera combined with a video camera

### 2.4.5 Printers 122
### 2.4.6 Telecommunications Equipment 127
### 2.4.7 Digital Cameras 135
### 2.4.8 Character Codes 137
### 2.5 SUMMARY 142

## 3. THE DIGITAL LOGIC LEVEL

- 3.1 GATES AND BOOLEAN ALGEBRA 147
  - 3.1.1 Gates 148
  - 3.1.2 Boolean Algebra 150
  - 3.1.3 Implementation of Boolean Functions 152
  - 3.1.4 Circuit Equivalence 153
- 3.2 BASIC DIGITAL LOGIC CIRCUITS 158
  - 3.2.1 Integrated Circuits 158
  - 3.2.2 Combinational Circuits 159
  - 3.2.3 Arithmetic Circuits 163
  - 3.2.4 Clocks 168
- 3.3 MEMORY 169
  - 3.3.1 Latches 169
  - 3.3.2 Flip-Flops 172
  - 3.3.3 Registers 174
  - 3.3.4 Memory Organization 174
  - 3.3.5 Memory Chips 178
  - 3.3.6 RAMs and ROMs 180
- 3.4 CPU CHIPS AND BUSES 185
  - 3.4.1 CPU Chips 185
  - 3.4.2 Computer Buses 187
  - 3.4.3 Bus Width 190
  - 3.4.4 Bus Clocking 191
  - 3.4.5 Bus Arbitration 196
  - 3.4.6 Bus Operations 198
- 3.5 EXAMPLE CPU CHIPS 201
  - 3.5.1 The Intel Core i7 201
  - 3.5.2 The Texas Instruments OMAP4430 System-on-a-Chip 208
  - 3.5.3 The Atmel ATmega168 Microcontroller 212
- 3.6 EXAMPLE BUSES 214
  - 3.6.1 The PCI Bus 215
  - 3.6.2 PCI Express 223
  - 3.6.3 The Universal Serial Bus 228
- 3.7 INTERFACING 232
  - 3.7.1 I/O Interfaces 232
  - 3.7.2 Address Decoding 233
- 3.8 SUMMARY 235

## 4. THE MICROARCHITECTURE LEVEL
- 4.1 AN EXAMPLE MICROARCHITECTURE 243
  - 4.1.1 The Data Path 244
  - 4.1.2 Microinstructions 251
  - 4.1.3 Microinstruction Control: The Mic-1 253
- 4.2 AN EXAMPLE ISA: IJVM 258
  - 4.2.1 Stacks 258
  - 4.2.2 The IJVM Memory Model 260
  - 4.2.3 The IJVM Instruction Set 262
  - 4.2.4 Compiling Java to IJVM 266
- 4.3 AN EXAMPLE IMPLEMENTATION 267
  - 4.3.1 Microinstructions and Notation 267
  - 4.3.2 Implementation of IJVM Using the Mic-1 272
- 4.4 DESIGN OF THE MICROARCHITECTURE LEVEL 283
  - 4.4.1 Speed versus Cost 283
  - 4.4.2 Reducing the Execution Path Length 286
  - 4.4.3 A Design with Prefetching: The Mic-2 293
  - 4.4.4 A Pipelined Design: The Mic-3 293
  - 4.4.5 A Seven-Stage Pipeline: The Mic-4 301
- 4.5 IMPROVING PERFORMANCE 305
  - 4.5.1 Cache Memory 306
  - 4.5.2 Branch Prediction 312
  - 4.5.3 Out-of-Order Execution and Register Renaming 317
  - 4.5.4 Speculative Execution 322
- 4.6 EXAMPLES OF THE MICROARCHITECTURE LEVEL 324
  - 4.6.1 The Microarchitecture of the Core i7 CPU 325
  - 4.6.2 The Microarchitecture of the OMAP4430 CPU 331
  - 4.6.3 The Microarchitecture of the ATmega168 Microcontroller 336
- 4.7 COMPARISON OF THE I7, OMAP4430, AND ATMEGA168 338
- 4.8 SUMMARY 339

## 5. THE INSTRUCTION SET
- 5.1 OVERVIEW OF THE ISA LEVEL
  - 5.1.1 Properties of the ISA Level
  - 5.1.2 Memory Models
  - 5.1.3 Registers
  - 5.1.4 Instructions
  - 5.1.5 Overview of the Core i7 ISA Level
  - 5.1.6 Overview of the OMAP4430 ARM ISA Level
  - 5.1.7 Overview of the ATmega168 AVR ISA Level
- 5.2 DATA TYPES
  - 5.2.1 Numeric Data Types
  - 5.2.2 Nonnumeric Data Types
  - 5.2.3 Data Types on the Core i7
  - 5.2.4 Data Types on the OMAP4430 ARM CPU
  - 5.2.5 Data Types on the ATmega168 AVR CPU
- 5.3 INSTRUCTION FORMATS
  - 5.3.1 Design Criteria for Instruction Formats
  - 5.3.2 Expanding Opcodes
  - 5.3.3 The Core i7 Instruction Formats
  - 5.3.4 The OMAP4430 ARM CPU Instruction Formats
  - 5.3.5 The ATmega168 AVR Instruction Formats
- 5.4 ADDRESSING
  - 5.4.1 Addressing Modes
  - 5.4.2 Immediate Addressing
  - 5.4.3 Direct Addressing
  - 5.4.4 Register Addressing
  - 5.4.5 Register Indirect Addressing
  - 5.4.6 Indexed Addressing
  - 5.4.7 Based-Indexed Addressing
  - 5.4.8 Stack Addressing
  - 5.4.9 Addressing Modes for Branch Instructions
  - 5.4.10 Orthogonality of Opcodes and Addressing Modes
  - 5.4.11 The Core i7 Addressing Modes
  - 5.4.12 The OMAP4440 ARM CPU Addressing Modes
  - 5.4.13 The ATmega168 AVR Addressing Modes
  - 5.4.14 Discussion of Addressing Modes
- 5.5 INSTRUCTION TYPES
  - 5.5.1 Data Movement Instructions
  - 5.5.2 Dyadic Operations
  - 5.5.3 Monadic Operations
  - 5.5.4 Comparisons and Conditional Branches
  - 5.5.5 Procedure Call Instructions
  - 5.5.6 Loop Control
  - 5.5.7 Input/Output
  - 5.5.8 The Core i7 Instructions
  - 5.5.9 The OMAP4430 ARM CPU Instructions
  - 5.5.10 The ATmega168 AVR Instructions
  - 5.5.11 Comparison of Instruction Sets
- 5.6 FLOWOF CONTROL
  - 5.6.1 Sequential Flow of Control and Branches
  - 5.6.2 Procedures
  - 5.6.3 **Coroutines**
  - 5.6.4 **Traps**
  - 5.6.5 **Interrupts**
- 5.7 A DETAILED EXAMPLE: THE TOWERS OF HANOI
  - 5.7.1 The Towers of Hanoi in Core i7 Assembly Language
  - 5.7.2 The Towers of Hanoi in OMAP4430 ARM Assembly Language
- 5.8 THE IA-64 ARCHITECTURE AND THE ITANIUM 2
  - 5.8.1 The Problem with the IA-32 ISA
  - 5.8.2 The IA-64 Model: Explicitly Parallel Instruction Computing
  - 5.8.3 Reducing Memory References
  - 5.8.4 Instruction Scheduling
  - 5.8.5 Reducing Conditional Branches: Predication
  - 5.8.6 Speculative Loads
- 5.9 SUMMARY
 
## 6. THE OPERATING SYSTEM
- 6.1 VIRTUAL MEMORY
  - 6.1.1 Paging
  - 6.1.2 Implementation of Paging
  - 6.1.3 Demand Paging and the Working Set Model
  - 6.1.4 Page Replacement Policy
  - 6.1.5 Page Size and Fragmentation
  - 6.1.6 Segmentation
  - 6.1.7 Implementation of Segmentation
  - 6.1.8 Virtual Memory on the Core i7
  - 6.1.9 Virtual Memory on the OMAP4430 ARM CPU
  - 6.1.10 Virtual Memory and Caching
- 6.2 VIRTUAL I/O INSTRUCTIONS
  - 6.2.1 Files
  - 6.2.2 Implementation of Virtual I/O Instructions
  - 6.2.3 Directory Management Instructions
- 6.3 VIRTUAL INSTRUCTIONS FOR PARALLEL PROCESSING
  - 6.3.1 Process Creation
  - 6.3.2 Race Conditions
  - 6.3.3 Process Synchronization Using Semaphores
- 6.4 EXAMPLE OPERATING SYSTEMS
  - 6.4.1 Introduction
  - 6.4.2 Examples of Virtual Memory
  - 6.4.3 Examples of Virtual I/O
  - 6.4.4 Examples of Process Management
- 6.5 SUMMARY

## 7. THE ASSEMBLY LANGUAGE LEVEL
- 7.1 INTRODUCTION TO ASSEMBLY LANGUAGE
  - 7.1.1 What Is an Assembly Language?
  - 7.1.2 Why Use Assembly Language?
  - 7.1.3 Format of an Assembly Language Statement
  - 7.1.4 Pseudoinstructions
- 7.2 MACROS
  - 7.2.1 Macro Definition, Call, and Expansion
  - 7.2.2 Macros with Parameters
  - 7.2.3 Advanced Features
  - 7.2.4 Implementation of a Macro Facility in an Assembler
- 7.3 THE ASSEMBLY PROCESS
  - 7.3.1 Two-Pass Assemblers
  - 7.3.2 Pass One
  - 7.3.3 Pass Two
  - 7.3.4 The Symbol Table
- 7.4 LINKING AND LOADING
  - 7.4.1 Tasks Performed by the Linker
  - 7.4.2 Structure of an Object Module
  - 7.4.3 Binding Time and Dynamic Relocation
  - 7.4.4 Dynamic Linking
- 7.5 SUMMARY

## 8. PARALLEL COMPUTER ARCHITECTURES
- 8.1 ON-CHIP PARALELLISM
  - 8.1.1 Instruction-Level Parallelism
  - 8.1.2 On-Chip Multithreading
  - 8.1.3 Single-Chip Multiprocessors
- 8.2 COPROCESSORS
  - 8.2.1 Network Processors
  - 8.2.2 Media Processors
  - 8.2.3 Cryptoprocessors
- 8.3 SHARED-MEMORYMULTIPROCESSORS
  - 8.3.1 Multiprocessors vs. Multicomputers
  - 8.3.2 Memory Semantics
  - 8.3.3 UMA Symmetric Multiprocessor Architectures
  - 8.3.4 NUMA Multiprocessors
  - 8.3.5 COMA Multiprocessors
- 8.4 MESSAGE-PASSING MULTICOMPUTERS
  - 8.4.1 Interconnection Networks
  - 8.4.2 MPPs–Massively Parallel Processors
  - 8.4.3 Cluster Computing
  - 8.4.4 Communication Software for Multicomputers
  - 8.4.5 Scheduling
  - 8.4.6 Application-Level Shared Memory
  - 8.4.7 Performance
- 8.5 GRID COMPUTING
- 8.6 SUMMARY

## 9. SUGGESTIONS
- 9.1 SUGGESTIONS FOR FURTHER READING
  - 9.1.1 Introduction and General Works
  - 9.1.2 Computer Systems Organization
  - 9.1.3 The Digital Logic Level
  - 9.1.4 The Microarchitecture Level
  - 9.1.5 The Instruction Set Architecture Level
  - 9.1.6 The Operating System Machine Level
  - 9.1.7 The Assembly Language Level
  - 9.1.8 Parallel Computer Architectures
  - 9.1.9 Binary and Floating-Point Numbers
  - 9.1.10 Assembly Language Programming
- 9.2 ALPHABETICAL BIBLIOGRAPHY

## Appendix

- A.1 FINITE-PRECISION NUMBERS
- A.2 RADIX NUMBER SYSTEMS
- A.3 CONVERSION FROM ONE RADIX TO ANOTHER
- A.4 NEGATIVE BINARY NUMBERS
- A.5 BINARY ARITHMETIC
- B.1 PRINCIPLES OF FLOATING POINT
- B.2 IEEE FLOATING-POINT STANDARD 754
- C.1 OVERVIEW
  - C.1.1 Assembly Language
  - C.1.2 A Small Assembly Language Program
- C.2 THE 8088 PROCESSOR
  - C.2.1 The Processor Cycle
  - C.2.2 The General Registers
  - C.2.3 Pointer Registers
- C.3 MEMORY AND ADDRESSING
  - C.3.1 Memory Organization and Segments
  - C.3.2 Addressing
- C.4 THE 8088 INSTRUCTION SET
  - C.4.1 Move, Copy and Arithmetic
  - C.4.2 Logical, Bit and Shift Operations
  - C.4.3 Loop and Repetitive String Operations
  - C.4.4 Jump and Call Instructions
  - C.4.5 Subroutine Calls
  - C.4.6 System Calls and System Subroutines
  - C.4.7 Final Remarks on the Instruction Set
- C.5 THE ASSEMBLER
  - C.5.1 Introduction
  - C.5.2 The ACK-Based Assembler, as88
  - C.5.3 Some Differences with Other 8088 Assemblers
- C.6 THE TRACER
  - C.6.1 Tracer Commands
- C.7 GETTING STARTED
- C.8 EXAMPLES
  - C.8.1 Hello World Example
  - C.8.2 General Registers Example
  - C.8.3 Call Command and Pointer Registers
  - C.8.4 Debugging an Array Print Program
  - C.8.5 String Manipulation and String Instructions
  - C.8.6 Dispatch Tables
  - C.8.7 Buffered and Random File Access

