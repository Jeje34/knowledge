# Basics of Java Interview Questions

## Difference between JDK,JRE and JVM ?

**JVM** is an acronym for **Java Virtual Machine**, it is an abstract machine which provides the runtime environment in which java bytecode can be executed.

**JRE** stands for **Java Runtime Environment**. It is the implementation of JVM, it physically exists. It contains set of libraries + other files that JVM uses at runtime.

**JDK** is an acronym for **Java Development Kit**. It contains JRE + development tools.

They are platform dependent because configuration of each OS differs. But, Java is platform independent.

## Types of memory areas allocated by JVM

1. **Class Area** : Class Area stores per-class structures such as the runtime constant pool, field and method data, the code for methods.
2. **Heap** :  runtime data area in which objects are allocated.
3. **Stack** : Stack stores frames. It holds local variables and partial results, and plays a part in method invocation and return.
Each thread has a private JVM stack, created at the same time as thread.
A new frame is created each time a method is invoked. A frame is destroyed when its method invocation completes.
4. **Program Counter Register** : contains the address of the JVM instruction currently being executed.
5. **Native Method Stack** : contains all the native methods used in the application.

## Why main() method is static in java?

- main() method is entry point for any java program.
- JVM looks for public static void main(String[] args) method
- no compilation error
- but runtime error because JVM doesn't find the entry point in the program


## Is it possible to instantiate an Abstract class in Java?

* No, you cannot instantiate an abstract class in Java.
* When you create an instance of a class, its constructor is called and even though abstract class can have a constructor, the compiler will not allow you to create an instance of the class.
* It's a compile-time error to create an instance of an abstract class in Java :

        Exception in thread "main" java.lang.Error: Unresolved compilation problem: at tool.Hello.main(Hello.java:15)


## Sources

- https://www.javatpoint.com/corejava-interview-questions
- http://www.java67.com/