# Dead Lock

## Conditions

- 1. Mutual exclusion
- 2. Hold and wait
- 3. No preemption
- 4. Circular wait condition

## Solution

- Don't care!
- Detection and recovery. Let deadlocks occur, detect them, and then take action.
- Dynamic avoidance by careful resource allocation.
- Prevention, by structurally negating one of the four required conditions.

### Detection

Banker's algorithm

### Avoiding

- Resource Trajectories
- In numeric order