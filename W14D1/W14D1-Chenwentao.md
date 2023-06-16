# Review OS

## 以UNIX为例子

历史：MULTICS `->` 现代操作系统 

抽象：CPU/MEM/IO `->` process/virtual memory/file

### process 

每个进程都是一个 **程序**，有独立的寄存器、程序计数器、堆栈指针

thread（线程）：有独立的栈空间

考虑：task_struct

### 系统调用 syscall

- fork/exec/exit/wait

进程的状态：

- running
- block
- ready
- zombie

## 内存管理

### 物理内存

管理的单位为页框：page frame

在linux中利用buddy算法进行管理

### 虚拟内存

- page_table
- mmap：把文件映射到进程的内存中，当成连续的内存进行处理
- malloc：调用系统的 brk（扩展堆空间）来分配虚拟内存

## 文件系统

