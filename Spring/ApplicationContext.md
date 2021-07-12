### two types of IoC container
- BeamFactory
- ApplicationContext

### Spring Annotations
- The ***@ComponentScan*** annotation is used with the ***@Configuration*** annotation to tell Spring the packages to scan for annotated components. 
- @ComponentScan also used to specify base packages and base package classes using thebasePackageClasses or basePackages attributes of @ComponentScan.
- @Configuration annotation indicates that a class declares one or more @Bean methods and may be processed by the Spring container to generate bean definitions 
  and service requests for those beans at runtime.
- ***@Beam is a method level annotation*** and name of the method serves as the bean name. 
- In most typical applications, we have distinct layers like data access, presentation, service, business, etc.
  Additionally, in each layer we have various beans. To detect these beans automatically, Spring uses classpath scanning annotations.
  Then it registers each bean in the ApplicationContext.
  Here's a quick overview of a few of these annotations: (below are the ***class level annotation***)
- @Component is a generic stereotype for any Spring-managed component.
- @Controller annotates classes at the contorller layer in MVC application.
- @Service annotates classes at the service layer.
- @Repository annotates classes at the persistence layer, which will act as a database repository(or DAO).
- https://www.baeldung.com/spring-component-repository-service

### Component Scan
```java
<!--XML配置开启组件扫描，才能使用注解-->
<context:component-scan base-package="com.imooc">
  <context:exclude-filter type="regex" expression="com.imooc.exl.*"/>
</context:component-scan>
```
