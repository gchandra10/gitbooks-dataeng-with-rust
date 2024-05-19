# Unary Operators

Unary operators in Rust are operators that operate on a single operand. They perform various operations such as negation, dereferencing, and borrowing. Common unary operators in Rust include:

* - (Negation): Negates a numerical value.
* ! (Logical NOT): Inverts a boolean value.
* * (Dereference): Dereferences a pointer, allowing access to the value it points to.
* & (Borrow): Creates a reference to a value.
* &mut (Mutable Borrow): Creates a mutable reference to a value.

## Examples

### Negation (-):

```rust
fn main(){
    let x = 5;
    let y = -x;
    println!("y: {}", y);  // Output: y: -5
    }
```

### Logical NOT (!):

```rust
fn main(){
    let a = true;
    let b = !a;
    println!("b: {}", b);  // Output: b: false
}
```

### Dereference (*):

```rust
fn main(){
    let x = 10;
    let y = &x;
    let z = *y;
    println!("z: {}", z);  // Output: z: 10
}
```

### Borrow (&):

```rust
fn main(){
    let s = String::from("hello");
    let r = &s;
    println!("r: {}", r);  // Output: r: hello
}
```

### Mutable Borrow (&mut):

```rust
fn main(){
    let mut s = String::from("hello");
    {
        let r = &mut s;
        r.push_str(", world");
    }
    println!("s: {}", s);  // Output: s: hello, world
}
```