## OS Notes W13D2

###### 陈永杉

## case study: UNIX, Lunix and Android
#### AIDL:

using binder_module in the kernel to connect different processes

Motorola, mobile system based on lunix.

On a mobile phone, the system need GUI, IM, Cell with a lunix kernel.

#### Android:

unsing byte code to commute, Just-in-Time

if init is the 0 processer of lunix, the direct parent of all android java progroms is zygote

on lunix, the whole android is one process

using binder IPC, to commuinte bitween different processes.

Since OS make sure that each process is independent, so all communition between processes are kernel-dependented.

using watch-dog to make sure that the programs run correctly (in case of the bite reverse). or the watch dog will reset the system.

heart beating: to check if the other one alive.

 using intent to sent requirement to service manager. If the local manager can't handle this requirement, itwould turn to the packet manager, or would sent this t the cloud, ask for service.