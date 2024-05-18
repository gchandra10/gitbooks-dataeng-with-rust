# Pretty Please - Print

```rust
// Print

fn main() {
    let doesnt_print = ();
    println!("This will not print: {}", doesnt_print); // ⚠️
}
```

Pretty Print

```rust
// Pretty Print

fn main() {
    let doesnt_print = ();
    println!("This will print: {:#?}", doesnt_print); // ⚠️
}
```

What is the output of this?

```rust
// Print Space

fn main() {
    let doesnt_print = ' ';
    println!("This will not print: {}", doesnt_print); // ⚠️
}

```

```rust
// Pretty Print Space

fn main() {
    let doesnt_print = ' ';
    println!("This will print: {:#?}", doesnt_print); // ⚠️
}
```
