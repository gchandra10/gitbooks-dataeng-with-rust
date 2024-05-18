# & and \*

```
& - Reference

* - Dereference
```

```
// & and *
```

```
// Reference and Dereference

fn main() {
    let a = 10;
    let b = &a;
    
    //Printing the value of a and memory reference of a
    
    println!("{} - {:p}",a, &a);
    
    // dereferencing b (10) and value of b (memory location of a)
    println!("{} - {:p}",*b, b);
    
    // dereferencing memory reference of a, referencing deference of b
    println!("{} - {:p}",*(&a), &(*b));
}
```



