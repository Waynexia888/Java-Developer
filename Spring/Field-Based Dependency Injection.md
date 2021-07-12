### Field-Based Dependency Injection
- In case of Field-Based DI, we can inject the dependencies by marking them with an ***@Autowired annotation***:
```java
public class Store {
    @Autowired
    private Item item; 
}
```
- While constructing the Store object, if there's no constructor or setter method to inject the Item bean, the container will use reflection to inject Item into   Store.
- We can also achieve this using ***XML configuration*** (not recommend)
  - This approach might look simpler and cleaner, but we don't recommend using it because it has a few drawbacks such as:
  - This method ***uses reflection to inject the dependencies***, which is **costlier than constructor-based or setter-based injection**.
  - It's really easy to keep adding multiple dependencies using this approach. If we were using constructor injection, having multiple arguments would make us think that the class does more than one thing, which can violate the Single Responsibility Principle.
- @Autowired: Wiring allows the Spring container to automatically resolve dependencies between collaborating beans by inspecting the beans that have been defined.
- 参考: https://www.baeldung.com/inversion-control-and-dependency-injection-in-spring

### Spring Annotations
- The ***@ComponentScan*** annotation is used with the ***@Configuration*** annotation to tell Spring the packages to scan for annotated components. 
- ***@ComponentScan*** also used to specify base packages and base package classes using thebasePackageClasses or basePackages attributes of @ComponentScan.
- ***@Configuration*** annotation indicates that a class declares one or more @Bean methods and may be processed by the Spring container to generate bean definitions and service requests for those beans at runtime.
- ***@Beam is a method level annotation*** and name of the method serves as the bean name. 
- In most typical applications, we have distinct layers like data access, presentation, service, business, etc.
  Additionally, in each layer we have various beans. To detect these beans automatically, Spring uses classpath scanning annotations.
  Then it registers each bean in the ApplicationContext.
  Here's a quick overview of a few of these annotations: (below are the ***class level annotation***)
- ***@Component*** is a generic stereotype for any Spring-managed component.
- ***@Controller*** annotates classes at the contorller layer in MVC application.
- ***@Service*** annotates classes at the service layer.
- ***@Repository*** annotates classes at the persistence layer, which will act as a database repository(or DAO).
- https://www.baeldung.com/spring-component-repository-service

### Mind Mapping
- <img src="https://github.com/Waynexia888/Java-Developer/blob/main/Images/mind-mapping.png" width="1000" height="400">

### Component Scan （Open annotation (also called scan package)）
```java
<!--XML配置开启组件扫描，才能使用注解-->
<context:component-scan base-package="com.imooc">
  <context:exclude-filter type="regex" expression="com.imooc.exl.*"/>
</context:component-scan>
```

### Annotation-based Container Configuration
- 1.9 https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-annotation-config
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd">
    <!--    在IoC容器初始化时自动扫描四种组件类型注解 并完成实例化
        @Component
        @Controller
        @Service
        @Repository
    -->
    <context:component-scan base-package="com.imooc"/>
</beans>
```

### IntelliJ IDEA
- sout -> (System.out.println())
- command + N -> getter and setter
- psvm (public static void main(String[] args) {})
- command + o -> search file/class/symbols/actions

### Wiring in Spring: @Autowired, @Inject, @Resource
- Match by type
  - @Autowired: 按容器内对象类型动态注入属性，由Spring机构提供
  - @Inject: The @Inject annotation belongs to the JSR-330 annotations collection. 其他同@Autowired，但不支持required属性
- Match by name
  - @Named: 与@Inject配合使用，JSR-330规范，按属性名自动装配属性
  - @Resource: The @Resource annotation is part of the JSR-250 annotation collection, 优先按名称，再按类型智能匹配
- 参考： https://www.baeldung.com/spring-annotations-resource-inject-autowire
