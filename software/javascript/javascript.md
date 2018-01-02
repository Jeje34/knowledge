# Javascript

## Comparison operators

### Equality operators

#### Equality (==)

The equality operator converts the operands if they are not of the same type, then applies strict comparison. If both operands are objects, then JavaScript compares internal references which are equal when operands refer to the same object in memory.

    1    ==  1         // true
    '1'  ==  1         // true
    0    == false      // true
    0    == null       // false
    var object1 = {'value': 'key'}, object2 = {'value': 'key'}; 
    object1 == object2 //false
    0    == undefined  // false
    null == undefined  // true


#### Strict equality / Identity (===)

The identity operator returns true if the operands are strictly equal with no type conversion. 

    3 === 3   // true
    3 === '3' // false
    var object1 = {'value': 'key'}, object2 = {'value': 'key'};
    object1 === object2 //false

### Sources

- [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators)

## Loop on an array
        
    for (sensor of sensors) {
        // ...
    }
   
## Inserts new elements at the start of an array
       
     var a = [1, 2, 3];
     a.unshift(4, 5);     
     console.log(a); // [4, 5, 1, 2, 3]
    
