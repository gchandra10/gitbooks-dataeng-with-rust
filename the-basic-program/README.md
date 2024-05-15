# The Basic Program

Rust code is always put in a file with `.rs` extension

{% code overflow="wrap" lineNumbers="true" %}
```rust
fn main() {
    println!("Hello World!");
}

```
{% endcode %}

![Images Source: https://www.educative.io](../.gitbook/assets/01\_fn\_main.png)

![Image Source: https://www.educative.io](../.gitbook/assets/01\_print\_macro.png)

![Image Source: https://www.educative.io](../.gitbook/assets/01\_macro\_explanation.png)



**Basic Formatting**

![Image Source: https://www.educative.io](../.gitbook/assets/01\_print\_formatting.png)



In Rust, unlike other languages, we cannot directly print numbers or variables within the \
&#x20;macro. We need a placeholder  trait`{}`.

In Rust, a trait is a way to define a set of methods that can be implemented on different types.

**Positional Arguments**

```
fn main() {
    println!("Number: {}", 1);
}
```

```
fn main() {
    println!("{} last name is {} ", "Rachel", "Green");
}
```

**Named Arguments**

```
fn main() {
    println!("{fname} last name is {lname} ", lname="Green", fname="Rachel");
}
```

**Basic Math**

```
fn main() {
    println!("{} * {} = {}",15, 15, 15 * 15);
}
```

A trait in Rust is **a group of methods that are defined for a particular type.**

**Printing formatters**

```
fn main() {
    println!("Number : 20 \nBinary:{:b} Hexadecimal:{:x} Octal:{:o}", 20, 20, 20);
}
```

**Debug Trait {:?}**

In Rust, the `Debug` trait is a built-in trait that allows types to be formatted for debugging purposes. It is primarily used by the `println!` and related macros to print a text representation of a value when used with the `{:?}` formatter.

```
fn main() {
    println!("{:?}", (100, "Rachel Green"));
}
```

**Printing Styles**

![Source: http://www.educative.io](../.gitbook/assets/01\_printing\_styles.png)

