# File System

Lin Tianchuan

Examples

- EXT2 (in Linux)
  by Rémy Card, 1994
  (FFS at BSD by McKusick)
- FAT
  by Tim Paterson, 1980

Filesystem = {set of files}

Q: Where is file A?
   Where is file A's block (data) ?

The following notes use the ext2 filesystem as an example.

## Disk layout

![](http://www.science.smith.edu/~nhowe/262/oldlabs/img/ext2.png)

Data Block Bitmap & Inode Bitmap: A bit value of 0 indicates that the block/inode is free, while a value of 1 indicates that the block/inode is being used.

![](http://www.science.smith.edu/~nhowe/262/oldlabs/img/ext2_bitmap.png)

## Inode

![](https://www.science.unitn.it/~fiorella/guidelinux/tlk/img84.gif)

struct ext2.inode (128 B)

- 12 direct blocks: pointers to the physical data blocks
- indirect blocks: points at a block of pointers to data blocks
- double indirect: points at a block of pointers to blocks of pointers to data blocks
- triple indirect: ...

K = blk_size / index_size

Max block num of a inode: 12 + K + K^2 + K^3

## Directory inode

![](http://www.science.smith.edu/~nhowe/262/oldlabs/img/dir_entry.png)

## Locating a file

![](http://www.science.smith.edu/~nhowe/262/oldlabs/img/ext2_locate.png)

## Hard link / Symbolic link

- Hard link: multiple entries in (same or different) directory inode point to the same inode.
  - Every non-root directory inode contains a hard link `.` to itself and a hard link `..` to its parent directory inode.
- Symbolic link: different inodes. The "content" of the symlink is the name it points to.
