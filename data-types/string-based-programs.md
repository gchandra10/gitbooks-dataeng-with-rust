# String based programs

Assignment - Explain the logic behind these working examples.

For example, you need to explain why \&str2 ? why not str2.

what is the use of collect()

### Concatenation

```
// concatenation

fn main() {
  let str1 = "Hello".to_string();
  let str2 = " world".to_string();
  let string = str1 + &str2;
  println!("{}", string);
}
```

### String Reverse

```
// Reverse String

fn main() {
    let s = "Hello World";
    let t: String = s.chars().rev().collect();
    println!("{}", t);
}

```

### Check Palindrome

```
// Palindrome

fn main() {
    let s = "rotator";
    let t: String = s.chars().rev().collect();
    
    if s == t {
        println!("Palindrome")
    }
    else{
        println!("Not Palindrome")
    }
}
```

### String Padding

```
 // String Padding

fn main() {
    let s = "pizza";
    
    println!("{s:-^30}");
    println!("{s:*<30}");
    println!("{s:#>30}");
}
```
