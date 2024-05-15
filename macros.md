# Macros

Rust provides a powerful macro system that allows metaprogramming. As you've seen in previous chapters, macros look like functions, except that their name ends with a bang !, but instead of generating a function call, macros are expanded into source code that gets compiled with the rest of the program.

Macros are created using the **macro\_rules!** Macro.

() -- takes no argument ($argument: designator)

**Popular designators are**

expr is used for expressions&#x20;

ty is used to type&#x20;

ident is used for variable/function names

**Syntax**

```
macro_rules! <name of macro>{
    () => {}
}
```

```
() - Match for the pattern
{} - Expand the code / Body of the macro
```

```
// Macro with No argument

macro_rules! print_hello {
    () => {
        // The macro will expand into the contents of this block.
        println!("Hello World");
    };
}

fn main() {
    print_hello!();
}
```

**Macro returning a constant value**

```
// Macro returning value 10

macro_rules! ten {
    () => {5 + 5};
}

fn main(){
    println!("{}",ten!());
}
```

**Macro with one argument**

using **expr** designator

```
// Macro with one argument

macro_rules! hi {
    ($name:expr) => {
        println!("Hello {}!",$name);
    };
}

fn main() {
    hi!("Rachel");
}
```

**Simple addition macro**

```
// Takes two arguments

macro_rules! add{
    ($a:expr,$b:expr)=>{
         {
            $a+$b
        }
    }
}

fn main(){
    let c = add!(1,2);
    println!("{c}");
}

```

**Demo Stringify**

```
// Stringify
//In Rust, stringify! is a macro that takes a Rust expression 
//and converts it into a string literal 

fn main() {
    println!("{},{}",1+1,stringify!("1+1"));
}

```

**Macro with Expressions**

```
// More Expressions

macro_rules! print_result {
    ($expression:expr) => {
        println!("{:?} = {:?}", stringify!($expression), $expression);
    };
}

fn main() {
    print_result!(1 + 1);

    // Recall that blocks are expressions too!
    print_result!({
        let x = 10; x * x + 2 * x - 1
    });
}
```

using **expr** and **ty** designators

```
// multiple designators
// variables with different datatypes can be added using this macro

macro_rules! add_using{
    // using a ty token type for matching datatypes passed to the macro
    
    ($x:expr,$y:expr,$typ:ty)=>{
        $x as $typ + $y as $typ
    }
}

fn main(){
    let i:u8 = 5;
    let j:i32 = 10;
    println!("{}",add_using!(i,j,i32));
}
```

**Repeat / Dynamic Arguments**

```
($($v:expr),*)  - Here the star (*) will repeat the patterns inside $()
And comma is the separator.
```

```
// Repeat / Dynamic number of arguments

macro_rules! hi {
    ($($name:expr),*) => {
        {
            //let mut n = Vec::new();
            $(
                println!("Hi {}!",$name);
            )*
        }
    };
}

fn main() {
    hi!("Rachel","Ross","Monica");
}
```

Remember vec! Macro?

Let's try to create our equivalent of it.

```
// Creating vec! equivalent 

macro_rules! my_vec {
    (
        $( $name:expr ), * ) => {
        {
            let mut n = Vec::new();
            $( n.push($name); )*
            
            n
        }
    };
}

fn main() {
    println!("{:?}",my_vec!("Rachel","Ross","Monica"));
}
```

### Repeat - with Numeric arguments

```
macro_rules! add_all{
    ($($a:expr) , *) => 
    {
    // initial value of the expression
    0
    // block to be repeated
    $(+$a)*
    }
}

//The * in $(+$a)* is a repetition operator, meaning 
//"repeat +$a for each $a matched".

fn main(){
    println!("{}",add_all!(1,2,3,4));
    //println!("{}",add_all!());
}
```

### Compile time Assertions

```

macro_rules! assert_equal_len {
    ($a:expr, $b:expr) => {
        assert!($a.len() == $b.len(), "Arrays must have the same length");
    };
}

fn main() {
    let a1 = [1, 2, 3];
    let a2 = [4, 5, 6];
    assert_equal_len!(a1, a2); // Compiles fine

    //let a3 = [7, 8];
    //assert_equal_len!(a1, a3); // This will fail to compile
}

```

### Macro Overloading

Overload to accept different combinations of arguments

```
// `check!` will compare `$left` and `$right`
// in different ways depending on how you invoke it:

macro_rules! check {

    ($left:expr; and $right:expr) => {
        println!("{:?} and {:?} is {:?}",
                 stringify!($left), stringify!($right), $left && $right)
    };

    ($left:expr; or $right:expr) => {
        println!("{:?} or {:?} is {:?}",
                 stringify!($left), stringify!($right), $left || $right)
    };
}

fn main() {
    check!(1i32 + 1 == 2i32; and 2i32 * 2 == 4i32);
    check!(true; or false);
}
```
