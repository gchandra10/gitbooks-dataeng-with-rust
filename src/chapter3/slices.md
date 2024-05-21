# Slices

_Slices_ let you reference a contiguous sequence of elements in a collection rather than the whole collection. A slice is a kind of reference, so it does not have ownership.

A _string slice_ is a reference to part of a `String`, and it looks like this:

```rust
// String Slicing

fn main() {
    //define an array of size 4
    let arr:[i32;8] = [1, 2, 3, 4,5,6,7]; 
    
    //define the slice
    let slice_array1 = &arr;
    let slice_array2 = &arr[0..4];
    let slice_array3 = &arr[3..];
    
    // print the slice of an array
    println!("Value of slice_array1: {:?}", slice_array1);
    println!("Value of slice_array2: {:?}", slice_array2);
    println!("Value of slice_array3: {:?}", slice_array3);
}
```

### Example 2

```rust
fn first_word(s: &String) -> usize {
    let bytes = s.as_bytes();

    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return i;
        }
    }

    s.len()
}

fn main() {
    let s = String::from("hello world");
    let word = first_word(&s); // word will get the value 5
    println!("{}",word);
}
```

The string s is converted to bytes using the as_bytes() method for the purpose of iterating over individual bytes and finding the index of the first space character (b' ').

The reason for converting the string to bytes is that strings in Rust are encoded using UTF-8, which means that a single character (like 'é') can be represented by multiple bytes. If you were to iterate over the characters of the string directly, you might not get the correct index of the space character, especially if the string contains non-ASCII character.


```rust
// return value

fn first_word(s: &String) -> &str {
    let bytes = s.as_bytes();

    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &s[0..i];
        }
    }

    &s[..]
}

fn main() {
    let s = String::from("hello world");
    let word = first_word(&s); // word will get the value 5
    println!("{}",word);
}
```
