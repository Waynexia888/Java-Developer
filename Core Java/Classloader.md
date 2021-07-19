### What is Classloader?
- java classes are not loaded into memory all at once, but when required by an application. At this point, the java classloader is called by the JRE 
  and these classloader loaded classes into memory dynamically.
- The Java Class Loader is a part of the JRE(Java Runtime Environment)used to load java classes file into the JVM at run time.
- there are three types of classloader, they are parent-child relationship. and each classloader is responsible for loading a specific type of class into the JVM.
- Bootstrap classloader: load all the Java core libraries like java.lang. It doesn't have any parent classloader.
- Extension classloader: it is a child of bootstrap classloader, load classes defined in jar files
- System classloader: it is a child of extension classloader, load classes from the CLASSPATH.

### The Class class
- It is a class named Class in Java.lang package. It is used to describe the meta information inside a class. When a class is loaded from ClassLoader, one(and only one per classloader) Class object will be created.
- Every class or object can call getClass() method or .class field to get the instance of the Class class.
```java
Class c1 = String.class;
Class c2 = "hello".getClass();
Class c3 = "hi".getClass();

System.out.println(c1 == c2); // true
System.out.println(c2 == c3); // true, becuase they all get the same Class object from the classloader.
```
- The object of Class class can perform lots of useful/powerful functionalities related to the class and objects of it.
```java
// a demo class
class Apple{
    private String color;

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}


public class ChangeDataType {

    public static void main(String[] args) throws Exception {
        Class appleClass = Class.forName("net.antra.reflection.Apple"); // Load the class without create object from Apple class
        Apple a = (Apple) appleClass.newInstance(); // create Apple class using Class.
        Constructor[] constructors = appleClass.getConstructors(); // get constructors.
        Method[] methods = appleClass.getDeclaredMethods(); // get methods
        Annotation[] annotations = appleClass.getDeclaredAnnotations(); // get annotations
        Field[] fields =  appleClass.getDeclaredFields(); // get fields
// During the runtime, all the members inside a class is visible to ClassLoader.
// By using Reflection API.
// All the methods and field can be called. Even for those who are private.
        constructors[0].newInstance();
        methods[0].invoke(a);
        fields[0].set(a,"newValue");
    }
}
```

### Reflection API
- Reflection is an Api, using reflection api, we don't need to know the class untill at the runtime.
- Through reflection, all the methods and field can be called. Even for those who are private.
- Combine with annotations, using reflection api can achieve lots of framework jobs. 
- Below is a small "framework" to print out company value in the annotation Antra.
```java
// Framework code: Annotation
@Target({ElementType.METHOD,ElementType.TYPE,ElementType.FIELD})
@Retention(RetentionPolicy.RUNTIME)
public @interface Antra {
    String companyValue() default "Java is the best";
}

// Scanning class
public class ScanDemo {

    public static void scanThisClass(String className) {
        try {
            Class clazz = Class.forName(className);
                        
            //Annotation on top of class
            Annotation[] ann = clazz.getDeclaredAnnotations();
            for (Annotation a : ann) {
                if(a instanceof Antra) {
                    System.out.println(((Antra) a).companyValue());
                }
            }
            //Annotations on Fields
            Field[] fields = clazz.getDeclaredFields();
            for (Field f : fields) {
                Annotation[] fAnn = f.getDeclaredAnnotations();
                for (Annotation a : fAnn) {
                    if(a instanceof Antra) {
                        System.out.println(((Antra) a).companyValue());
                    }
                }
            }
            //Annotation on Methods
            Method[] methods = clazz.getDeclaredMethods();
            for (Method m : methods) {
                Annotation[] mAnn = m.getDeclaredAnnotations();           
                for (Annotation a : mAnn) {
                    if(a instanceof Antra) {
                        System.out.println(((Antra) a).companyValue());
                    }
                }
            }
        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }

}

//////////// with above code, we are able to read the annotation Antra from any class.

//////////// below is usage code.
// Demo Apple 
@Antra(companyValue = "hqweqwei")
public class Apple {

    @Antra(companyValue = ".Net is OK")
    private String color;

    @Antra
    public String getColor(){
        return color;
    }
}

// Demo Test. Run the main method.
public class TestScan {

    public static void main(String[] args) {
        ScanDemo.scanThisClass("net.antra.design.scan.Apple");
    }
}
```
