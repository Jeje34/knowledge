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

## Can you make a class Static in Java?

* cannot make a top level class static in Java, compile time error :
    
        "Illegal modifier for the class Top; only public, abstract & final are permitted

* can make a nested class static in Java (good practice) then you can directly create an instance of nested class without first creating an object of enclosing class.
                                              
        class Top {
            static class Nested {
                ...
            }
        }
         
        Top.Nested n = new Top.Nested();
  
## Differences between StringBuffer, StringBuilder and String

* StringBuffer and StringBuilder are mutable, but String is immutable : you can add, remove or replace characters from StringBuffer and StringBuilder objects but any change on String will always result in a new String object. 

* StringBuffer and StringBuilder represent mutable String

* If you need to manipulate String data then wrap it inside a StringBuffer or StringBuilder to avoid creating lots of small and temporary String objects and putting pressure on Garbage collector
 
* StringBuffer and String are thread-safe but StringBuilder is not thread-safe. String achieves its thread-safety from Immutability but StringBuffer achieves it by synchronizing methods which change the state (append(), delete()...)

* StringBuilder = StringBuffer without synchronized keyword, but StringBuilder is much faster than StringBuffer
  
* Use String if you need text data which is relatively constant 
  
* Use StringBuilder if are doing lots of String concatenation
 
## Can you make an abstract class/method final in Java?

- No, cannot make an abstract class or method final in Java
- Abstract and final are exclusive concepts :
    - Abstract class is incomplete and can only be instantiated by extending a concrete class and implementing all abstract methods
    - Final class is considered as complete and cannot be extended further
    - Abstract method must be overridden to be useful and called
    - Final method cannot be overridden in Java
- Compilation error :

        The class XXX can be either abstract or final, not both
        
## Is it possible to have an abstract method in a final class?

No, because as soon as you declare an abstract method in a class, the class automatically becomes an abstract class and you cannot make an abstract class final in Java (see above)

## Can an abstract class have static methods in Java?
   
Yes, because you don't need to instantiate a class to use the static method, you can just call them by using the class name
    

## Sources

- https://www.javatpoint.com/corejava-interview-questions
- http://www.java67.com/
- http://javarevisited.blogspot.fr