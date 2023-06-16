# Dead Lock

## Conditions

1. Mutual exclusion
1. Hold and wait
1. No preemption
1. Circular wait condition

## Solution

- Don't care!
- Detection and recovery. Let deadlocks occur, detect them, and take action.
- Dynamic avoidance by careful resource allocation.
- Prevention, by structurally negating one of the four required conditions.

### Detection

Banker's algorithm

### Avoiding

- Resource Trajectories
- In numeric order
