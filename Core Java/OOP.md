### Why OOP SOLID Principle?
- follow the oop solid principle, will increase the code maintainablilty(可维护性) and extensibility(延展性).
- make the code loosely coupled

### SOLID Principle
- ***Single responsibility principle***
  - ***A class should only have a single responsibility or functionality(功能);***
  - Implement multiple functionality in a single class will mashup(混乱) the code, and if any modification is required may affect the whole class.
```java
public class Student {  
    public void printDetails() {  
        //functionality of the method  
    }  
    pubic void calculatePercentage() {  
        //functionality of the method  
    }  
    public void addStudent() {  
        //functionality of the method  
    }  
} 
// The above code snippet violates the single responsibility principle. 
// To achieve the goal of the principle, we should implement a separate class that performs a single functionality only.
```
```java
public class Student {  
    public void addStudent() {  
        //functionality of the method  
    }  
}  

public class PrintStudentDetails {  
    public void printDetails() {  
        //functionality of the method  
    }  
}  

public class Percentage {  
    public void calculatePercentage() {  
        //functionality of the method  
    }  
}  
// Hence, we have achieved the goal of the single responsibility principle by separating the functionality into three separate classes.
```
- ***Open-Closed Principle***
  - ***The module entities should be open for extension but closed for modification.***
```java
public class VehicleInfo {  
    public double vehicleNumber(Vehicle vcl) {  
        if (vcl instanceof Car) {  
            return vcl.getNumber();  
        }
        if (vcl instanceof Bike) {  
            return vcl.getNumber();  
        }  
    }
// If we want to add another subclass named Truck, simply, we add one more if statement that violates the open-closed principle. 
// The only way to add the subclass and achieve the goal of principle by overriding the vehicleNumber() method, 
// as we have shown below.
}  
```
```java
public class VehicleInfo {        
    public double vehicleNumber() {   // java only support single inheritance.
        //functionality               // one class can extend only one class, but one class can implement multiple interfaces
    }                                 // An interface can extend multiple interfaces
}  

public class Car extends VehicleInfo {  
    public double vehicleNumber() {  
        return this.getValue();  
    }  
}

public class Truck extends VehicleInfo {  
    public double vehicleNumber() {  
        return this.getValue();  
    } 
}
// we can add more vehicles by making these vehicles extending from the interface.
// the approach would not affect the existing application.
```
- ***Liskov Substitution Principle***
  - it applies to inheritance in such a way that ***the derived classed(派生类) must be completely substitutable for their base classes.***
  - ***In other words, if class A is a subtype of class B, then we should be able to replace B with A without interrupting the behavior of the program.***
  - It extends the open-close principle and also focuses on the behavior of a superclass and its subtypes. 
```java
public class Student {  
    private double height;  
    private double weight;  
    public void setHeight(double h) {   
        height = h;   
    }  
    public void setWeight(double w) {   
        weight= w;   
    }  
    ...  
}  

public class StudentBMI extends Student {  
    public void setHeight(double h) {  
        super.setHeight(h);  
        super.setWeight(w);  
    }  
    public void setWeight(double h) {  
        super.setHeight(h);  
        super.setWeight(w);  
    }  
} 
// The above classes violated the Liskov substitution principle 
// because the StudentBMI class has extra constraints i.e. height and weight that must be the same. 
// Therefore, the Student class (base class) cannot be replaced by StudentBMI class (derived class).
// Hence, substituting the class Student with StudentBMI class may result in unexpected behavior.
```
- ***Interface Segregation Principle***
  - ***Many client-specific interfaces are better than one general-purpose interface***
  - The goal of the interface segregation principle is similar to the single responsibility principle.
```java
public interface Conversion {  
    public void intToDouble();  
    public void intToChar();  
    public void charToString();  
}  
// The above interface has three methods. If we want to use only a method intToChar(), 
// we have no choice to implement the single method. 
// To overcome the problem, the principle allows us to split the interface into three separate ones.
```
```java
public interface ConvertIntToDouble {  
    public void intToDouble();  
}   

public interface ConvertIntToChar {  
    public void intToChar();  
} 

public interface ConvertCharToString {  
    public void charToString();  
} 

// Now we can use only the method that is required. 
// Suppose, we want to convert the integer to double and character to string then, 
// we will use only the methods intToDouble() and charToString().

public class DataTypeConversion implements ConvertIntToDouble, ConvertCharToString {  
    public void intToDouble() {  
         //conversion logic  
    }  
    public void charToString() {  
        //conversion logic  
    }  
}  
```
- ***Dependency Inversion Principle***
  - The principle states that ***we must use abstraction (abstract classes and interfaces) instead of concrete implementations.***
  - High-level modules should not depend on the low-level module but both should depend on the abstraction
  - Because the abstraction does not depend on detail but the detail depends on abstraction. It decouples the software. 
 ```java
public class WindowsMachine {  
    public final keyboard;  
    public final monitor;  
    public WindowsMachine() {  
        monitor = new monitor();  //instance of monitor class  
        keyboard = new keyboard(); //instance of keyboard class  
    }  
}  
// we face the problem. Because we have tightly coupled the three classes together by using the new keyword. 
// It is hard to test the class windows machine.
// To make the code loosely coupled, we decouple the WindowsMachine from the keyboard by using the Keyboard interface and this keyword.
```
```java
public interface Keyboard {   
    //functionality  
}

public class WindowsMachine {  
    private final Keyboard keyboard;  
    private final Monitor monitor;  
    public WindowsMachine(Keyboard keyboard, Monitor monitor) {  
        this.keyboard = keyboard;  
        this.monitor = monitor;  
    }  
}  
// In the above code, we have used the dependency injection to add the keyboard dependency in the WindowsMachine class. 
// Therefore, we have decoupled the classes.
```
- reference: https://www.javatpoint.com/solid-principles-java
