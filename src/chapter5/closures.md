# Closures

**Rust closures are anonymous functions** without any name that you can save in a variable or pass as arguments to other functions.

Also called headless functions.

\| | represents its a Closure.

```rust
// Simple Closure Example

fn main() {
    let example = |num| -> i32 { num + 1 };
    println!("{}", example(5));
}
```

### Function vs. Closure

```rust
// Function vs Closure

fn add_one_fn(x: i32) -> i32 {
    1 + x
}
```

```rust
fn main() {
    //let y = 6;
    let add_one_cl = |x: i32| -> i32 { 1 + x};
    println!("Closure : {}", add_one_cl(3));
    println!("Function : {}", add_one_fn(3));
}

```

Unlike functions, closures can capture values from the scope in which they're called.

One more example

```rust
// Closure returns a value

fn main() {
    let s = String::from("Hello");

    let closure = |name: String| -> String {
        format!("{}, {}!", s, name)
    };

    let result = closure(String::from("Rachel"));
    println!("The result is: {}", result);
}
```

```rust
// Mutable Values inside Closure

fn main() {
    let plus_two = |x| {
        let mut result: i32 = x;

        result += 1;
        result += 1;

        result
    };

    println!("{}", plus_two(2));
}

```

## Use Cases

* Creating functions that can be passed around and used in different parts of your code without explicitly defining the function in every place you want to use it.
  
* This can make your code more modular and easier to understand.

* Capturing variables from the environment and using them in the closure's code.

* This allows you to create functions that can access and use values from the scope in which they are defined, even after the code that defined the closure has finished executing.

* Implementing complex behavior for a type without creating a new struct or type. For example, you can use a closure to define the behavior of a trait object, which allows you to define complex behavior without creating a new type to represent that behavior.

* Creating a  higher-order function takes other functions as arguments and  return other functions as results.

Overall, closures are a very useful tool in Rust, and they can be used to solve a wide range of problems in your code.

