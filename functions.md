# Functions

Like other programming languages, functions are the basic building blocks of readable, maintainable, and reusable code.

In Rust, functions can be created before or after the main routine.

### Simple Function

```
// Simple Function

fn main(){
   //calling a function
   hello();
}

fn hello(){
   println!("Hi");
}
```

### Return a Value

```
// Return Value
// Demonstrate the same with the return value (35000.00*5.0*6.4/100.00)

fn main(){
   println!("Hi {}",calc_si());
}

fn calc_si()->f32 {
   35000.00*5.0*6.4/100.00
}
```

### Call By Value

```
// Call by Value

fn main(){
   let no:i32 = 5;
   changeme(no);
   println!("Main Function:{}",no);
}

fn changeme(mut param_no: i32) {
   param_no = param_no * 0;
   println!("Inside the Function :{}",param_no);
}
```

### Call By Reference

```
// Call by Reference

// Call by Reference

fn main() {
    let mut no: i32 = 5;
    println!("Main fucntion initial value :{} -> {:p}", no,&no);
    changeme(&mut no);
    println!("Main function final value  is:{} -> {:p}", no,&no);
}

fn changeme(param_no: &mut i32) {
    println!("Changeme function initial value :{} -> {:p}", *param_no,&(*param_no));
    *param_no = 0; //de reference
    println!("Changeme function final value :{} -> {:p}", *param_no,&(*param_no));
}

```



Call By Reference

