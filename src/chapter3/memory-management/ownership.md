# Ownership

### Ownership

It's a unique & critical aspect of Rust.

**In C/C++ there is no concept called a Garbage Collector. (which frees up the unused memory).**

* But they are very fast and performant.
* Developers need to work to free up memory. (remember free() function?)

**In other languages such as Python, Java, and Go we have Garbage Collector**

* Relatively slower
* Developers can focus only on business logic.

### Rust Ownership System

* Best of both worlds.
* The Compiler replaces most of GC's responsibilities.
* Determines at compile time when memory is allocated and deallocated.
* Requires developers to code in specific ways. (All the checks and balances)

### Rules of Ownership

* Each value in Rust has a variable that is called its Owner.
* There can only be one owner at a time.
* When the owner goes out of scope, the value will be dropped.

_{:p} - Pointer Trait, used to print the memory location of variables._

```
// Demonstrate Shadowing

fn main() {
    let x = String::from("Rachel");
    println!("Memory address of x: {:p}", &x);
    
    // new x is created in another memory location
    let x = 5;
    println!("Memory address of x: {:p}", &x);
}
```

