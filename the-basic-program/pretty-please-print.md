# Pretty Please - Print

```
// Print

fn main() {
    let doesnt_print = ();
    println!("This will not print: {}", doesnt_print); // ⚠️
}
```

Pretty Print

```
// Pretty Print

fn main() {
    let doesnt_print = ();
    println!("This will not print: {:#?}", doesnt_print); // ⚠️
}
```

What is the output of this?

```
// Print Space

fn main() {
    let doesnt_print = ' ';
    println!("This will not print: {}", doesnt_print); // ⚠️
}

```

```
// Pretty Print Space

fn main() {
    let doesnt_print = ' ';
    println!("This will not print: {:#?}", doesnt_print); // ⚠️
}
```
