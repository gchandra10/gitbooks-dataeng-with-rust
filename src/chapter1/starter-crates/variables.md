# Variables

A variable is like a **storage box** paired with an **associated name** which contains **data**. The associated name is the identifier and the data that goes inside the variable is the value. They are **immutable by default**, meaning, you cannot reassign value to them.

![Images Source: https://www.educative.io](../../assets/02\_variable.png)

To create a variable, use the `let` binding followed by the variable name

> **What is binding?**
>
>
>
> Rust refers to **declarations** as bindings as they bind a name at the time of creation. **`let`** is a kind of **declaration statement**.

> **Naming Convention:** By convention, you would write a variable name in a **snake\_case** i.e.,
>
>
>
> * All letters should be lower case.
> * All words should be separated using an underscore ( \_ )
>
>

### Initialize a variable

A variable can be initialized by assigning a value to it when it is declared. The value is said to be bound to that variable.

**Note:** It’s possible to declare the variable first and assign it a value later. However, it is not recommended to do this as it may lead to the use of uninitialized variables.

```rust
fn main() {
    let language = "Rust"; // define a variable
    println!("Language: {}", language); // print the variable
}
```

Note: it is not possible to directly print a variable within a `println!()`. You need a placeholder.

### How to create a Mutable Variable

```
let mut variable = "value"
```

```rust
fn main() {
    let mut language = "Rust"; // define a mutable variable
    println!("Language: {}", language); // print the variable
    language = "Java"; // update the variable
    println!("Language: {}", language); // print the updated value of variable
}
```

### Assigning Multiple Values

```
let (variable1,variable2) = ("value1", value2);
```

```rust
fn main() {
    let (fname,lname) =("Rachel","Green"); // assign multiple values
    println!(" Student Name is {} {}.", fname,lname); // print the value
}
```

If variables are unassigned or unused compiler will generate warning

```
#[allow(unused_variables, unused_mut)]
```

```rust
fn main() {
    let (fname,lname,mi) =("Rachel","Green",""); // assign multiple values
    println!(" Student Name is {} {}.", fname,lname); // print the value
}
```

### Variable Scope

The scope of a variable refers to the visibility of a variable, or, which parts of a program can access that variable.

It all depends on where this variable is being declared. If it is declared inside any curly braces **{}**, i.e., a block of code, its scope is restricted within the braces, otherwise the scope is global.

**Local Variable**

A variable that is within a block of code, `{ }`, that cannot be accessed outside that block is a local variable. After the closing curly brace, `}` , the variable is freed and memory for the variable is deallocated.

**Global Variable**

The variables that are declared outside any block of code and can be accessed within any subsequent blocks are known as global variables.

![Images Source: https://www.educative.io](../../assets/02\_variable\_scope.png)

```rust
fn main() {
  let outer_variable = 112;
  { // start of code block
        let inner_variable = 213;
        println!("block variable inner: {}", inner_variable);
        println!("block variable outer: {}", outer_variable);
  } // end of code block
    println!("inner variable: {}", inner_variable); // use of inner_variable outside scope
}

```

### How to fix this error?

```rust
fn main() {
  let outer_variable = 112;
  let inner_variable = 213;
  { // start of code block
        println!("block variable inner: {}", inner_variable);
        println!("block variable outer: {}", outer_variable);
  } // end of code block
    println!("inner variable: {}", inner_variable);
  }

```

### Shadowing

Variable shadowing is a technique in which a variable declared within a certain scope has the same name as a variable declared in an outer scope. This is also known as masking. This outer variable is shadowed by the inner variable, while the inner variable is said to mask the outer variable.

![Images Source: https://www.educative.io](../../assets/02\_variable\_shadowing.png)

```
fn main() {
  let outer_variable = 112;
  { // start of code block
        let inner_variable = 213;
        println!("block variable: {}", inner_variable);
        let outer_variable = 117;
        println!("block variable outer: {}", outer_variable);
  } // end of code block
    println!("outer variable: {}", outer_variable);
  }
```

### Another - Variable reused in same scope

```rust
// Shadowing

fn main() {
   let spaces = "Testing";
   println!("{:?}",spaces);
   let spaces = spaces.len();
   println!("{:?}",spaces);
}
```
