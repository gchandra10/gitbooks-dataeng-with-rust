# if..elseif..else construct

```rust
fn main() {
      //define a variable 
      let learn_language="Rust";
      
      // if..elseif..else construct 
      
      if learn_language == "Rust" { 
         println!("You are learning Rust language!");
      }
      else if learn_language == "Java" { 
         println!("You are learning Java language!");
      }
      else {
         println!("You are learning some other language!");
      } 
}
```

## Nested IF

```rust
// Nested If Block

fn main() {
    //define a variable 
    let learn_language1 = "Rust";
    let learn_language2 = "Java";
    // outer if statement
    if learn_language1 == "Rust" {  // inner if statement
        if learn_language2 == "Java"{
              println!("You are learning Rust and Java language!");
        }
    }
    else {
      println!("You are learning some other language!");
    } 
}
```

## If Expression

```rust
// If Expression

fn main() {
    //define a variable  
    let learn_language = "Rust";
    // short hand construct
    let res= if learn_language == "Rust" {"You are learning Rust language!"} else {"You are learning some other language!"};
    println!("{}", res);
}
```

## Q & A

**Q1: What is the output of the following?**

```rust
// Qn 1

fn main() {
   let age=23; 
   if age >=21{ 
      println!("Age is greater than 21");
   }
    else if age <21{
       println!("Age is less than 21");
    }
    println!("Value Printed");
}
```

**Q2: Which `If` block is executed?**

```rust
fn main() {
   let age=23; 
   let play=true; 
   let activity="Tennis" ;
   if age >=21 && play==false && activity=="Tennis"{ 
     println!("Age is greater than 21");
     println!("You are not allowed to play");
     println!("The sport is {}",activity);
   }
   else if  age >=21 && play==true && activity=="Tennis"{ 
     println!("Age is greater than 21");
     println!("You are allowed to play");
     println!("The sport is {}",activity);
   }
   else if age <21 && play==false && activity=="Tennis"{
     println!("Age is less than 21");
     println!("You are allowed to play");
     println!("The sport is {}",activity);
   }
   else {
     println!("Value Printed");
   }
}
```

**Q3: What is the output of the following code?**

```rust
fn main() {
  let age = 23; 
  let play = true; 
  let activity="Baseball" ;
  if age >= 21 && play==true || activity == "Tennis" { 
    println!("Age is greater than 21");
    println!("You are allowed to play");
    println!("The sport is {}",activity);
  }
  else if  age >= 21 && play == true && activity == "Tennis"{ 
    println!("Age is greater than 21");
    println!("You are allowed to play");
    println!("The sport is {}",activity);
  }
  else if age <21 && play == false && activity == "Tennis"{
    println!("Age is less than 21");
    println!("You are allowed to play");
    println!("The sport is {}",activity);
  }
  else{
    println!("Value Printed");
  }
 }
```
