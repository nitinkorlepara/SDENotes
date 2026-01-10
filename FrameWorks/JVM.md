# Java Virtual Machine

### **Garbage Collection**

Memory in java is divided into **Stack** and **Heap**:

- **Stack**: Stores primitive values and object references; memory is automatically freed when variables go out of scope
- **Heap**: Stores actual objects; managed by Garbage Collection to reclaim unused memory

**Marking in GC** : 
The GC process identifies which objects are still reachable from root references (stack variables, static fields, etc.). Objects not reachable are marked for deletion. During the sweep phase, unmarked objects are removed and their memory is reclaimed. This prevents memory leaks and allows Java applications to run without manual memory management.

**Sweeping in GC** : 
After marking, the GC removes all unmarked objects from the heap and consolidates free memory. This phase compacts the heap, reducing fragmentation and improving memory allocation efficiency. The reclaimed memory becomes available for new object allocation.

- **Sweeping Strategies in GC**: The sweep phase can employ different strategies
    1. Normal Sweeping simply removes unmarked objects
    2. Sweeping with Compacting consolidates remaining objects to reduce fragmentation
    3. Sweeping with Copying moves live objects to a new memory region while clearing the old region entirely.

**Generations in GC** : 
Java's generational garbage collection divides the heap into Young Generation and Old Generation based on object lifespan. Most objects die young, so the Young Generation is collected frequently with short pauses. Long-lived objects are promoted to the Old Generation, which is collected less often. This approach optimizes GC performance by focusing intensive collection on where most garbage is created.

- **Metaspace in GC** : 
Metaspace is a memory region that stores class metadata (bytecode, method data, constant pools, field data, code for methods, and runtime constant pool data). Unlike the heap, Metaspace is allocated in native memory and is not subject to garbage collection in the traditional sense. When a class loader is no longer referenced and all its classes are unloaded, Metaspace reclaims the associated memory. This design eliminates the fixed PermGen size limitations and allows Metaspace to grow dynamically based on application needs.

**Different GC Types**: 

1. **Serial GC**: A simple garbage collector that uses a single thread for both marking and sweeping. It is suitable for small applications with low memory requirements.
    ``` 
    javac YourProgram.java
    java -XX:+UseSerialGC YourProgram
    ```
2. **Parallel GC**: Also known as throughput collector, it uses multiple threads for garbage collection, improving performance for applications with large heaps and multi-core processors.
    ``` 
    javac YourProgram.java
    java -XX:+UseParallelGC YourProgram

    java -XX:+UseParallelGC -XX:ParallelGCThreads=4 YourProgram
    ```
3. **CMS GC (Concurrent Mark Sweep)**: A collector that minimizes pause times by performing most of its work concurrently with the application threads. It is designed for applications that require low latency.
    ``` 
    javac YourProgram.java
    java -XX:+UseConcMarkSweepGC YourProgram
    ```
4. **G1 GC (Garbage-First)**: A server-style garbage collector that divides the heap into regions and prioritizes the collection of regions with the most garbage. It aims to provide predictable pause times.
    ``` 
    javac YourProgram.java
    java -XX:+UseG1GC YourProgram
    ```
5. **Z GC**: A low-latency garbage collector that aims to keep pause times short, even for large heaps. It uses a concurrent approach to minimize the impact on application performance.
    ``` 
    javac YourProgram.java
    java -XX:+UseZGC YourProgram
    ```
Other Useful Options
```
# View GC details
java -XX:+UseG1GC -XX:+PrintGCDetails -XX:+PrintGCTimeStamps YourProgram

# Set heap size
java -XX:+UseG1GC -Xms512m -Xmx2g YourProgram

# Enable GC logging (Java 9+)
java -XX:+UseG1GC -Xlog:gc* YourProgram
```

### JVM Tuning 

Determine requirements, measure and adjust
- jstat
: A command-line tool that monitors JVM statistics such as garbage collection behavior, heap memory usage, and class loading. It provides real-time insights into JVM performance without requiring application restart.
    ```
    jstat -gc -h10 <pid> 1000
    jstat -gccause <pid>
    jstat -class <pid>
    ```