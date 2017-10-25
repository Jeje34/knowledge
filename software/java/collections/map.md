# Map

![](http://codepumpkin.com/wp-content/uploads/2017/09/ConcurrentHashMap.jpg)

## HashMap
 
- not thread-safe : if multiple threads are accessing the same HashMap object and try to modify the structure of the HashMap (using put() or remove() method), it may cause an inconsistency in the state of HashMap (instead use Hashtable, Collections.SynchronizedMap or ConcurrentHashMap).
- allows one null key and mutiple null values.
 
## Hashtable

- uses synchronized methods to achieve thread safety : at a time only one thread can read or write into Hashtable. 
- performance is quite slow
- does not allow null keys or values
 
## Collections.SynchronizedMap

- a static inner class of utility class java.util.Collections
- quite similar to Hashtable and it also acquires lock on entire Map instance
- provides functionality to convert any thread-unsafe Map implementation to thread-safe implementation using Collections.synchronizedMap(Map map) static method :
        
        Map<String,String> map = new HashMap<String,String>();
        Map<String,String> syncmap = Collections.synchronizedMap(map);
- wraps original Map object with synchronized block
- performance is quite slow
- allows one null key and multiple null values

## ConcurrentHashMap

- thread-safe
- more than one threads can read and write concurrently in ConcurrentHashMap (unlike Hashtable and SynchronizedMap)
- divides the Map instance into different segments. And each thread acquires lock on each segment. 
- fast performance
- doesn't allow null keys and null values.

## Sources

- http://codepumpkin.com/hashtable-vs-synchronizedmap-vs-concurrenthashmap/