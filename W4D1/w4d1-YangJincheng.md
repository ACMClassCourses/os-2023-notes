## OSNotes-W4D1

#### Overview

Scheduler

- Process/Thread Schedule 
  
  + O(1),SD/RSDL,CFS
  
  + Unix's Schedule Principle

- Higher/lower scheduler
  
  + User-level: `/etc/crontab`
  
  + I/O-level: e.g. elevator disk scheduling

#### Lecture Notes

**Q1: Preformance (system) vs. Fairness (user) conflicts**

users want a fair share of CPU, while frequent task switch results in low efficiency 

**Q2: Time slice vs. Priority**

a larger time slice or a higher priority

**Priority Inversion Problem (PIP)**

In computer science, priority inversion is a scenario in scheduling in which a high priority task is indirectly superseded by a lower priority task effectively inverting the assigned priorities of the tasks. This violates the priority model that high-priority tasks can only be prevented from running by higher-priority tasks. Inversion occurs when there is a resource contention with a low-priority task that is then preempted by a medium-priority task.

**O(1) scheduler**

An O(1) scheduler (pronounced "O of 1 scheduler", "Big O of 1 scheduler", or "constant time scheduler") is a kernel scheduling design that can schedule processes within a constant amount of time, regardless of how many processes are running on the operating system.

**Rotating Staircase Deadline (RSDL)**

![[RSDL]](https://static.lwn.net/images/ns/kernel/RSDL1.png)

**Completely Fair Scheduler (CFS)**

In contrast to the previous O(1) scheduler used in older Linux 2.6 kernels, which maintained and switched run queues of active and expired tasks, the CFS scheduler implementation is based on per-CPU run queues, whose nodes are time-ordered schedulable entities that are kept sorted by red–black trees. The CFS does away with the old notion of per-priorities fixed time-slices and instead it aims at giving a fair share of CPU time to tasks (or, better, schedulable entities).

**SCAN (Elevator) algorithm**   

In SCAN disk scheduling algorithm, head starts from one end of the disk and moves towards the other end, servicing requests in between one by one and reach the other end. Then the direction of the head is reversed and the process continues as head continuously scan back and forth to access the disk. So, this algorithm works as an elevator and hence also known as the **elevator algorithm**. As a result, the requests at the midrange are serviced more and those arriving behind the disk arm will have to wait.
