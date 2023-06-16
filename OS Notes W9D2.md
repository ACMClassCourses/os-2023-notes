## OS Notes W9D2

###### 陈永杉

#### How to drive an I/O device

### Input/Output

Challenges for OS to handle IO:

(1) Exists DMA Interruptions for some reasons

(2) Variety of devices

### IO devices

##### Block devices

-Store information in fixed-size blocks

-Transfers are in units of entire blocks 

##### Character devices

-Delivers or accepts stream of characters, without regard to block structure

-Not addressable, does not have any seek operation

We usually regard devices with large data blocks devices, other character devices.

### USB

similar with Near Field Communication

Field Buss: CAN / Lonworks

### Direct Memory Access

CPU using DMA to get appoint data from disk, interrupt when done.

on-fly: data going to memory directly, doesn't go to DMA storage.

zero-copy: data stay in system don 't move, any consumer come to get data here.

### Interrupts controller

control all interrupts sent to CPU

### Goals of the I/O software

Issues:

-Devices independence

-Uniform naming (avoid same name)

-Error handling

-Synchronous versus asynchronous

-Buffering

