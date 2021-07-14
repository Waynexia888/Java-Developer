## Four Ways to Creat Thread
### extend Thread class
  - public void run(): is used to perform action for a thread.
  - public void start(): starts the execution of the thread. JVM calls the run() method on the thread.
  - example:
```java
class MyThread extends Thread { // extend Thread class
    @Override
    public void run() { 
        System.out.println(Thread.currentThread().getName() + " - print in a new thread");
    }
}

class MyThread2 implements Runnable { // implement runnable interface
    @Override
    public void run() {
        System.out.println(Thread.currentThread().getName() + " - print in a new thread");
    }
}

class MyCallableClass implements Callable<String> {  // implement callable interface:
    @Override
    public String call() throws Exception {
        return "Today is " + LocaldateTime.now();
    }
}

public class ThreadDemo {
    public static void main(String[] args) {
        System.out.println(Thread.currentThread().getName() + " - print in main thread");
        MyThread t = new MyThread();
        t.start();
        
        Thread t2 = new Thread(new MyThread2());
        t2.start();
        
        // using Thread pool
        ExecutorService es = Executors.newFixedThreadPool(10);
        es.submit(new MyThread2());  // runnable
        es.shutdown(); 
        
        Future<String> future = es.submit(new MyCallableClass()); // callable
        System.out.println(future.get()); // it will give us the result
    }
}
```
### implement runnable interface

### Interview Question:*** which way do you prefer? 
- I prefer runnable because java only supports single inheritance, so you can only extend one class, but you can implement multiple interface. it gives us more flexibility.

### implement callable interface:


### callable vs runnable
- callable can have a return value
- callable can throw an exception
- callable is override(重写) call() method, while runnable is override run() method.

### Interview Question: run() v.s start() method
- when the program calls start() method, a new thread is created, and code inside run() method is executed in new Thread
- while if you call run() method, no new thread is created, and code inside run() will execute on current Thread.

### why create thread pool, instead of creating 10 new thread object?
- create a thread means you have to aside certain JVM resource to do that. in that case, you frequently create and then recycle, create then recycle, that will lower the perfermance of the JVM. 
- The thread pool is primarily used to reduce the number of application threads and provide management of the worker threads.
- serveal way to create thread pool, for example, 

### implement ThreadPool
- Threads are objects. It takes memory and consumes(消耗) computational power(计算能力) in cpu. To reduce the cost of creating and destorying new threads, and also to confine(限制) the memory usage(内存使用). On the server side application, we use thread pool to pre-populate(预先填充) certain number of threads to be reused by different tasks.
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
