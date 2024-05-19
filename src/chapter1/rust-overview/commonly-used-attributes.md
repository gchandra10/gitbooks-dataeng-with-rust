# Commonly Used Attributes

In Rust, attributes provide metadata about the code to the compiler. Some commonly used attributes include:

#[derive(...)]:
Automatically implements standard traits for a struct or enum.

```
#[derive(Debug, Clone, PartialEq)]
struct Point {
    x: i32,
    y: i32,
}
```

#[cfg(...)]:
Compiles code conditionally based on specified configuration options.

```
#[cfg(test)]
mod tests {
    #[test]
    fn it_works() {
        assert_eq!(2 + 2, 4);
    }
}
```

#[test]:
Marks a function as a test function to be run by the test harness.

```
#[test]
fn test_addition() {
    assert_eq!(2 + 2, 4);
}
```

#[allow(...)] and #[deny(...)]:
Controls compiler warnings and errors.

```
#[allow(dead_code)]
fn unused_function() {
    // This function is not used
}

#[deny(missing_docs)]
fn another_function() {
    // This will cause a compilation error if there are no docs
}
```

#[inline] and #[inline(always)]:
Suggests to the compiler to inline the function.

```
#[inline]
fn add(a: i32, b: i32) -> i32 {
    a + b
}

#[inline(always)]
fn multiply(a: i32, b: i32) -> i32 {
    a * b
}
```

#[macro_use]:
Imports macros from an external crate.

```
#[macro_use]
extern crate serde_derive;

#[derive(Serialize, Deserialize)]
struct MyStruct {
    field: String,
}
```


#[non_exhaustive]:
Prevents exhaustive matching on enums, making it easier to add variants in the future.

```
#[non_exhaustive]
enum MyEnum {
    Variant1,
    Variant2,
}
```


Don't worry if these things don't make sense; we will learn all these things in the coming weeks.
