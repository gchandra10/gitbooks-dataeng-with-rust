# Constants

Constant variables are ones that are declared constant throughout the program scope, meaning, their value cannot be modified. They can be defined in the global and local scope.

All letters should be UPPER CASE and words separated by underscore (\_)

**Example:**

ID\_1

ID\_2

```
const ID_1: i32 = 4; // define a global constant variable

fn main() {
    const ID_2: u32 = 3; // define a local constant variable
    println!("ID:{}", ID_1); // print the global constant variable
    println!("ID:{}", ID_2); // print the local constant variable
}
```

How is it different from let immutable variables

| Const                                                | Immutable Let                            |
| ---------------------------------------------------- | ---------------------------------------- |
| declared using const                                 | declaured using let                      |
| mandatory to define the data type                    | data type declaration is optional        |
| The Value of const is set before running the program | Variable can store the result at runtime |
| Const cannot be shadowed                             | let can be shadowed                      |
|                                                      |                                          |

