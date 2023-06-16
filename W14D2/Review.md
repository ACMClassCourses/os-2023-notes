## 线程 进程
8-core CPU: when pthread
real/yield time
turbo: change the CPU frequency, thus change the speed
## 优先级反转
优先级反转
优先级继承：如果在pthread转换的时候发现了锁，为了避免轮空，让$T_2$继承$T_1$的优先级
                       lock          unlock
$T_1$——————————         ———————————
$T_2$                               ———
                                  lock
transaction抽象
## 内存
vdso等内存段
内存应不应该能感觉到地址页的存在
buddy伙伴算法应该出现在哪里进行管理，地址异或，位图bit
MMU `MAKE_SATP`
KPTI: page table $\rightarrow$ kernel page table isolation
from user state to kernel state, we have to flush all the TLB

软链接和硬链接中inode的区别是什么
superblock backup stored on blocks: ?
mmap读写与普通文件系统的区别，`char *`读写不会把整个文件全部load进来
类FAT文件系统的缺点是什么，如何实现变长度读？引入page
## 虚拟化与安全
虚拟机内翻译一次虚拟地址多少次内存访问
watchdog
rcu: detect stalls
NMI
cli关中断
kernel thread (not process): share memory space
内核挂了：狗死了
VMX root mode/VMX non-root mode
Guest OS/Guest User/Guest Kernel
CR3 points to the PA of virtual machine
GVA $\rightarrow$ GPA $\rightarrow$ HPA
software realizing? 四级 20/16 times of read
hardware realizing? no virtualization, I/O interruption via kvm to host machine
## Fork分析
## 综合设计
### VMEXIT
GPU I/O interruption $\rightarrow$ via kvm in Host OS $\rightarrow$ VCPU/VGPU $\rightarrow$ come back to host to handle interrupt
The process of devisualization and coming back to host is consuming a lot of time
Non-Latency and in great number
Zheng Wenxin: Delay+Batch
I/O thread: collect all the interruptions in one queue and when it accumulates to some extent, just trigger one kvm processing, we hope to avoid strenuous exit from virtual machine.
In which condition will this be better?
### NUMA
when the number of cores are increased to an extent, then the cache collision will be very serious, so the throughput will decrease greatly.
A list of locks, and when one pthread gets the lock and change the variable, the next lock in the list will wait for it.
So at a time, there are only two pthreads fighting for that variable.
This will decrease the cache covariance and ensure justice.
avoid the core which is farther to the data failing all the time.
### 可信执行环境
TEE: protect from Host OS.
If the computing is performed only in CPU or GPU, we can isolate the computing in hardware. 
But if there are interaction between CPU and GPU
crypto + CPU can be in TEE.