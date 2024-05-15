# Generics

**Monomorphization** is a process where the compiler replaces generic placeholders with concrete datatypes.

Generics are a way to make a function or a type work for multiple types to avoid code duplication.

* Doesn't affect Runtime Performance.&#x20;
* Generics are a zero-cost abstraction.&#x20;
* Make Programming easier without reducing runtime performance.

```
// Some code

use std::fmt::Debug;
use std::fmt::Display;
use std::ops::*;

fn main() {
    //i32
    let n1: i32 = 10;
    let n2: i32 = 20;
    print_this(n1, n2);
    
    println!("Adding i32 ( {} + {} ) = {}", n1,n2, add_values(n1, n2));
    println!("Subtracting i32 ( {} from {} ) = {}", n1,n2,sub_values(n1, n2));
    println!("-----------------------------------");

    // F64
    let t1 = 23.45;
    let t2 = 34.56;
    print_this(t1, t2);

    println!("Adding f64 ( {} + {} ) = {}", t1,t2, add_values(t1, t2));
    println!("Subtracting f64 ( {} from {} ) = {}", t1,t2,sub_values(t1, t2));
    println!("-----------------------------------");

    // &str
    let r1 = "Rachel";
    let r2 = "Green";
    print_this(r1, r2);
    println!("----------------");

    // String Object
    let s1 = String::from("Rachel");
    let s2 = String::from("Green");
    print_this(s1, s2);
    println!("----------------");
    
    //printing diff datatypes
    
    print_another(t1,n1);

}


fn print_this<T: Debug + Display>(p1: T, p2: T) -> () {
    println!("Printing - {:?},{}", p1, p2)
}

fn add_values<T: Add<Output = T>>(p1: T, p2: T) -> T {
    // ://doc.rust-lang.org/std/ops/index.html
    p1 + p2
}

fn sub_values<T: Sub<Output = T>>(p1: T, p2: T) -> T {
    p1 - p2
}

fn print_another<T: Debug + Display, U:Debug + Display>(p1: T, p2: U) -> () {
    println!("Printing Diff Datatypes - {:?},{}", p1, p2)
}
```

### Generics with Struct

```
// Generics with Struct

struct Sample<T, U, V> {
    a: T,
    b: U,
    c: V
}

fn main() {
    let var1 = Sample{ a: 43.10, b: 2, c:"Hello" };
    println!("A: {}", var1.a);
    println!("B: {}", var1.b);
    println!("C: {}", var1.c);

    println!("----------------");

    let var2 = Sample{ a: "Hello", b: "World", c:34.6 };
    println!("A: {}", var2.a);
    println!("B: {}", var2.b);
    println!("C: {}", var2.c);
}


```

