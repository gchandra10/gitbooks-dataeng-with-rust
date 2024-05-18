# Escape Printing

Similar to other programming languages  \t and \n are used for Tab and Newlines

```rust
// \t \n

fn main() {
    print!("\t first line is tabbed \nand second line is on a new line");
}
```

### How to print \t and  \n?

```rust
// Escape Characters

fn main() {
    println!("Here are two escape characters: \\n and \\t");
}
```

### Print multiple escape characters

```rust
// Print multiple \\ , "

fn main() {
    println!("File \"folder location is at c:\\users\\ganesh\\Documents\\01.rs.\" ") 
}
```

Too many \\\ there is a good chance one might forget to \\\\, is there an easy way?

```rust
// r#  and  #  

fn main() {
    println!(r#"File "folder location is at c:\users\ganesh\Documents\01.rs." "#) 
}
```

If you need to print #, then use ##

```rust
// # & ##

fn main() {
    let hashtag_string = r##"The hashtag #IceToSeeYou had become very popular."##; // Has one # so we need at least ##
    let many_hashtags = r####""You don't have to type ### to use a hashtag. You can just use #.""####; // Has three ### so we need at least ####

    println!("{}\n{}\n", hashtag_string, many_hashtags);
}
```

### Alternate Use 
*Not a good programming practice to use keywords as variables*

```rust
// Using reserved words

fn main() {
    let let=4;
    println!("{}", let);
}
```

```rust
// r#

fn main() {
    let r#let=4;
    println!("{}", r#let);
}
```
