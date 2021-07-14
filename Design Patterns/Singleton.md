### Singleton
- A singleton class means only one object can be created from the class. and it provides a single point of access to it for any other code.(它为任何其他代码提供了一个单一的访问点。)
- when to use?
  - when a class in your program should have just a single instance available to all clients; 
  - for example, a single database object shared by different parts of the program.
- how to implement?
  - a private static reference (to the only object)
  - a private constructor (make sure ousider cannot use new keyword)
  - public static method to return the only reference (or public static get instance). it is static so we can use Class name to call it. SingletonA.getInstance()
```java
public class SingletonA {

    // a private static reference to the only object.
	  private static final SingletonA instance = new SingletonA();

    // a private constructor, make sure outsider cannot use new keyword.
	  private SingletonA() {
		    if (instance != null) {
			      throw new RuntimeException("Cannot create");
        }  
	  }

    // the only public method to return the only reference.
    // it is static so we can use Class name to call it.  SingletonA.getInstance()
	  public static SingletonA getInstance() {
		    return instance;
	  }
}

// combine all of the above, private constructor, public get instance, static reference.
// object is create eagerly. No thread safety issue in this one.
```

### static keyword
- the static keyword is used for memory management.
- advantage: make your program memory efficient. (i.e., it saves memory)
- static variable: 
  - is used to refer to the common property of all objects. for example, the company name of employees, college name of students, etc.
  - the static variable gets memory only once ***in the class area*** at the time of class loading.
- static method:
  - it belongs to the class rather than the object of a class
  - a static method can be invoked without the need for creating an instance of a class
  - A static method can access static data member and can change the value of it.
```java
class Student {
    int id;
    String name;
    static String college = "UCSD";
    // static method to change the value of static variable
    static void change() {
        college = "UCLA";
    }
}
```
- There are two main restrictions for the **static method**. They are:
  - The static method can not use non static data member or call non-static method directly.
  - this and super cannot be used in static context.
```java
class A{  
    int a=40;//non static  
    public static void main(String args[]){  
        System.out.println(a);  
    }  
```        
- static block
  - is used to initialize the static data member
  - it is executed before the main method at the time of classloading.
```java
class A2  {  
    static {
        System.out.println("static block is invoked");
    }  
    public static void main(String args[]){  
        System.out.println("Hello main");  
    }  
}  
```
- Why is the Java main method static?
  -  It is because the object is not required to call a static method. If it were a non-static method, JVM creates an object first then call main() method that will lead the problem of extra memory allocation.
