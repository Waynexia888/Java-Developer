## Four Ways to Creat Thread
- ***extend Thread class***
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
- ***implement runnable interface***

- ***Interview Question:*** which way do you prefer? 
  - I prefer runnable because java only supports single inheritance, so you can only extend one class, but you can implement multiple interface. it gives us more flexibility.

- ***Thread class methods:***
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
