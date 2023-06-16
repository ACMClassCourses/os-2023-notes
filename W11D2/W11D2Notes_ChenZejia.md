## W11D2 notes

**written by Chen Zejia.**

## Multi-core/processer

* e.g. SMC/SMP/cluster/Grid/Cloud...
* UMA: provides equal access to memory for all processors and has lower latency.
* NUMA: provides higher scalability and better memory utilization.

### Multiprocessor Synchronization

* Multiple spinlock: locks form a list.
* Use of multiple locks to avoid cache thrashing

### Time/Space Sharing 

### Gang Scheduling

* Groups sof related threads are scheduled as a unit, a gang.
* All member of a gang run at once on different timeshared CPUs.
* All gang members start and end their time slices together.

### Blocking vs Nonblocking Calls

### Distributed Shared Memory

* Like page table
* "False" Sharing

### Graph computing

* Use graph to express show the relation(the edges represent the correlation of the data).
* Graph-Theoretic Deterministic Algorithm
* GraphChi
* less space, higher locality.

### Object-Based Middleware

* CORBA
* DCOM: Distributed Component Object Model

