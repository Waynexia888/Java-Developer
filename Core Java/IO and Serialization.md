### I/O 
- I/O (input and output) is used to process the input and produce the output.
- Java uses the concept of a stream to make I/O operation fast.
- stream
  - A stream is a sequence of data, and it is composed of bytes.
  - In java, 3 streams are created for us automatically.
    - System.out: standard output stream
    - System.in: standard input stream
    - System.err: standard error stream
- OutputStream
   - Java application uses an output stream to ***write data to a destination;*** it may be a file, an array, peripheral device or socket.
   - OutputStream class is an abstract class. It is the superclass of all classes representing an output stream of ***bytes.***
- InputStream
  - Java application uses an input stream to ***read data from a source;*** it may be a file, an array, peripheral device or socket.
  - InputStream class is an abstract class. It is the superclass of all classes representing an input stream of ***bytes.***
- ***Byte Stream***
  - Read/write in flow of byte(8 bits)
  - InputStream and OutputStream are two parent classes.
- Character Stream
  - Read/write in flow of 2-bytes.
  - Reader and Writer are two parrents class.
- https://www.javatpoint.com/java-io

### Serialization && Deserialization
- Serialization is a mechanism of converting the state of an object into a byte stream. 
- The reverse operation of serialization is called deserialization where byte-stream is converted into an object.
- For serializing the object, we call the ***writeObject()*** method ObjectOutputStream, 
- and for deserialization we call the ***readObject()*** method of ObjectInputStream class.
- We must have to implement the ***Serializable interface*** for serializing the object.
- Advanatges:
  - Used for marshaling (traveling the state of an object on the network)
  - used to persist the (state of the) object.
- Transient Keyword
  - transient keyword is used in serialization. ***If you define any data member as transient, it will not be serialized.***
```java
public class SerializationDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Person p = new Person("wayne", 20);
        serialize(p);
        deserialize();
    }

    private static void serialize(Person p) throws IOException {
        FileOutputStream fos = new FileOutputStream("person.data"); // writing data to a File
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(p);
        System.out.println("Done");
    }

    private static void deserialize() throws IOException, ClassNotFoundException {
        FileInputStream fis = new FileInputStream("person.data"); // read data from a source
        ObjectInputStream ois = new ObjectInputStream(fis);
        Object obj = ois.readObject();
        Person p = (Person)obj;
        System.out.println(p);
//        System.out.println(obj);
    }
}

class Person implements Serializable {
    static final long serialVersionUID = 42L; // once you serialize(p), you change/delete some fields or methods
    private String name;                      // as long as you keep serialVersionUID the same, you can still deserialize back
    private transient int age;               // the int age will not be serialized since it has a transient keyword

    private static String CLASS_NAME = "ABC"; // static variable won't be serialized
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }

}
```

