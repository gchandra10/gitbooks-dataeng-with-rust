# Comments

Line Comments //

Block Comments /\*  \*/

Doc Comments

Outer Doc Comments ///

Inner Doc Comments //!

```rust
// Writing a Rust program
fn main() {
    //The line comment is the recommended comment style
    println!("This is a line comment!"); // print hello World to the screen
}
```

```
/* Writing a Rust program */

/* comments can be /* nested */ too */

fn main() {
    println!("This is a line comment!");
}

```

Doc Comments are used to generate Documentation and they support markdown notations

```
/// This is a Doc comment outside the function
/// Generate docs for the following item.
/// This shows my code outside a module or a function
fn main() {
    //! This a doc comment that is inside the function   
    //! This comment shows my code inside a module or a function  
    //! Generate docs for the enclosing item
    println!("{} can support {} notation","Doc comment","markdown");
}
```

