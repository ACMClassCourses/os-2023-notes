## OS Notes W5D2

###### 陈永杉

#### setjump/longjump

```OS
main(){
...
e=setjump(jx);
switch(e){
...
}
bar();
...
}

bar(){
foo();
}

foo(){
if(somthing error) longjump(jx,value); // back to the setjump in the main func
}
```

similar to the "long jump"

In jump buffer $j_x$, it stores the position of the instruction setjump and the stack in the main function.

### File and Filesystem 

#### memory management

physical memory

virtual memory:

​	process: vm_ware_structure, mmap( vadd, --, --, file, offset, size)

​	phy: budInode dy algorithm

#### File: a seq of bytes, Filesystem: a set of files

Essential requirements for long-term information storage:

1, It must be possible to store a very large amount of information.

2, Information must survive termination of process using it.

3, Multiple proceses must be able to access information concurrently.

#### Link Method

$\textbf{Hard Link}$

Each file is given more than one "inode index". So there exist situations that more than more one inodes pointing to one file. So hard link can avoid deletion in accident. Only all hard links poiting to the file are deleted, when the file is deleted. Inode index is unique in one file system.

$\textbf{Symbolic Link}$

It's a special file which conatins opsition information of another file. If the other file is deleted, symbolic still exists, but invailed.

#### FIle type

using magic number to confirm file type.

need a relocation table, symbol table.

Lunix regards menu as a file.

Lunix mount: mount one directory to another directory point. One point can only mount one. Using this to organize different storage equipments.

s