# Iterations a.k.a Loops

There are 3 types of loops in Rust

## While Loop

Loops as long as the condition is True, exit when the condition if False.

```rust
fn main() {
    let mut i = 0;
    while i != 6 {
        i += 1;
        println!("inside loop value of i : {i}")
    }
    println!("finally i is {}", i);
}
```

## For Loop

```rust
// Left side Inclusive, Right side exclusive

fn main() {
    for x in 0..5 {
        println!("{}", x);
    }

// By adding =, both sides are inclusive

    for x in 0..=5 {
        println!("{}", x);
    }
}
```

## Loop

```rust
fn main() {
    let mut x = 0;
    loop {
        x += 1;
        if x == 5 {
            break;
        }
    }
    println!("{}", x);
}
```

```rust
// Break with message

fn main() {
    let mut x = 0;
    let v = loop {
        x += 1;
        if x == 5 {
            break "found the 5";
        }
    };
    println!("from loop: {}", v);
}
```
