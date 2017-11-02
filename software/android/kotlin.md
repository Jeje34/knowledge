# Kotlin

- Kotlin is a programming language that can be used for developing Android Apps
- server side code and instead of JavaScript in web clients
- 100% interoperable with Java or Android (you can use both Java and Kotlin together to develop an Android app)

##  Kotlin better than Java ?

### Null Safety

    var a: String = "Hello"
    a = null                 // Compilation error - since a cannot be null
    var b: String? = "Hello" // ? indicates that var can hold null value
    b = null                 // Somewhere in your code, b is set to null
    val len = b.length       // Compilation error - since b can be null
    val len = b?.length      // Will never throw NPE. returns null instead
    
### Lambda expressions

A lambda expression is a function that is not declared, but passed immediately as an expression.

    Boolean compare(String a, String b) {
       return (a.length < b.length)
    }
    max(strings, compare(a,b))
    
    //Replace it by a Lambda function
    max(strings, { a, b -> a.length < b.length })
    
### Extension functions and properties

You can easily extend a class with new functionality without having to inherit from the class. The functions or properties are accessed statically.

    fun Int.square(): Int {  
        return this * this
     }
    val a:Int = 2
    var b:Int = a.square()
    
## Sources

- https://medium.com/maverick-labs/should-i-learn-kotlin-d3a30604d496