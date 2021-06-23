## Four Ways to Creat Thread
- extend Thread class
  - public void run(): is used to perform action for a thread.
  - public void start(): starts the execution of the thread.JVM calls the run() method on the thread.
  - example:
```java
class MyThread extends Thread { // 线程的主体类
    private String title;
    public MyThread(String title) {
        this.title = title;
    }
    @Override
    public void run() {  // 线程的主体方法
        for (int x = 0; x < 10; x++) {
            System.out.println(this.title + "运行, x = " + x);
        }
    }
}
public class ThreadDemo {
    public static void main(String[] args) {
        new MyThread("线程A").start();
        new MyThread("线程B").start();
        new MyThread("线程C").start();
    }
}
```
- implement runnable interface
- which way do you prefer? 
  - I prefer runnable because java only supports single inheritance, so you can only extend one class, but you can implement multiple interface. it gives us more flexibility.

- Thread class methods:
  - start()
  - run()
  - currentThread()
  - getName()
  - setName()
  - yield()
  - join()
  - stop(): deprecated
  - sleep(long mili time)
  - isAlive()

- LifeCycle:
  - reference: https://www.geeksforgeeks.org/lifecycle-and-states-of-a-thread-in-java/
  - Thread class state: cannot start a thread by calling run method; cannot run start() two times
  - The life cycle of the thread in java is controlled by JVM. There has 6 states as follows:
  - new
    - When a new thread is created, it is in the new state. The thread has not yet started to run when thread is in this state. When a thread lies in the new state, it’s code is yet to be run and hasn’t started to execute.
  - runnable
    - A thread that is ready to run is moved to runnable state. In this state, a thread might actually be running or it might be ready run at any instant of time. It is the responsibility of the thread scheduler to give the thread, time to run.
    - A multi-threaded program allocates a fixed amount of time to each individual thread. Each and every thread runs for a short while and then pauses and relinquishes the CPU to another thread, so that other threads can get a chance to run. When this happens, all such threads that are ready to run, waiting for the CPU and the currently running thread lies in runnable state.
  - blocked / waiting
    - When a thread is temporarily inactive, then it’s in one of the following states: Blocked or Waiting
    - For example, when a thread is waiting for I/O to complete, it lies in the blocked state. It’s the responsibility of the thread scheduler to reactivate and schedule a blocked/waiting thread. A thread in this state cannot continue its execution any further until it is moved to runnable state. Any thread in these states does not consume any CPU cycle.
    - A thread is in the blocked state when it tries to access a protected section of code that is currently locked by some other thread. When the protected section is unlocked, the schedule picks one of the thread which is blocked for that section and moves it to the runnable state. Whereas, a thread is in the waiting state when it waits for another thread on a condition. When this condition is fulfilled, the scheduler is notified and the waiting thread is moved to runnable state.
    - If a currently running thread is moved to blocked/waiting state, another thread in the runnable state is scheduled by the thread scheduler to run. It is the responsibility of thread scheduler to determine which thread to run.
  - timed_waitting
    - A thread lies in timed waiting state when it calls a method with a time out parameter. A thread lies in this state until the timeout is completed or until a notification is received. For example, when a thread calls sleep or a conditional wait, it is moved to a timed waiting state.
  - terminated
    - Thread state for a terminated thread. The thread has completed execution.


- Java9 Docs: https://docs.oracle.com/javase/9/docs/api/overview-summary.html#
- Javatpoint Docs: https://www.javatpoint.com/creating-thread