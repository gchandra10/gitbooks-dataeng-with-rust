# RHAI

Rhai is an embedded scripting language for Rust that allows you to extend your Rust applications with scripting capabilities.

It is highly extensible and safe, making it suitable for various applications where scripting capabilities are desired.

[RHAI Playground](https://rhai.rs/playground/stable/)

[RHAI Scripts](https://github.com/rhaiscript/rhai/tree/main/examples)

[RHAI Book](https://rhai.rs/book/about/features.html)

Demo to see capability of RHAI before learning the use cases.

Examples:

```
git clone https://github.com/gchandra10/rust-rhai-demo.git
```

## How Rhai Works

Rhai scripts are written in a simple, easy-to-learn syntax. When you execute a Rhai script, it goes through several stages:

**Parsing**: The script is parsed into an Abstract Syntax Tree (AST).
When this script is parsed by Rhai, it gets converted into an AST. The AST is a tree-like structure that represents the syntactic structure of the script.

**Compilation**: The AST is compiled into an internal representation.

**Execution**: The compiled script is executed by the Rhai engine.

Check AST in Rhai Playground

```
let x = 5;
let y = x * 2;
print(y);
```

## Why Use Rhai?

**Ease of Embedding**: Rhai is designed to be easily embedded within Rust applications, providing a simple API for integration.

**Safety**: Rhai ensures safety through Rust's ownership and borrowing principles, making it a reliable choice for applications where security is critical.

**Extensibility**: Rhai allows you to extend its functionality with Rust code, enabling you to create custom functions and integrate seamlessly with existing Rust libraries.

**Performance**: Although it is an interpreted language, Rhai is designed to be fast and efficient, suitable for performance-critical applications.

**Simplicity**: The syntax of Rhai is straightforward and easy to learn, making it accessible to both developers and end-users who need to write scripts.

**Concurrency**: Rhai supports concurrency, which can be beneficial for applications that require multitasking or parallel execution.

**Dynamic Typing**: Rhai is dynamically typed, allowing for flexible and expressive scripting without the need for explicit type declarations.

## Use Cases

**Game Development**: Embedding Rhai to script game logic, AI behavior, or user interfaces.

**Configuration**: Allowing users to define configuration scripts that can modify the behavior of an application at runtime.

**Automation**: Providing a scripting interface for automating tasks or extending the functionality of an application.

**Prototyping**: Quickly testing and iterating on new features without recompiling the entire Rust application.

## Why not use RHAI

Its not as fast native Rust.

Doesn't support Classes/Traits/Closures/Tuples


