## Four Ways to Creat Thread
- By extending Thread class
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
- https://docs.oracle.com/javase/9/docs/api/overview-summary.html#
