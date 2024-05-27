# Command Line Args

Command Line Arguments

CLI Arguments are passed to the program when it is invoked.

**Example**

`rustc --version`

_Commonly used for File Paths & Configuration Settings._

To use Command Line Arguments, you need to include a standard libraries environment module.

**std::env::args**

Returns an iterator over arguments passed to the program.

The first argument is traditionally the executable path.

```rust
// command line arguments

use std::env;

fn main(){
    for (index,argument) in  env::args().enumerate(){
        println!("{},{}", index, argument)
    }
}
```

Pick a specific argument.

```
// option 1

let arg2 = eng::args().nth(2);
prinln!("{}", arg2);

// another option
let name = env::args().skip(1).next();

// dbg macro
dbg!(env::args());
```

**Some**

```rust
use std::env;

fn main() {
    println!("{:?}",env::args());
    
    let name = env::args().skip(1).next();
    
    match name{
        Some(n) => println!("Hi {n}"),
        None => panic!("Missing parameter")
    }
   
}
```

Checking for the number of arguments.&#x20;

Example for copying you need  src and destination&#x20;

```

if env::args().len() <= 2{
    println!("need atleast 2 args");
    return;  //exists the program
}

```

