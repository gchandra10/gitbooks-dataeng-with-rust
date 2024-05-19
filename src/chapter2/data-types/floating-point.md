# Floating Point

Floats are numbers with decimal points.

* `f32`: The **32-bit floating point** type.
* `f64`: The **64-bit floating point** type.

It doesn't support 16 or 128

```rust
 fn main() {
    //explicitly define a float type
    let f1:f32 = 32.9;
    let f2:f64 = 6789.89;
    let f3:fsize = 3.141414141414;
    println!("f1: {}", f1);
    println!("f2: {}", f2);
    println!("f3: {}", f3);
    
    //implicitly define a float type
    let pi = 3.14;
    let e = 2.17828;
    println!("pi: {}", pi);
    println!("e: {}", e);
}
```

Values are the same, but they are not equal.&#x20;

```rust
// Adding f32 + f64

fn main() {
    let my_float: f64 = 5.0; // This is an f64
    let my_float2: f32 = 5.0; // This is an f32

    let my_float3 = my_float + my_float2;️
    println!("{}",my_float3);
}
```

So how to fix it?

```rust
// Adding f32 + f64 the right way

fn main() {
    let my_float: f64 = 5.0; // This is an f64
    let my_float2: f32 = 5.0; // This is an f32

    let my_float3 = my_float + my_float2 as f64;
    println!("{}",my_float3);
}
```

**If not declared, the Default type is f64**

```rust
// What is size of my_other_float variable?
// Adding f32 with f64 will it work or fail?
// Rust is smart, 
// since it is doing addition with f32, it will default it to f32 instead of f64

fn main() {
    let my_float: f32 = 5.0;
    let my_other_float = 8.5; 

    let third_float = my_float + my_other_float;
}
```

