## W3D2 notes

**written by Chen Zejia.**

## Process/Thread

### Sync

* lock, mutex, semaphore
  * mutex: shared, exclusive. It might lead to Race Condition.
* CLI: Clear Interrupt.
* Busywating: keep testing and setting(might be no atomic).
* Sleep and wake up
* Semaphone by Dijkstra
* RCU: read-copy-update

### producer-consumer problem

* using semaphores: use a counter/waiting queue. The order of up/down cannot be revered.
* mutex in pthread: condition variable and mutex
* Monitors: try to solve this in language level. Every time there are at most one procedure running at a time. Use condition variable to switch.

### Barriers

* Memory barriers: it is used to avoid the reverse of the operation of memory(eg: Tomasulo in ARH, 
* Memory consistency.

### Schedule

* Priority, time slice(time-use unit)
* RR 
* O(1): use to two queues to maintain the processes
* Staircase Down -> RSDL
* CFS
* Brain Fuck

