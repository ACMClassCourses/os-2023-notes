## OSNotes-W12D1

#### Overview

NFS 1985 @Sun

RPC

Ethernet/Internet

network serveice/protocol 

network socket

#### Lecture Notes

**Network File System (NFS)**

Network File System (NFS) is a distributed file system protocol originally developed by Sun Microsystems (Sun) in 1984, allowing a user on a client computer to access files over a computer network much like local storage is accessed. 

In NFS, operations on the mounted virtual filesystem are transfered into correspondent RPC, and the real handler of such operations are the remote ones. 

**Remote Procedure Call (RPC)**

In distributed computing, a remote procedure call (RPC) is when a computer program causes a procedure (subroutine) to execute in a different address space (commonly on another computer on a shared network), which is written as if it were a normal (local) procedure call, without the programmer explicitly writing the details for the remote interaction.

<img src="https://s3.bmp.ovh/imgs/2023/06/16/dc07c3a3c5b29e17.png" title="" alt="" width="292">

**Review of Previous Lectures**

<img src="https://s3.bmp.ovh/imgs/2023/06/16/d2edf63471f43860.png" title="" alt="" width="319">

<img src="https://s3.bmp.ovh/imgs/2023/06/16/ed25b8de0bc3bdb8.png" title="" alt="" width="420">

**Computational Graph**

A computational graph is defined as a directed graph where the nodes correspond to mathematical operations. Computational graphs are a way of expressing and evaluating a mathematical expression.

**Ethernet & Internet**

<img src="https://s3.bmp.ovh/imgs/2023/06/16/88a02e23591caea9.png" title="" alt="" width="397">

<img src="https://s3.bmp.ovh/imgs/2023/06/16/a40ef5bb413613cf.png" title="" alt="" width="363">

LAN vs. WAN: whether pass router

DNS: Domain Name System. Lookup recursively

**Network Service & Network Protocol**

protocol stack / network stack: an implementation of a computer networking protocol suite or protocol family. 

![](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/220px-OSI_Model_v1.svg.png)

**Network Socket**

A network socket is a software structure within a network node of a computer network that serves as an endpoint for sending and receiving data across the network. The structure and properties of a socket are defined by an application programming interface (API) for the networking architecture. Sockets are created only during the lifetime of a process of an application running in the node.
