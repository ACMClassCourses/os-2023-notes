# Review OS

## History

- 1950s: batch processing
- 1960s: multiprogramming
- 1970s: time-sharing
- 1980s: personal computing
- 1990s: distributed computing

## Process

1. User/kernel process/thread
2. Interfaces: fork, exec, wait, exit
3. Scheduling
4. States: running, ready, blocked, zombie

## Memory

1. Physical memory
   Interfaces: kmalloc, alloc_pages, vmalloc
2. Virtual memory
  - Page table
  - Interfaces: mmap, munmap, mprotect, mremap, msync
  - malloc: dynamic memory allocation

## File system

1. File: sequence of bytes
   Interfaces: open, read, write, close
2. VFS
