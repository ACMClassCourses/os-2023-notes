# Process & Thread

## Sync

### Lock, Mutex and Semaphore

Race condition

Semaphore by Dijkstra

- need a counter
- a waiting queue (either kernel or user)
- maybe two locks (mutex and a flag/slot)
- order (as a stack)

Mutex
```c
pthread_mutex_lock(&mutex);
pthread_cond_wait(&cond, &mutex);
```

The second line is to avoid sleep with a mutex locked and to make it possible for the consumer to wake it.

### Monitor

To design a sync function in language level.

Avoid the problem caused by a breaking change in architecture

### Memory Barrier

To make sure the consistency

- Before this statement, no matter what the order is (for multi-thread), nothing happened.
- After this statement, ...
- But the statements after this statement cannot be executed before the memory barrier. And vice versa.

### Thread Scheduling

For a scheduler, it should determine who is next.

Algorithm:
- RR
- O(1): In O(1) time complexity
- Staircase Down
- RSDL
- CFS
- Brain Fuck
