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
- 参考资料:
  -  https://www.javatpoint.com/static-keyword-in-java
