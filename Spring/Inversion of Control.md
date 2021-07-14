### Interview Question: What is Dependency Injection(DI) and Inversion of Control(IoC)?
- Dependency Injection is a technique /pattern we use to implement Ioc. Inversion of Control is a programming principle. 
  The key of IoC is that ***objects do not create other objects on which they rely to do their work.*** 
  Instead, they get the objects that they need from an oustide source. (for example, an XML configuration file)

### Interview Question: Why we need Dependency Injection(DI)?

### What is the advantages of Dependency Injection(DI) or Inversion of Control(IoC)?
- It make the code lossly coupled.
- It is easy to test
- resuability of code

### let’s understand what a dependency in programming means.
- When class A uses some functionality of class B, then its said that class A has a dependency of class B.
- In Java, before we can use methods of other classes, we first need to create the object of that class (i.e. class A needs to create an instance of class B).
