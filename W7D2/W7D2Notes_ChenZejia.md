## W7D2 notes

**written by Chen Zejia.**

## Deadlock

### Definition

A set of process is deadlocked if:

* Each process is waiting for an event
* That event can be caused only by another process

### Conditions:

* Mutual exclusion
* Hold and wait
* No preemption
* Circular wait condition

### Solutions

* Don't care, ignore the problem.
* Detection and recovery
  * use something(e.g. matrix/graph) to maintain the resources.
* Dynamic avoidance by careful resource allocation.
* Prevention, by structurally negating one of the four required conditions:
  * Mutual exclusion 
  * Hold and wait: Request all resources initially
  * No preemption:  Take resources away
  * Circular wait: Order resources numerically

### Banker's algorithm

