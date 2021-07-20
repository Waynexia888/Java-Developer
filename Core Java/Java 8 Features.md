### Functional Interface
- Functional interface is a kind of interface that has only 1 abstract method. but it can have multiple default methods and static methods.
- default method is a method with an implementation
- Static methods are the methods that can be called without creating an object of class. it's belongs to a class rather than an instance of a class.
```java
@FunctionalInterface // annotation is optional
public interface Doable {

  // this is the only abstract method. It doesn't have body.
  int doIt(String event);

  default int defaultMethodDemo1(){ // this is a default method, it has body.
    System.out.println("This is Java");
  }

  static int staticMethodDemo2() {. // this is a static method, it has body.
    System.out.println("Static");
  }
  
}

```
- Commonly used functional interfaces, they are all in JDK, like Runnable, callable, Comparator
```java
public interface Runnable {
    public abstract void run();
}

public interface Callable {
    V call() throws Exception;
}

// this interface has lots of static and default methods, but just has 1 abstract method.
public interface Comparator {
    int compare(T o1, T o2);
}

@FunctionalInterface
public interface Function<T, R> {
    R apply(T t);
}

@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
}

@FunctionalInterface
public interface Supplier<T> {
    T get();
}

@FunctionalInterface
public interface Consumer<T> {
    void accept(T t);
}
```

### Lambda
- Lambda introduce the functional style processing in java, is to simplify the creation of objects from functional interface.
```java
() -> {} //parameter list, arrow, return type
        // parameter list, you can omit their type
        // if you have only one return statement, you an omit the {} and return keyword
        // if you have multiple return statement, you cannot omit the {}

// Assume we have a customized Functional Interface

public interface Doable {
  
  boolean doIt(String type, int number);

}

// the Above functional interface takes two parameter and return 1 boolean.
// we can use lambda like

(String a, int b) -> {return true};
// simplify the return and parameter list.
(a,b) -> true;

// if multiple statements, we cannot omit the {}
(a,b) -> { System.out.println("hi"); return true;}
```
- Some commonly used Lambda:
```java
// Comparator
(a,b)-> a - b; // this can be used to compare two int.
(a,b) -> a.getAge() - b.getAge(); // this can be used to compare two Person's age

// Runnable
Runnable r = () -> { // code to be executed in new thread};
```
### Method reference
- It is a short-cut of lambda, it's used to use existing method to implement a functional interface
```java
Consumer c = (i) -> System.out.println(i);
// using method reference
Consumer c = System.out::prinln;  // notice there is no ().
```
```java
@FunctionalInterface
interface MyInterface {
    public int opertionX(int x);
}

public class Java8MethodReference {
    public static void main(String[] args) {
    
        MyInterface ref = (x) -> (x * x);
        System.out.println(ref.operationX(5));    // 25
    
        MyInterface ref1 = Java8MethodReference :: squareIt;    // method reference
    }
  
    public static int squareIt(int n) {
        return n * n;
    }
}

```
