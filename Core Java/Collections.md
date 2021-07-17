### Collections - List
- An ordered collection.
- Allow duplicated (how to define? explaination in below) elements
- is implmented by ArrayList or LinkedList
- ![List](https://github.com/Waynexia888/Java-Developer/blob/main/Images/ArrayList.png)

### Collections - Set
- A collection that contains no duplicate elements.
- Sets contain no pair of elements e1 and e2 such that e1.equals(e2), and at most one null element.
- Same elements in this context refers to two objects are logically identical. 
```java
a1 = new Apple("red"); 
a2 = new Apple("red");
a1.equals(a2);  // if true, then we must override equals() method in Apple class and indicate the color comparison. 
// also by contract, we have to override hashCode() method to ensure the same elements return same hashCode.
```
- HashSet - Internally using HashMap to save the elements as the keys, value is a dummy Object o = new Object();
```java
// See Map session for more detail.
class Apple {
    private String color;
    Apple(String color) {
        this.color = color;
    }
}
//...
public void doSomething(){
    Set<Apple> aSet = new HashSet<>();
    aSet.add(new Apple("RED"));
    aSet.add(new Apple("RED"));
    aSet.size(); // 2, because Apple doesn't override equals method. by default ==. 
                 // so hashSet treat two new Apple as two objects.
}
//...

// if override equals using color field. aSet.size() will be 1. Try it.
```
### Collections - Map
- An object that maps keys to values. A map cannot contain duplicate keys; each key can map to at most one value.
- HashMap
  - In order to make it fast to locate the key-value pair in O(1) time complexity of data retrieval and saving. ***Hahsmap internally uses an array of linkedlist.***
  - Each element in this array is a bucket. Hashmap uses the ***hashcode()*** method to calculate the index of the target bucket. 
  - After finding the bucket, it uses the ***equals()*** method to check if there is duplicate key. 
  - if the operation is get(), then it will return the key-value pair, 
  - if it is put(), it will overwrite the key-value with the new value.
  - If there are two keys having the same hashCode(), due to the nature of hashmap, those two keys will use the same bucket. this is ***hash collision.*** 
  - ***The solution of hash collision*** is to use linkedlist to save all k-v pair and use equals() method to check the duplication of key.
```java
// Create a map of Char-occurency in a string
String str = "AABBCCDD";

HashMap<Character, Integer> data = new HashMap<>();

for (Character c : str.toCharArray()) {
    data.put(c, data.getOrDefault(c, 1));
}
```
- LinkedHashMap
  - Maintain the insertion order of the key-value pairs. This implementation differs from HashMap in that it maintains a doubly-linked list running through all of its entries. This linked list defines the iteration ordering, which is normally the order in which keys were inserted into the map (insertion-order). Note that insertion order is not affected if a key is re-inserted into the map.
- TreeMap
  - The map is sorted according to the natural ordering of its keys, or by a Comparator provided at map creation time, depending on which constructor is used.
