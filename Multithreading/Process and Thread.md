## Interview Question: What is a Progarm && a Process 进程 and a Thread 线程?

- a **program** is the static codes that we write down.
- a **process** is an execution of a program. The Java Virtual Machine allows an application to have multiple threads of execution running concurrently
- a **thread** is a light-weight process. It's a unit of execution within a given process(a process may have several threads). Each thread in a process shares the memory and resources.
- Thread class represent a virtual thread.
- One thread object can only be started once.

### Multithreading advantages:
- we can design more responsive applications: we can do several operations concurrently.
- we can achieve better resource utilization.
- we can improve performance of the program.
