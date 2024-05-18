# Assert Macros

```
// Different assert macros

let result = add(2,2);

assert!(result == 4);
assert!(result == 4,"Expected 4; returned result is {}",result);

-----------

let result = add(2,2);

assert_eq!(result,4);

assert_eq!(result,4,"Expected 4; returned result is {}", result);

------------

Similar to the previous one, checks for NOT Equalto.
assert_ne!()

```
