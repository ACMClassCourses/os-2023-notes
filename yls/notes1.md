#### fork, vfork, clone 等创建线程方法

- fork ：直接拷贝一份
- vfork : 父子进程共享内存，会有冲突和竞争：在vfork函数中，判断创建出的子进程是否exec或者exit，否则一直yield

```rust
pub fn vfork() -> isize{
    ...
    while !exec_or_exit(child_pid) {
        yield();
    }
}
```

- clone ： 可以指定父子进程共享的资源，比如内存，文件描述符等

#### process, thread, coroutine

- 进程用于管理一系列的资源，各自的地址空间隔离
- 不同的线程可以处于同一进程，共享地址空间，但是可以运行在不同的core上，并且享有独立的运行栈
- Thread Contorl Block (TCB)

#### 进程调度

HRRN (Highest Response Ratio Next) 策略

- 响应比 = (等待时间 + 服务时间) / 服务时间

$$
\text{Response Ratio} = \frac{T_{\text{wait}}}{T_{\text{run}}} + 1
$$

多级队列调度

- 多个队列，有不同的优先级
- 只有高优先级的任务做完之后才有可能轮到低的优先级
- 同一优先级的任务可以采用Round Robin的方式，即分时复用
- 造成严重的低优先级饥饿：优先级提升，设置等待阈值

多级反馈队列 (Multilevel Feedback Queue)

- 短任务，高优先级，低时间片
- 动态调整优先级：执行时间超过预设，降低优先级
- 定时将所有任务优先级重置为最高优先级，防止低优先级任务饥饿
