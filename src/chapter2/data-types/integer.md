# Integer

**Fixed Size Integers**

* `i8`: The **8-bit signed** integer type.
* `i16`: The **16-bit signed** integer type.
* `i32`: The **32-bit signed** integer type.
* `i64`: The **64-bit signed** integer type.
* `u8`: The **8-bit unsigned** integer type.
* `u16`: The **16-bit unsigned** integer type.
* `u32`: The **32-bit unsigned** integer type.
* `u64`: The **64-bit unsigned** integer type.

**Variable Size Integers**

The integer type in which the particular size depends on the underlying machine architecture.

* `isize`: The **pointer-sized signed** integer type.
* `usize`: The **pointer-sized unsigned** integer type.

```rust
// see the smallest and biggest numbers,you can use MIN and MAX 
// after the name of the type

fn main() {
    println!("The smallest i8 is {} and the biggest i8 is {}.", i8::MIN, i8::MAX); // hint: printing std::i8::MIN means "print MIN inside of the i8 section in the standard library"
    println!("The smallest u8 is {} and the biggest u8 is {}.", u8::MIN, u8::MAX);
    println!("The smallest i16 is {} and the biggest i16 is {}.", i16::MIN, i16::MAX);
    println!("The smallest u16 is {} and the biggest u16 is {}.", u16::MIN, u16::MAX);
    println!("The smallest i32 is {} and the biggest i32 is {}.", i32::MIN, i32::MAX);
    println!("The smallest u32 is {} and the biggest u32 is {}.", u32::MIN, u32::MAX);
    println!("The smallest i64 is {} and the biggest i64 is {}.", i64::MIN, i64::MAX);
    println!("The smallest u64 is {} and the biggest u64 is {}.", u64::MIN, u64::MAX);
    println!("The smallest i128 is {} and the biggest i128 is {}.", i128::MIN, i128::MAX);
    println!("The smallest u128 is {} and the biggest u128 is {}.", u128::MIN, u128::MAX);

}
```

## Explicit Declaration

```rust
fn main() {
    //explicitly define an integer
    let a:i32 = 24;
    let b:u64 = 23;
    let c:u8 = 26;
    let d:i8 = 29;
    //print the values
    println!("a: {}", a);
    println!("b: {}", b);
    println!("c: {}", c);
    println!("d: {}", d);
    
}
```

## Alternate Way to Declare

```rust
// Alternate Way

fn main() {
    let small_number: u8 = 10;
    let small_number1 = 10u8; // 10u8 = 10 of type u8 (no space inbetween 10 and u8)
    let big_number = 100000000i32;
    let big_number1 = 100_000_000i32; // adds clarity to numbers
     let big_number2 = 100_____000________000i32;  //to demonstrate multiple ___
}
```

## Type Inference

```rust
fn main() {
    //implicitly define an integer
    let a = 21; 
    let b = 1;
    let c = 54;
    let d = 343434;
    //print the variable
    println!("a: {}", a);
    println!("b: {}", b);
    println!("c: {}", c);
    println!("d: {}", d);
    
}
```

**When not declared, the Default integer type inferred by Rust is i32**

```rust
// 
fn print_type_of<T>(_: &T) {
    println!("{}", std::any::type_name::<T>())
}

fn main() {
    let a = 5;
    let b = 3.14;
    print_type_of(&a);
    print_type_of(&b);
}    
```
