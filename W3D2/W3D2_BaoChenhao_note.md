### Process & Thread

#### synchronize

- lock, mutex, semaphore
  - mutex means: mutual exclusion.
  - method 1: lock variable. if lock=0, lock=1 and run; if lock =1,wait til lock=0and then run.
  - method 2: **Peterson.** Always try to let others run. Run when all else quit the competition.
  
Mutex
```c
pthread_mutex_lock(&mutex);
pthread_cond_wait(&cond, &mutex);
```

The second line is to avoid sleep with a mutex locked and to make it possible for the consumer to wake it.

#### Monitor
To solve the problem at language level. There will be only one procedure running at a time.

### process scheduling

#### Memory consistency

**memory barriers:** to protect the code sequences, which might be edit by compiler, tomasulo,  etc..

#### scheduling

- Q: who's next?!
  - according to priority.
- Avoiding locks
  - Read-copy-update