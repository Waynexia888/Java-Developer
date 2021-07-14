### Singleton
- A singleton class means only one object can be created from the class. and it provides a single point of access to it for any other code.(它为任何其他代码提供了一个单一的访问点。)
- when to use?
  - when a class in your program should have just a single instance available to all clients; 
  - for example, a single database object shared by different parts of the program.
- how to implement?
  - a private static reference (to the only object)
  - a private constructor (make sure ousider cannot use new keyword)
  - public static method to return the only reference (or public static get instance). it is static so we can use Class name to call it. SingletonA.getInstance()
```java
public class SingletonA {

    // a private static reference to the only object.
	  private static final SingletonA instance = new SingletonA();

    // a private constructor, make sure outsider cannot use new keyword.
	  private SingletonA() {
		    if (instance != null) {
			      throw new RuntimeException("Cannot create");
        }  
	  }

    // the only public method to return the only reference.
    // it is static so we can use Class name to call it.  SingletonA.getInstance()
	  public static SingletonA getInstance() {
		    return instance;
	  }
}

// combine all of the above, private constructor, public get instance, static reference.
// object is create eagerly. No thread safety issue in this one.
```

### 
