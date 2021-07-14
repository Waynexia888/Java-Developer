## Four Ways to Creat Thread
### extend Thread class
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
### implement runnable interface

### Interview Question:*** which way do you prefer? 
- I prefer runnable because java only supports single inheritance, so you can only extend one class, but you can implement multiple interface. it gives us more flexibility.

### implement callable interface:
- 

### callable vs runnable
- callable can have a return value
- callable can throw an exception
- callable is override(重写) call() method, while runnable is override run() method.

### why create thread pool, instead of creating 10 new thread object?
- create a thread means you have to aside certain JVM resource to do that. in that case, you frequently create and then recycle, create then recycle, that will lower the perfermance of the JVM. 
- The thread pool is primarily used to reduce the number of application threads and provide management of the worker threads.
- serveal way to create thread pool, for example, 

### implement ThreadPool
- Thread pool represents a group of worker threads that are waiting for the job and reuse many times.
- In case of thread pool, a group of fixed size threads are created. A thread from the thread pool is pulled out and assigned a job by the service provider. After completion of the job, thread is contained in the thread pool again.
- Advantage: Better performance It saves time because there is no need to create new thread.
- Real time usage: It is used in Servlet and JSP where container creates a thread pool to process the request.
- 4 basic thread pool we can create in java
  - cachedThreadPool
  - FixedThreadPool(10)
  - SingleThreadPool
  - ScheduleThreadPool
- thread pool using ExecutorService and Executors

### Thread class methods:
  - start() -> starts the execution of the thread.JVM calls the run() method on the thread.
  - run() -> is used to perform action for a thread.
  - currentThread() -> returns the reference of currently executing thread.
  - getName() -> returns the name of the thread.
  - setName(String name): changes the name of the thread.
  - yield() -> causes the currently executing thread object to temporarily pause and allow other threads to execute.
  - join() -> waits for a thread to die
  - stop(): deprecated
  - sleep(long mili time) -> Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds.
  - isAlive() -> tests if the thread is alive.

- Java9 Docs: https://docs.oracle.com/javase/9/docs/api/overview-summary.html#
- Javatpoint Docs: https://www.javatpoint.com/creating-thread
