#### 内存管理算法（buddy，slab）

- 内碎片：已经分配的内存中没有被使用的部分
- 外碎片：尚未被分配的内存，但是太小了，无法分配给需要的进程

操作系统分配物理内存的两个粒度，用户态的malloc实现

- 物理页粒度填写页表
- Bytes粒度分配内存，用于内核的动态内存申请
- 用户态的malloc是在虚拟地址上做分配，在堆区（小于`brk`）的地方划分内存池，将可用的区域划分为若干个chunk
- rCore 中的buddy伙伴算法：堆大小固定，用于在堆内划分

Buddy 算法

- 维护空闲链表数组
- 对于每一种块，维护一个bitmap，表示这个大小的某个块
  - 1 : 被分裂的，并且还有一个空闲
  - 0 : 两个都空闲或者两个都被使用了
- 用地址的xor，不用储存meta信息（其实就是地址xor长度）

#### 软连接和硬连接 inode 的区别

- 硬连接：在目录项里面建立的文件名字到inode的链接，如果所有的硬连接全部失效了，则ref count = 0， 这个文件的inode有可能会被删除。
- 硬连接：建立符号到文件路径的链接，实际上走的是，符号->文件路径->inode
- 软硬链接删文件的过程

#### ext 文件系统

基本要素

- Super Block : 存储文件系统的基本信息和其他块的位置
- Bitmap : inode的bitmap和block的bitmap
- Inode : Index Node，固定个数
- Block : 可以被分配的block

多级Inode

- 像多级页表一样的结构，但是每个Inode同样可以有直接的Block指针，也可以有二层的Block指针，三层的Block指针

文件系统的目录

- 一个目录：包括了很多个目录项。所以一个目录就是很多个目录项（`file name -> inode`）的集合

```
$ ls -l

drwxr-xr-x  3 hnyls2002 hnyls2002  4096 May 27 16:54 .
drwxr-xr-x 40 hnyls2002 hnyls2002  4096 May 28 19:40 ..
-rw-r--r--  1 hnyls2002 hnyls2002     0 May 27 13:37 123
-rw-r--r--  1 hnyls2002 hnyls2002   586 May 27 16:54 a.c
drwxr-xr-x  3 hnyls2002 hnyls2002  4096 May 23 23:38 .git
```

- 一个目录需要存储很多个目录项，**所以也是一个具有存储功能的文件，所以也有一个inode**

- 一个目录保存在上一层目录的文件结构中，直到根目录，**根目录是空，用`/`来指代根目录，第一个inode默认为根目录中的数据**


#### 文件系统崩溃一致性

- 合理性检查，一些数量需要在合理的范围内
- 资源分配一致性检查：不能有资源被标记分配了，但是却不能被索引到
- 内在不变量检查：比如硬链接数量

Super Block 

- makefs 的过程写入了多个super block
- 非常重要，所以保存了多个备份
- 根据超级块中的元数据信息，再结合了后续的结果之后，可以做合理性检查和资源分配一致性检查

fsck (file system check) 工具

- 一致性检查和修复工具
- 具有局限性
- 很耗时间

#### 文件系统的Journal

- 日志在文件写入之前：预写入时日志
- 日志也是文件，但是日志没有日志：一条崩溃的日志会直接被舍弃
- 一条日志写入完成之后会需要commit，表示这条日志是完整的
- 日志commit之后开始写入文件
- 写入文件完毕之后，将日志标记为无效
- 日志占用了太多的内存空间：销毁

#### FAT 文件系统 ( File Allocation Table )

- FAT的存储结构是分为了若干个cluster。
- FAT实际上就是由cluster编号组成的数组，一个文件可以看做是若干个cluster的链表。
- 可以通过Table中的信息来判断某个cluster的使用情况，如果是0x0，那么就是空闲的，如果0xffff（全部都是f），那么就是某个文件的结尾。

缺点

- 连续的文件结构实际的物理存储地址可能在磁盘上的不同位置，导致过于分散，写入和读取文件的效率过低
- 只能通过遍历所有的cluster的方式来寻找某个文件中的某个位置，效率过低

#### 文件系统的二级缓存：buffer cache & page cache

Reference from [Quora](https://www.quora.com/What-is-the-major-difference-between-the-buffer-cache-and-the-page-cache-Why-were-they-separate-entities-in-older-kernels-Why-were-they-merged-later-on)

- Buffer Cache : 按照文件系统的逻辑来组合，比如按照block来缓存 (Behave exactly like a disk, but in memory)
- Page Cache : 文件系统的组织非常复杂（inode，superblock, etc），上层的抽象是直接用地址+offset来访问，这个访问模式完全可以直接缓存在内存中，于是page cache就按照内存的管理方式来组织了（页模式）。

一般的写cache和读cache

- Reed Cache
- Write Buffer : 在后台慢慢来，可以合并写操作，可能会有一致性？
