# Simple Rust Programs

### Using Variables

```rust
fn main() {
    let name = "Rachel";
    let age=30;
    println!("Hello {},{}", name,age);

    //change the value of variable
    
    let name = "Rachel Green";
    println!("Hello {},{}", name,age);

}
```

### Using Multiple Variables

```rust
#[allow(unused_variables, unused_mut)]

fn main() {
    let (fname,lname,mi) =("Rachel","Green",""); // assign multiple values
    println!(" Student Name is {} {}.", fname,lname); // print the value
}
```

### FOR Loops

```rust
// non inclusive on right side

fn main() {
    for i in 0..5 {
        println!("Hello {}", i);
    }
}
```

### ODD / EVEN

```rust
fn main() {
    for i in 0..5 {
        if i % 2 == 0 {
            println!("even {}", i);
        } else {
            println!("odd {}", i);
        }
    }
}
```

#### Alternate Method

```rust
// Expression assigned as Value

fn main() {
    for i in 0..5 {
        let even_odd = if i % 2 == 0 {"even"} else {"odd"};
        println!("{} {}", even_odd, i);
    }
}
```
