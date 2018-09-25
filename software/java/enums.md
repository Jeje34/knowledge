# Enumerations in Java

- Declare enum constants with UPPERCASE letters
- Enum can have fields, constructors, and methods along with enum constants.
- Enum constructors are private by default. Only private constructors are allowed in enum types. That’s why you can’t instantiate enum types using a new operator.
- Enum constants are created only once for the whole execution. All enum constants are created when you initially refer any enum constant in your code. While creating each enum constant, the corresponding constructor is called.

        Enum constants must be declared before fields, constructors, and methods (if any).

        All enum types extend the java.lang.Enum class by default. As multiple inheritances are not supported in Java, they can’t extend to any other classes.

        Enum types can implement any number of interfaces.

        Enum constants can have their own body called Constant Specific Body. In that body, you can define fields and methods. But, these methods and fields are visible within the Constant Specific Body in which they were defined.

        Enum types are final by default. They cannot be extended by any other types.

        For every enum type written in a file, the .class file will be generated after compilation.

        Enum types can have any number of static initialization blocks as well as instance initialization blocks.

        Since the java.lang.Enum class implements theComparable  and Serializable  interface, all enum types are Comparable and Serializable by default.

        We can compare the enum constants using the  == operator.

        You can retrieve the enum constants of any enum type using the values() method. The values() method returns an array of enum constants.

        Enums provide type-safety during compilation. That means you will get a compile-time error if you try to assign any values other than the specified enum constants.

        You can define enum types outside a class or inside a class but not inside a method or block.

        The  ordinal() method is used to get the order of an enum constant in an enum type.

        Enums are mostly used when you want to allow a limited set of options that remain constant for the whole execution and you know all possible options at compile time. For example, this could be choices on a menu or options of a combobox.