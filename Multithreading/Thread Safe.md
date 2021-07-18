### Thread Safe
- Thread running on its own sequencial order won't know what's going on in other threads(以自己的顺序运行的线程不会知道其他线程中发生了什么). A racing condition will arise(出现）logic error and unpredictable results. Thread safely issues usually cannot be detected in compilation time. And sometimes hard to reproduce(再生，复制).
- Common ways to make a code thread-safe:
  - synchronization using lock(使用锁同步)
  - Don't change the shared data(Stateless Class)
    - e.g. AtomicInteger, AtomicBoolean, AtomicDouble....

### synchronized keyword + object locker
- A lock mechanism to make code to be executed just in one thread at the same time.
- The synchronized keyword can be put on method or blocks. when put on blocks, explicit(明确的，清楚的) lock should be declared.
- when the synchronized keyword is put on method, it means only one thread can access this method at the same time.
- https://geek-docs.com/java/java-concurrent/java-memory-model-intro.html

### Leetcode: 1114. Print in Order
```java
class Foo {
    
    private boolean firstFinish = false;
    private boolean secondFinish = false;
    private final Object lock = new Object();

    public Foo() {
        
    }

    public void first(Runnable printFirst) throws InterruptedException {
        synchronized (lock) {
            // printFirst.run() outputs "first". Do not change or remove this line.
            printFirst.run();
            firstFinish = true;
            lock.notifyAll();
        }  
    }

    public void second(Runnable printSecond) throws InterruptedException {
        synchronized (lock) {
            while (!firstFinish) {
                lock.wait();
            }
            // printSecond.run() outputs "second". Do not change or remove this line.
            printSecond.run();
            secondFinish = true;
            lock.notifyAll();
        }
    }

    public void third(Runnable printThird) throws InterruptedException {
        synchronized (lock) {
            while (!secondFinish) {
                lock.wait();
            }
            // printThird.run() outputs "third". Do not change or remove this line.
            printThird.run();
            lock.notifyAll();
        }
    }
}
```

### Volatile Keyword
- The valatile keyword does not cache the value of the variable from CPU, instead, it always read the variable from the main meomory.
- It is used to make classes thread safe.
- https://geek-docs.com/java/java-concurrent/java-memory-model-intro.html

### Concurrent Package

### ThreadLocal

