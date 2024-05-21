# Enumerate()

In an given Array, how to print the index and value?

```rust
fn main() {
    let fruits = ["apple", "banana", "cherry"];

    for i in 0..fruits.len() {
        println!("Index: {}, Fruit: {}", i, fruits[i]);
    }
}
```

Instead of handling i and index positions manually, Rust offers an easier technique using **Enumerate()**.

Like iter() enumerate() is also a part of Functional programming.

In Rust, enumerate() is a method provided by the standard library that is used to iterate over an iterator (like a array, or any other data structure that implements the IntoIterator trait) and get both the index and the value at that index in each iteration.

Here are some use cases:

1. **Index Tracking**: When you need to know the index of an element while iterating, `enumerate()` is handy.
2. **Conditional Logic**: Sometimes, the logic inside a loop might depend on the element's index. For example, you might want to skip the first element.
3. **Debugging**: When debugging, knowing the index of an element can help trace or log.
4. **Data Mapping**: When you need to create a new data structure that relies on the index and value from an existing iterable.

The enumerator turns an iterator over elements.

```rust
fn main() {
    let fruits = ["apple", "banana", "cherry"];

    for (index, fruit) in fruits.iter().enumerate() {
        println!("Index: {}, Fruit: {}", index, fruit);
    }
}
```

Using multiple conditions and variables, a loop condition can also be more complex. For example, the for loop can be tracked using enumerate.

```rust
fn main() {
    for (i, j) in (100..120).enumerate() {
        println!("loop has executed {} times. j = {}", i, j);
    }
}
```

## Ignoring Index position with an _

```rust
// _ is a generic placeholder.

fn main()  
{ 
    let my_array: [i32; 7] = [1i32,3,5,7,9,11,13]; 
    let mut value = 0i32; 
    for(_, item) in my_array.iter().enumerate() 
    { 
       value += item; 
    } 
    println!("{}", value); 
} 
```

