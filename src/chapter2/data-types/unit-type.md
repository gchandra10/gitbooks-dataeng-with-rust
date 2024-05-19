# Unit Type

The () type, also called “unit”. The () type has exactly one value () , and is used when there is no other meaningful value that could be returned.

**The empty tuple type, () , is called “unit”, and serves as Rust's void type** (unlike void , () has exactly one value, also named () , which is zero-sized).

**Example 1**

```rust
fn main() {
    let my_tuple = (42, "hello", ());
    println!("Tuple: {:?}", my_tuple);
}

```

In this example, the tuple `my_tuple` contains an integer, a string, and a unit type `()`. When you run the code, it will print:

```
Tuple: (42, "hello", ())
```

**Example 2**

```rust
fn main() {
    let result = do_nothing();
    println!("Result of do_nothing: {:?}", result);
}

fn do_nothing() -> () {
    // This function does nothing and returns unit type
}
```
