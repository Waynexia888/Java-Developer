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

### Annotation-based Container Configuration
- https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-annotation-config

### IntelliJ IDEA
- sout -> (System.out.println())
- command + N -> getter and setter
- psvm (public static void main(String[] args) {})
- command + o -> search file/class/symbols/actions

### @Autowired, @Inject, @Resource
- Match by type
  - @Autowired: 按容器内对象类型动态注入属性，由Spring机构提供
  - @Inject: The @Inject annotation belongs to the JSR-330 annotations collection. 其他同@Autowired，但不支持required属性
- Match by name
  - @Named: 与@Inject配合使用，JSR-330规范，按属性名自动装配属性
  - @Resource: The @Resource annotation is part of the JSR-250 annotation collection, 优先按名称，再按类型智能匹配
- https://www.baeldung.com/spring-annotations-resource-inject-autowire
