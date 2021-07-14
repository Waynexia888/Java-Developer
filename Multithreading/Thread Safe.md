### Thread Safe
- Thread running on its own sequencial order won't know what's going on in other threads(以自己的顺序运行的线程不会知道其他线程中发生了什么). A racing condition will arise(出现）logic error and unpredictable results. Thread safely issues usually cannot be detected in compilation time. And sometimes hard to reproduce(再生，复制).
- Common ways to make a code thread-safe:
  - synchronization using lock(使用锁同步)
  - Don't change the shared data(Stateless Class)

### synchronized keyword + object locker
- A lock mechanism to make code to be executed just in one thread at the same time.
- The synchronized keyword can be put on method or blocks. when put on blocks, explicit(明确的，清楚的) lock should be declared.

### Volatile Keyword

### Concurrent Package

### ThreadLocal

