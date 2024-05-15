# Input from user

```
// Input String

use std::io;

fn main(){
    println!("Please enter your name: ");

    let mut name = String::new();
    io::stdin().read_line(&mut name).expect("Failed");

    println!("Welcome {}",name);
}

```

Expect (): Is used when the program panics.



```
// Accept two numbers

use std::io;

fn main(){
    println!("Enter First Number: ");

    let mut s1 = String::new();
    io::stdin().read_line(&mut s1).expect("Not a valid input");
    let n1:u32 = s1.trim().parse().expect("Not a valid Number");

    
    println!("Enter Second Number: ");
    let mut s2 = String::new();
    io::stdin().read_line(&mut s2).expect("Not a valid input");
    let n2:u32 = s2.trim().parse().expect("Not a valid Number");


    let result = n1 + n2;

    println!("Result : {result}");
}

```
