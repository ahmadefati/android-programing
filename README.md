# android-programing
## Coroutines and LaunchedEffectsin Jetpack Compose
[DisposableEffect](DisposableEffect.pdf)

## lifecycle of View
[ViewTreeObserver](ViewTreeObserver.pdf)
 
## Compose Flow
[SnapshotFlow](SnapShotFlow.pdf)
[ProduceState](ProduceState.pdf)
[DerivedState](DerivedState.pdf)

#### OOP

* **Explain OOP Concepts.**
 [OOP](OOP.pdf)

* **Explain SOLID Concepts.**
 [SOLID](SOLID.pdf)


* **Differences between abstract classes and interfaces?**
  [abstractVSinterface](abstractVSinterface.pdf)
    - An abstract class, is a class that contains both concrete and abstract methods 
    (methods without implementations). An abstract method must be implemented by the abstract class
     sub-classes. Abstract classes cannot be instantiated and need to be extended to be used.
    - An interface is like a blueprint/contract of a class (or it may be thought of as a class with methods, but without their implementation). It contains empty methods that 
    represent, what all of its subclasses should have in common. The subclasses provide the 
    implementation for each of these methods. Interfaces are implemented.

* **Difference between method overloading and overriding.**

* **What are the access modifiers you know? What does each one do?**
[accessModifier](accessModifier.pdf)
  

* **Can an Interface implement another Interface?**
  - Yes, an interface can implement another interface (and more than one), but it needs to use `extends`, rather than `implements` keyword. And while you can not remove methods from parent interface, you can add new ones freely to your sub-interface.

#### Collections and Array And ArrayList
[ArrayVsCollections](ArrayVsCollections.pdf)

* **Arrays Vs ArrayLists** - [Learn from here](https://stackoverflow.com/questions/32020000/what-is-the-difference-between-an-array-arraylist-and-a-list/32020072)

* **HashSet Vs TreeSet** - [Learn from here](https://stackoverflow.com/questions/25602382/java-hashset-vs-treeset-when-should-i-use-over-other)

* **HashMap Vs Set** - [Learn from here](https://stackoverflow.com/questions/2773824/difference-between-hashset-and-hashmap)

[boxingAndUnboxing](boxingAndUnboxing.pdf)

#### Objects and Primitives

* **How is `String` class implemented? Why was it made immutable?**
  - There is no primitive variant of `String` class in Java language - all strings are just wrappers around underlying array of characters, which is declared `final`. This means that, once a `String` object is instantiated, it cannot be changed through normal tools of the language (Reflection still can mess things up horribly, because in Java no object is truly immutable). This is why `String` variables in classes are the first candidates to be used, when you want to override `hashCode()` and `equals()` of your class - you can be sure, that all their required contracts will be satisfied.
    > Note: The String class is immutable, so that once it is created a String object cannot be changed. The String class  has a number of methods, some of which will be discussed below, that appear to modify strings. Since strings are  immutable, what these methods really do is create and return a new string that contains the result of the operation. ([Official Java Documentation](https://docs.oracle.com/javase/tutorial/java/data/strings.html))

    This class is also unique in a sense, that, when you create an instance like this:
    ```java
    String helloWorld = "Hello, World!";
    ```
    `"Hello, World!"` is called a *literal* and compiler creates a `String` object with its' value. So
    ```java
    String capital = "Hello, World!".toUpperCase();
    ```
    is a valid statement, that, firstly, will create an object with literal value "Hello, World!" and then will create and return another object with value "HELLO, WORLD!"
  - `String` was made immutable to prevent malicious manipulation of data, when, for example, user login or other sensitive data is being send to a server.

* **What does it means to say that a `String` is immutable?**
    - It means that once created, `String` object's `char[]` (its' containing value) is declared `final` and, therefore, it can not be changed during runtime.

* **Can you list 8 primitive types in java?**
    - `byte`
    - `short`
    - `int`
    - `long`
    - `float`
    - `double`
    - `char`
    - `boolean`

* **What is the difference between an Integer and int?**
  - `int` is a primitive data type (with `boolean`, `byte`, `char`, `short`, `long`, `float` and `double`), while `Integer` (with `Boolean`, `Byte`, `Character`, `Short`,`Long`, `Float` and `Double`) is a [wrapper](https://docs.oracle.com/javase/tutorial/java/data/numberclasses.html) class that encapsulates primitive data type, while providing useful methods to perform different tasks with it.

* **Do objects get passed by reference or value in Java? Elaborate on that.**

#### Java Memory Model and Garbage Collector

* **What is garbage collector? How does it work?**
  - All objects are allocated on the heap area managed by the JVM.
  As long as an object is being referenced, the JVM considers it alive.
  Once an object is no longer referenced and therefore is not reachable by the application code,
  the garbage collector removes it and reclaims the unused memory.

#### Concurrency

* **What does the keyword `synchronized` mean?**

* **What is a `ThreadPoolExecutor`?** - [ThreadPoolExecutor in Android](https://outcomeschool.com/blog/threadpoolexecutor-in-android)

* **What is `volatile` modifier?**

* **Object Level Lock vs Class Level Lock in Java** - [Learn from here](https://x.com/amitiitbhu/status/1818156936413778332)

* **Concurrency vs Parallelism** - [Learn from here](https://www.linkedin.com/posts/pallavi-shekhar_outcomeschool-softwareengineering-activity-7226208648115404801-u8uu)

* **The classes in the atomic package expose a common set of methods: `get`, `set,`, `lazyset`, `compareAndSet`, and `weakCompareAndSet`. Please describe them.**

#### Exceptions

* **How does the `try{}`, `catch{}`, `finally` works?**

* **What is the difference between a `Checked Exception` and an `Un-Checked Exception`?**

#### Others

* **Shallow vs. Deep Copy in Java** - [Learn from here](https://www.linkedin.com/posts/amit-shekhar-iitbhu_outcomeschool-softwareengineering-activity-7224635014641016834-j8X1)

* **Explain Serialization and Deserialization** - [Learn from here](https://www.linkedin.com/posts/pallavi-shekhar_outcomeschool-softwareengineering-tech-activity-7228977637916823552-Bo2N)

* **What is serialization? How do you implement it?**

* **What is `transient` modifier?**

* **What are anonymous classes?**

* **What is the difference between using `==` and `.equals` on an object?**

* **What is the `hashCode()` and `equals()` used for?**

* **When would you make an object value `final`?**

* **What are these `final`, `finally` and `finalize` keywords?**

* **What is the difference between "throw" and "throws" keyword in Java?**
    - `throws` is just used to indicated which exception is to be thrown. But the `throw` keyword is used to throw some exception from any static block or any method.

* **What does the `static` word mean in Java?**
    - In case of `static` variable it means that this variable (its' value or the object it references) spans across all instances of enclosing class (changing it in one instance affects all others), while in case of `static` methods it means that these methods can be invoked without an instance of their enclosing class. It is useful, for example, when you create util classes that need not be instantiated every time you want to use them.

* **Can a `static` method be overridden in Java?**
    - While child class can override a static method with another static method with the same signature (return type can be down-casted), it is not truly overridden - it becomes "hidden", but both methods can still be accessed under right circumstances (see question about overloading/overriding above).

* **When is a `static` block run?**
    - Code inside static block is executed only once: the first time you make an object of that class or the first time you access a static member of that class (even if you never make an object of that class).

* **Explain Reflection in Java** - [Learn from here](https://x.com/amitiitbhu/status/1819234916812341567)

* **What is Dependency Injection?**

* **Difference between `StringBuffer` and `StringBuilder`?** - [Learn from here](https://outcomeschool.com/blog/string-vs-stringbuffer-vs-stringbuilder)

* **What is the difference between fail-fast and fail-safe iterators in Java?**

* **Monitor and Synchronization**

