- https://stackoverflow.com/questions/3918083/what-exactly-is-a-context-in-java

### interview question: What is difference between ApplicationContext and BeanFactory?
- BeanFactory and ApplicationContext both are ways to get beans from your spring IOC container.
- The BeanFactory is the most basic version of IOC containers, and the ApplicationContext extends the features of BeanFactory.
- BeanFactory loads beans on-demand, while ApplicationContext loads all beans at startup. Thus, BeanFactory is lightweight as compared to ApplicationContext
- https://www.baeldung.com/spring-beanfactory-vs-applicationcontext

### interview question: Design pattern - Singleton
- A singleton class means only one object can be created from the class.
- private constructor
- static reference
- get instance

### interview question: what is the default scope for a spring beam?
- default scope of a spring beam is singleton, means that spring, by default, only create one object inside the application context. everytime we use autowire annotation, we always go to the same object, always inject the same object.
- throughout the application context(the application context is container), we have only one object created by spring inside the application context.

### five basic scope for a spring beam?
- singleton
- prototype
- request
- session
- global session
- https://www.tutorialspoint.com/spring/spring_bean_scopes.htm

### interview question: Types of Dependency Injection
- field
- constructor
- setter
- https://www.geeksforgeeks.org/spring-dependency-injection-with-example/
- 
