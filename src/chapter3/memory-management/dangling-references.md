# Dangling References

A dangling reference occurs when you have a reference that points to an invalid memory location, usually because the data it refers to has been deallocated or moved. In languages like C and C++, this can lead to undefined behavior.

**Rust's ownership model is designed to eliminate this issue**. The borrow checker ensures that references cannot outlive the data they point to, making dangling references impossible in safe Rust code.

```rust
// Dangling Reference

fn main() {
    let r;
    {
        let x = 42;
        r = &x;
    }
    println!("r: {}", r);  // This won't compile
}
```



```rust
// Dangling Reference

fn get_name() -> &String{
    let name = String::from("Rachel");
    &name
}

fn main() {
    let name:String = get_name();
    println!("new name is {name}");
}
```

The above code results in an error.

```
this function's return type contains a borrowed value, but there is no value for it to be borrowed from
help: consider using the `'static` lifetime
```

The function get\_name returns a reference variable **\&name**;

After the function is done, the variable goes out of scope, leading to a NULL Pointer reference.

This is allowed in other languages like C++, leading to memory issues.

**How to solve it?**

Remove the & from the **return value and get_name()** definition and return the variable.

```rust
fn get_name() -> String{
    let name = String::from("Rachel");
    name
}

fn main() {
    let name:String = get_name();
    println!("new name is {name}");
}
```
