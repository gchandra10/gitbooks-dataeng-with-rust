# Borrowing References

### Borrowing Immutable References

There are few rules when it comes to borrowing. Let's take a quick look at them.

```rust
// Cannot change as it's not a mutable reference

fn changeme(param_msg: &String) {
    param_msg.push_str(" Green")
}

fn main() {
    let msg = String::from("Rachel");
    changeme(&msg);
}

```

**Example**: Borrow a book from the library; you cannot write anything. Just read from it.

### Borrowing Mutable References

```rust
// Mutable reference

fn changeme(param_msg: &mut String) {
    param_msg.push_str(" Green")
}

fn main() {
    let mut msg = String::from("Rachel");
    changeme(&mut msg);
    println!("{}", msg);
}
```

**Example**: Borrow a book from a friend with permission to highlight or underline important items.



### Immutable and Mutable Borrow

```rust
// Immutable Borrow - Stack

fn main() {
    let x = 5;
    
    // Immutable borrow
    let y = &x;
    // *y += 1;
    println!("Value of y: {}", y);
   

}

```

**Immutable Borrow**: Allows read-only access to a value. Multiple immutable borrows can coexist, but they cannot coexist with a mutable borrow.

```rust
// Mutable Borrow - Stack

fn main() {
    let mut x = 5;
    println!("Value of x: {}", x);
    
    // Mutable borrow
    let z = &mut x;
    *z += 1;
    println!("Value of x: {}", x);
}
```

**Mutable Borrow**: Grants read-write access to a value. Only one mutable borrow is allowed at a time, and no immutable borrows can coexist.

***

**Immutable and Mutable Borrow**

**Rule**: Immutable borrow should always be **used** in the code after the mutable borrow because whatever modifications are done by mutable borrow should not affect immutable borrow.&#x20;

That’s why they always use immutable borrows after mutable borrows.

```rust
fn main() {
    let mut x = 5;
    
    // Mutable borrow
    let z = &mut x;
    *z += 1;
    
    println!("Value of z: {}->{:p}", z, &z);
    
    println!("Value of x: {}->{:p}", x, &x);
    
    // immutable borrows
    let y1 = &x;
    println!("Value of y1: {}->{:p}", y1, &y1);
    
    // Flip the immutable and mutable and print the Immutable value after Mutable
  
}
```

Use this website to sort the Memory locations to understand how values are stored in Stack. You can sort them by ASC or DESC order.

[https://www.rajeshvu.com/storage/emc/utils/general/sorthexnumbers](https://www.rajeshvu.com/storage/emc/utils/general/sorthexnumbers)

**Borrow Checker**

Exactly. When `b` has a mutable borrow of `a`, `a` temporarily loses its write privilege. You can't modify `a` or even read from it while `b` has an active mutable borrow. Rust's **borrow checker** enforces this to ensure memory safety.

If you try to access **`a`** while **`b`** has an active mutable borrow, Rust's borrow checker will complain. This ensures you don't have multiple mutable references to the same data, which could lead to **data races** and undefined behavior. The borrow checker enforces these rules at compile time for memory safety.

```rust
// Borrow Checker - String - Heap

fn main() {
    let mut a = String::from("Rachel");
    
    let b = &mut a;
    
    println!("variable 'b' initial value is {} stored at this {:p}", b,b.as_ptr());
    
    b.push_str(" Green");
    
    //println!("variable 'a' {}{:p}", a,a.as_ptr());
    
    println!("variable 'b' {} {:p}", b,b.as_ptr());
    
    // println!("variable 'a' {}{:p}", a,a.as_ptr());
    
    b.push_str(" !");
    
    println!("variable 'b' after update {},{:p}", b,b.as_ptr());
    
    println!("variable 'a' after update {} {:p}", a,a.as_ptr());
}
```

**Example**: The book owner can use the book only after the borrowed person has completed the work.

### Multiple Mutable Borrowers

```rust
// Not allowed to have multiple Mutable Borrowers at the same time/scope

fn main() {
    let mut a = String::from("Rachel");
    
    let b = &mut a;
    let c = &mut a;
    
    println!("{}", b);
    println!("{}", c);
   
}
```

**Example**: Two friends borrow the same book to highlight the important items.



```rust
// Multiple Mutable Borrowers (different scope)

fn main() {
    let mut a = String::from("Rachel");
   
    let b = &mut a;
    println!("{}", b);

    let c = &mut a;
    println!("{}", c);
}
```

**Example**: 2 friends borrow the book one after another for writing.



For clarity's sake, the above code can be written this way, too.

```rust
// Multiple Mutable Borrowers (different scope)

fn main() {
    let mut a = String::from("Rachel");

    {    
       let b = &mut a;
        println!("{}", b);
    }

    let c = &mut a;
    println!("{}", c);
}
```

### Immutable and Mutable

Mutable  first, followed by Immutable

```rust
// Immutable and Mutable

fn main() {
    let mut a = String::from("Rachel");
    
    let c = &mut a;
    c.push_str("!");
    println!("c = {}", c);
    
    let b = &a;
    println!("b = {}", b);

```

**Rules**:

1. Multiple Immutable references are allowed in the same scope.
2. Immutable and Mutable references are not allowed in the same scope.
3. Immutable and Mutable references are allowed in different scopes.
