# Java Building Blocks

## Java Class Structure

### Comments

- Javadoc comment starts with /**

### Classes vs Files
- Si un fichier contient plusieurs classes, seulement une seule peut-etre publique
- If you do have a public class, it needs to match the filename
- Par défault, une classe est "Package Private" : Can only be seen and used by the package in which it was declared
- Protected : Package Private + can be seen by subclasses in differents packages.

## Writing a main() méthod

- main() méthod is the gateway between the startup of Java process (managed bu the JVM) and the begenning of the code.
- JVM calls on the underlying system to allocate memory and CPU time, access files...
<br>

      public class Zoo {
         public static void main (String[] args) { // or String args[] or String... args
           ...
         }
      }
- to compile :

      javac Zoo.java
The result is a file of bytecode (Zoo.class). Bytecode consists of instructions that the JVM knows how to execute

- to execute :

        java Zoo // without arguments
        java Zoo Bronx Zoo // with two arguments
        java Zoo "San Diego" Zoo // with space inside an argument

## Package declarations and imports

- Use wildcards doesn't slow down the program : the compiler figures out what is actually needs
- Package **java.lang** is automatically imported
- Wildcard only matches class names, no good :
    - import java.nio.*;
    - import java.nio.files.Paths.*;
- When a class is found in multiple package, Java gives you a compilation error :

        import java.util.*;
        import java.sql.*; // NOT COMPILE : "The type date is ambiguous"


  You need to explicitly import a class name, it takes precedence over any wildcards :

        import java.util.Date;
        import java.sql.*;

  With ties for precedence :

        import java.util.Date;
        import java.sql.Date; // NOT COMPILE : The import collides with another import statement

- If you need use 2 classes with the same name :
    - pick one to use in the import and use the other's fully qualified class name
    - user the fully qualified class name for both

- Compiling code with packages
    - To compile : javac packagea/ClassA.java packageb/ClassB.java
    - To run : java packageb.ClassB (ClassB contains main() method)
    - Class paths and JAR
        - Windows : java -cp ".;C:\temp\someOtherLocation\;c:\temp\myJar.jar" myPackage.MyClass
        - Linux / Mac OS : java -cp ".:/tmp/someOtherLocation:/tmp/myJar.jar" myPackage.MyClass
        - dot (.) indicates you want includes the current directory in class path
        - The rest says to look in "someOtherLocation" folder and within myJar.jar
        - You can use wildcar to match all the JARs in a directory (won't include JARs that are in subdirectory) : java -cp "C:\temp\directoryWithJars\*" myPackage.MyClass



