# W3D2 notes

Edit by: Yichao Zhong

## Process & threads

### how to synchronize?

- lock, mutex, semaphore
  - mutex means: mutual exclusion.
  - method 1: lock variable. if lock=0, lock=1 and run; if lock =1,wait til lock=0and then run.
  - method 2: **Peterson.** Always try to let others run. Run when all else quit the competition.

- CLI/busywaiting/sleepwakeup

#### Producer-Consumer problem 

using semaphore.

```cpp
void producer(void){
while(1){
	//...
	down(&empty)
	down(&mutex)
	//...
    //order cannot be reversed!
	up(&mutex)
	up(&full)
}
	
}
```

Monitor: solve the problem at language level. There will be only one procedure running at a time.

### process scheduling

#### Memory consistency

**memory barriers:** to protect the code sequences, which might be edit by compiler, tomasulo,  etc..

> A barrier is: Cannot change two code if one is before-barrier and the other is after-barrier.

#### CPU scheduling

- Q: who's next?!
  - according to priority.
- Avoiding locks
  - Read-copy-update

**Scheduling methods:** 

Run Queue(round robin). time-slice as a unit. Tradeoff: context switch

