### What is Excepting Handling?
- The Exception Handling in Java is one of the powerful ***mechanism to handle the runtime errors*** so that normal flow of the application can be maintained.

### What is Unchecked Exception?
- ***unchecked exception is an exception that is not verified during compile time***
- ***Don't need to be try-catched or decleared.***
- All subclasses of RuntimeException are Unchecked exception.
- e.g. NullPointerException, ArrayIndexOutOfBoundary, etc.

### What is checked exception?
- ***Has to be try-catched or decleared using throws keyword in the method.***
- All subclasses of exception are checked exception.
- e.g. IoException, SQLException

### what is Throwable?
- ***Throwable is the parent class of all exceptions and errors***

```java
class AntraUserNotFoundException extends Exception { // this is an checked exception
    ...                                              // AntraUserNotFoundException is a customed exception we created
}

class Test {
    public void doSomething() throws AntraUserNotFoundException { // declear, otherwise error in compilation.
        throw new AntraUserNotFoundException();
    }
  
    public void doSomethingElse() {
        try {
            doSomething(); // because doSomething throws, so here to catch. otherwise error.
        } catch(AntraUserNotFoundException ex) {
            System.out.println(ex);
        }
    }
}

// If we create an unchecked exception, then no need to declear or try-catch
class AntraUserNotFoundExeption extends RuntimeException {} // this is unchecked exception

public void doSomething() {   // no need to declear or try-catch
    throw new AntraUserNotFoundException();
}
```
### Try-catch-finally
- Multiple catch blocks can be put after a try block.
- Finally block is optional.
- Try-Finally block is also valid. No catch block.

### Throw vs Throws
| throw | throws |
| ----- | ------ |
| throw keyword is used to throw an exception | throws is used to declare an exception |
| Throw is followed by an instance | Throws is followed by class |
| you cannot throw multiple exceptions | You can declare multiple exception. eg. public void doSomething() throws IOException, SQLException |
- https://www.javatpoint.com/difference-between-throw-and-throws-in-java

### Final v.s Finally v.s Finalize
| final | finally | finalize |
| ----- | ------- | -------- |
| Final is a keyword | Finally is a block | Finalize is a method |
| Final is used to apply restrictions on class, method and variable, <br> Final class: you cannot extend it; <br> Final method: you cannot override it; <br> Final variable: the value cannot be changed | Finally block is used to place important code, <br> it will be executed whether exception is handled or not | Finalize is used to perform clean up processing just before object is garbage collected. |
- https://www.javatpoint.com/difference-between-final-finally-and-finalize

### ExceptionHandling with MethodOverriding in Java
- https://www.javatpoint.com/exception-handling-with-method-overriding
