### What is garbage collection?
- In java, it's Automatic Garbage Collection, it is the process of looping at heap memory, 
  identifying which objects are in use and which are not. and deleting the unused object.
- Java garbage collector uses Mark and Sweep strategy to clean the heap.
  - Mark is to identify which pieces of memory are in use and which are not
  - sweep is to remove objects identified during the "Mark" phase

- since the garbage collector is only collect those objects that are created by new keyword. so if we create an object without
 new, we can use finalize() method to perform the cleanup processing.
 
- what is the purpose of finalize() method?
  - the finalize() method is used to perform clean up processing just before the object is garbage collected. 

- JVM has five types of GC implementations:
  - Serial Garbage Collector
  - Parallel Garbage Collector
  - CMS Garbage Collector
  - G1 Garbage Collector
  - Z Garbage Collector
  - Each of them has its own approaches differ from each other in terms of performance, threading, concurrency. 
    Each version of java also choose different default GC.
    
 
