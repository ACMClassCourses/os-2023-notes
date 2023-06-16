# EXT2

## Block

The Ext2 file system divides up disk space into logical blocks of contiguous space. The size of blocks need not be the same size as the sector size of the disk the file system resides on. The size of blocks can be determined by reading the field starting at byte 24 in the Superblock.

## Block Group

Blocks, along with inodes, are divided up into "block groups." These are nothing more than contiguous groups of blocks.
Each block group reserves a few of its blocks for special purposes such as:

- A bitmap of free/allocated blocks within the group
- A bitmap of allocated inodes within the group
- A table of inode structures that belong to the group
- Depending upon the revision of Ext2 used, some or all block groups may also contain a backup copy of the Superblock and the Block Group Descriptor Table.

## Inode

An inode is a structure on the disk that represents a file, directory, symbolic link, etc. Inodes do not contain the data of the file / directory / etc. that they represent. Instead, they link to the blocks that actually contain the data. This lets the inodes themselves have a well-defined size which lets them be placed in easily indexed arrays. Each block group has an array of inodes it is responsible for, and conversely every inode within a file system belongs to one of such tables (and one of such block groups).