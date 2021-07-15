### Primitive Types (non-referenced types)
- There are 8: boolean , byte , char , short , int , long , float and double.
- They don't have any method. Because primitive type variables are directly pointing to the value not object.
- Can be compared with == 

### Non-Primitive Types (referenced types)
- e.g. Annotations, class, array, interface, Enum
- They are pointing to the reference of an object.
```java
Object o = new Object();
Object o1 = o;
// o1 and o are pointing to the save object
```

### Interview Questions: What is the difference between == and equals method?
- Compare with ==: will compare the reference value(the pointed location)
- Compare with equals(Object obj): will call the equals method of the object(default equals method is implemented by ==, which will compare their reference value), 
if we want to compare their content, we need to override equals method.
### What do you need to do if you override equals method? -> equals() and hashcode()
- we should also override the hashCode() method.
- hashcode() method is return the memory reference of the object in Integer form.
### How will you try to store an object element into a hashset?
### Given a hashset, what will you do if you wanna store Person object as key in hashmap?

```java
o1 == o; // true
o1.equals(o); // true, because by default equals is implemented by ==. Check the Object class.

class Apple{
    String color;
    Apple(String color){
        this.color = color;
    }
}

Apple a1 = new Apple("RED");
Apple a2 = new Apple("RED");

a1 == a2;  // false; They are different object.
a1.equals(a2); // false; We didn't override equals().

// to make a1.equals(a2) to return true
class Apple {
    //....
    public boolean equals(Object obj){
        // sanity check, type check
        //...
        Apple a = (Apple)obj;
        return a.color.equals(this.color);
    }
}
```
```java
Integer i1 = 100;
Integer i2 = 100;
System.out.println(i1 == i2); // true, because in IntegerCache, the high value is 127, the low value is -128. Integer valueOf(int i) {} 

Integer i3 = 1000;
Integer i4 = 1000;
System.out.println(i3 == i4); // false, since the value exceed the high value in IntergerCache
```

### final keyword
- the final keyword is used to restrict the user
- final variable means we cannot change the value of the variable. (it will be constant)
- final method means we cannot override it (the method)
- final class means we cannot extend it (the class)
- 
### Is string immutable or not?
- string is immutable

### How to design an immutable class?
- every time you deal with reference type, don't forgot the deep copy
- final class
- private fields
- Don't provide setter methods for variables.
- deep copy
- 参考： https://www.geeksforgeeks.org/create-immutable-class-java/
