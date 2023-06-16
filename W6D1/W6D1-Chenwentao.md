# File system

支持的操作：insert/delete/search/mkdir/rename/link

两类文件系统：EXT2(second_extend)，FAT（File allocation table）

## EXT2

search by index. 主要应用于 linux 系统

重要概念：

- MBR(master boot record)，0号扇区，记录每个扇区的始末地址
- superblock：记录了所有的关键参数，比如块的数量。常常需要多次备份，避免其被破坏后整个文件系统失效
- inode（index node）：每个文件都需要，记录了文件属性和每个文件块的地址。可能涉及到多级指针

软链接和硬链接：

- 软链接（符号链接）：创建一个 link 文件，访问时先读取该文件，得到真实路径，再访问原文件
- 硬链接：直接修改新文件的inode，让它也指向老文件

删除：在 **日志文件系统** 中有运用

- 先删除目录项
- 再回收 inode
- 最后回收 block

## FAT

search by link. 主要应用于早期的MS-DOS，如今的windows

思想：内存中的一个表记录了所有文件使用的块，访问一个文件时，只需要从该文件的起始块开始，每次向后查找即可

所以目录项中只需要维护每个文件的起始块

缺点：FAT本身占用了大量空间，难以处理大型磁盘

## virtual file system（VFS）

详细内容见课本165页