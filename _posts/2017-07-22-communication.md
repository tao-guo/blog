---
layout: post
title: Communication Notes
categories: math
published: false
author: Tao
date: 2017-07-22
---

## Communication

- In computer itself, it is through computer bus. One of the simpliest ways is through \\(I^2C\\).
- In JESD245(jedec nvdimm) spec, read single register and block read
  - Start-Slave Address-Rd/Wr-Ack-Data Byte-Ack-P(stop)
  - The sequences are protocols between hardware and motherboard
  - 计算机的外设接口和通信定义的一样的道理,不过对于前段开发而言，基本都定义成文本格式
  - offset只有一个字节，最大偏移量只能表示成256，所以如果要访问更远的地址，需要采用多页面
    - 类似于存储系统中，多卷地址的表示
  - 批量读写时候，需要有一个seq id(block ID, region ID)
- SPD(串行存在检测)
  - 自动配置当前存在的硬件。SPD是一项内存硬件特性，可使计算机了解存在的内存以及访问内存要使用的时序。
    - JEDEC标准要求在内存模块的一个EEPROM上的低128字节中存有特定参数
    - SPD EEPROM采用SMBus访问，这是I²C协议的一个变种。这将模块上的通信引脚数量减少到两个：时钟信号和数据信号。
    - tools: dmidecode, decode-dimms, i2c-tools
  - Jedec规范中主要是表示EEPROM的格式
- Catastrophic Save
  - 疑问: Spec中提出了要求所有buffer必须回刷，但是如果操作系统正好崩溃了如果处理？比如突然掉电，那么存在于cpu缓存中的数据就丢失了吗?
    - Examples of these scenarios include fatal platform errors such as NMI or memory controller errors.
- SAVE Pin
  - module detects the SAVE pin is low for 1usec.
- Restore

  > The Restore operation is initiated through the START_RESTORE bit in the NVDIMM_FUNC_CMD0
  > register in page 0. At the completion of the Restore operation, the module shall put the SDRAM into self-
  > refresh mode and update the RESTORE_STATUS0 register in page 0.

- Erase

  > Modules shall support the Erase operation. During the Erase operation, the last saved SDRAM contents in
  > non-volatile memory is erase and the NVM_Data_Valid bit in CSAVE_INFO register in page 0 is set to
  > 0.

- 疑问: 如果设备本身出现异常，是否可以主动报告给host？还是需要host一直进行polling?
  - Set Event Notification: module set the status?
  - Could interrupt CPU?
- Atomic Arm and Erase
  - 可以保证数据要么成功要么失败
- Shared Energy Source
  - 共享电源
