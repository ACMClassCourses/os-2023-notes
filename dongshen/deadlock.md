**deadlock** is any situation in which no member of some group of entities can proceed because each waits for another member, including itself, to take action, such as sending a message or, more commonly, releasing a lock
A deadlock situation on a resource can arise only if all of the following conditions occur simultaneously in a system:
1.  _Mutual exclusion:_ At least one resource must be held in a non-shareable mode; that is, only one process at a time can use the resource. Otherwise, the processes would not be prevented from using the resource when necessary. Only one process can use the resource at any given instant of time.
2.  _Hold and wait_ or _resource holding:_ a process is currently holding at least one resource and requesting additional resources which are being held by other processes.
3.  _No preemption:_ a resource can be released only voluntarily by the process holding it.
4.  _Circular wait:_ each process must be waiting for a resource which is being held by another process, which in turn is waiting for the first process to release the resource. In general, there is a set of waiting processes, _P_ = {_P_1, _P_2, …, _P__N_}, such that _P_1 is waiting for a resource held by _P_2, _P_2 is waiting for a resource held by _P_3 and so on until _P__N_ is waiting for a resource held by _P_1._
These four conditions are known as the _Coffman conditions_ from their first description in a 1971 article by Edward G. Coffman, Jr.
While these conditions are sufficient to produce a deadlock on single-instance resource systems, they only indicate the possibility of deadlock on systems having multiple instances of resources.

Eliminate deadlock
1. detect cycle by dfs or cutting branches
2. try all the possible allocation patterns
detection: (find deadlocks happening)banker's algorithm
avoidance: (avoid deadlocks at most extent)resource trajectories (check point and roll back)
prevention: (remove conditions, definitely no deadlock)
1. attack circular waiting condition
   1. mutial exclusion: spool everything and hide the resources
   2. hold and wait:request all the rescources intially
   3. preemption: take resources away
   4. circular wait: order all the resources numerically
busy waiting: livelock
signal : deadlock