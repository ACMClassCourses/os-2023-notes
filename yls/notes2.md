#### 信号机制

信号 sigal

- 信号的处理有单独的控制流：在trap return之前检查是否还有未处理的信号
- `kill` 系统调用用于发送信号 : default signal for kill is `TERM`
- `sigaction` **注册**一个信号处理函数，并不是在这个地方处理。会陷入内核态在`task_struct`的信号处理表中新建一个信号处理函数
- `old_action`：有时候我们希望限定某个信号处理函数的作用范围，于是在一个地方更改，另外一个地方roll back回去。

```C
sigaction(SIGINT, &copyInterrupted, &previousHandler);
copy(something);
sigaction(SIGINT, &previousHandler, null);
```

- `sigprocmask` 用于阻塞信号，防止信号的处理函数被打断（用于信号的嵌套）
- `sigreturn`：由于信号处理过程的独特控制流（进入用户态处理信号，之前的trap context 可能会被覆盖），sigreturn用于确保目前的trap context还是信号处理之前的trap context（不用的内核处理的方式不一样，我猜）。

#### 进程间通信机制 (Inter-Proccess Communication, IPC)

IPC的方向

- Send
- Recv
- RPC : Remote Procedure Call：可以看做是一次函数调用
- Reply

IPC 方式

- 简单IPC：消息接口
  - 同样是基于共享的内存和轮询的方式
  - 依赖大量轮询内存来判断是否有新的数据到来
- 共享内存：内存结构
- 管道：文件接口
- 信号：信号接口
- 消息队列：消息接口
- 套接字

Pipe 通信机制

- 管道被抽象为文件结构，拥有file descriptor
- FIFO 队列
- 匿名管道：只有两个fd，通过fork的方式继承文件描述符（父子进程通信）
- 命名管道：mkfifo得到一个全局的文件名，可以在不同的进程中打开
