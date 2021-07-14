## Interview Question: What is a Progarm && a Process 进程 and a Thread 线程?

- a **program** is the static codes that we write down.
- a **process** is an execution of a program. during that execution, we have multiple threads, all the threads can share the same memory. and then commucation bwtween threads are way more cheaper than communication between processes. Basicly, different process means we are running different program. but different thread within the same process/ during the same work, each thread is nothing, but is an execution runtime of a process.
- a **thread** is an execution runtime of a process.
- 线程是在进程基础之上划分的更小的程序单元，线程是在进程基础上创建并且使用的，所以线程依赖于进程的支持，但是线程的启动速度要比进程快很多，所以当使用多线程进行并发处理的时候，其执行的性能要高于进程。
- Java是多线程的编程语言，所以Java在进行并发访问处理的时候可以得到更高的处理性能。
