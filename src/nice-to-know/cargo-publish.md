# Cargo Publish

Note: Once you publish a crate, there is no removal.

Visit [https://crates.io/](https://crates.io/)

Login with GitHub

Verify the email address

Goto Account > API Settings and Generate a new token.

```
// lib.rs

use std::fmt::Display;
use std::fmt::Debug;

/// Function hello accepts an argument and returns Hello <argument> !.
/// It accepts any scalar datatype (i,u,&str,String,bool) and returns a String object.
/// This is a simple implementation to demonstrate Generics Function.
/// 
pub fn hello<T:Display + Debug>(s: T) -> String {
    format!("Hello {} !", s.to_string() )
}


```

```
// Cargo.toml

[package]
name = "hello_lib"
version = "0.1.6"
edition = "2021"
authors = ["Ganesh Chandrasekaran"]
description = "Demonstrate Generics Function"
documentation = "https://docs.rs/hello_lib"
readme="README.md"
license = "MIT"
keywords = ["demo", "generics","functions"]
categories = ["text-processing"]
repository = "https://github.com/gchandra10/hello_lib/"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
```

Create README.md at the same level as src folder

````
// README.md

## Library for demonstration

## Usage

```
    // Cargo.toml

    [dependencies]
    hello_lib = "0.1.6"
```

```
    // main.rs

    use hello_lib::hello;

    fn main() {
        println!("{}", hello("Rachel"));
        println!("{}", hello(31));
        println!("{}", hello(3.14));
        println!("{}", hello(true));
        println!("{}", hello('G'));
    }

```
````

```
// Cargo Commands

cargo login <token>
cargo publish --dry-run
```

```
// git commands

git add Cargo.toml
git add README.md
git add src/lib.rs
git add .gitignore

git commit -m "Demo Crate"
```

```
// Publish

cargo publish
```
