# Enumerator



Here are some use cases:

1. **Index Tracking**: When you need to know the index of an element while iterating, `enumerate()` is handy.
2. **Conditional Logic**: Sometimes, the logic inside a loop might depend on the element's index. For example, you might want to skip the first element.
3. **Debugging**: When debugging, knowing the index of an element can help trace or log.
4. **Data Mapping**: When you need to create a new data structure that relies on the index and value from an existing iterable.

\
The enumerator turns an iterator over elements.

Using multiple conditions and variables, a loop condition can also be more complex. For example, the for loop can be tracked using enumerate.

```
fn main() {
    for (i, j) in (100..200).enumerate() {
        println!("loop has executed {} times. j = {}", i, j);
    }
}
```

```
// _ is a generic placeholder.

fn main()  
{ 
    let my_array: [i32; 7] = [1i32,3,5,7,9,11,13]; 
    let mut value = 0i32; 
    for(_, line) in my_array.iter().enumerate() 
    { 
       value += line; 
    } 
    println!("{}", value); 
} 
```

