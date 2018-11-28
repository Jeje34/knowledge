# Overloading

## Definition

**Overloading** is a feature that allows a class to have more than one method having the same name, if their return type are the same and their argument lists are different 

### Examples valid overloading

    public void do(int i) throws AirithmeticException;
    public void do(long j)
    public int do(double j)
    private int do(String j)
    private void do()throws Exception;
<!-->
    doX(int i, long j)
    doX(long j, int i)

## Rules

1. Primitive widening uses the "smallest" method argument possible.
2. Used individually, boxing and var-args are compatible with overloading.
3. You can't widen from one wrapper type to another.
4. You can't widen and then box. (An int can't become a Long)
5. You can box and then widen. (An int can become an Object, via Integer.)
6. You can combine var-args with either widening or boxing.

### Examples

    doX(Integer i);
    doX(int i);
Calling **doX(2)**, **doX(int i)** will be called because overloading give always priority in primitive types.
<br/><br/>

    doX(Integer i);
    doX(int ... i);
Calling **doX(2)**, **doX(Integer i)** will be called because boxing has precedence over varargs.
<br/><br/>

    doX(Integer i);
    doX(long i);
Calling **doX(2)**, **doX(long i)** will be called because primitive widening has precedence over boxing.
<br/><br/>

    doX(Object i);
    doX(Long i);
Calling **doX(2)**, **do(Object i)** will be called because in overloading, boxing then widening is permissible (conversion is int->Integer->Object) but widening then boxing (int->long->Long) is not allowed




## Sources

* http://javaonfly.blogspot.fr/2015/11/overloading-in-java.html