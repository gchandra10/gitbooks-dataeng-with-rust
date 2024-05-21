# Enums

**Enumerators**

Define a data type with multiple possible variants.

If Today is Tuesday, it can be written as Tue, Tuesday, TUESDAY, T in several forms. How to standarize it?

Example:

- Days of the Week.
- Months in a year.
- Traffic light colors.


It Enumerates a finite number of options or types.

* Create custom enum types.
* How enums are commonly used.
* There are few standard enums you will use in Rust.


```rust
#[derive(Debug)]
enum TrafficLight{
    Red,
    Yellow,
    Green
}

fn main(){
    let my_light = TrafficLight::Red;

    println!("{:?}", my_light);
}
```

**Importance of using derive(Debug) Trait.**
Execute this script to see the result.

```rust
enum TrafficLight{
    Red,
    Yellow,
    Green
}

fn main(){
    let my_light = TrafficLight::Red;

    println!("{:?}", my_light);
}
```

In addition to simply representing one of several types, we can have additional data based on the value.

Let's add Unnamed parameters in parenthesis.

```rust
// Enum with additional data

#[derive(Debug)]
enum TrafficLight{
    Red (bool),
    Yellow (bool),
    Green (bool)
}

fn main(){
    let my_light = TrafficLight::Red(true);

    println!("{:?}", my_light);
}
```

```rust
// Separate the value and enum result

#[derive(Debug)]
enum TrafficLight{
    Red (bool),
    Yellow (bool),
    Green (bool)
}

fn main(){
    let my_light = TrafficLight::Red(false);

    println!("{:?}", my_light);
    
    match my_light {
        TrafficLight::Red(is_active) => println!("Red: {}", is_active),
        TrafficLight::Yellow(is_active) => println!("Yellow: {}", is_active),
        TrafficLight::Green(is_active) => println!("Green: {}", is_active),
    }
}
```



### Enums inside Enums

```rust
#[derive(Debug)]
enum TrafficLight {
    Red(bool),
    Yellow(bool),
    Green(bool),
}

#[derive(Debug)]
enum Vehicle {
    Stop,
    Drive(f64),
    CheckLight(TrafficLight),
}

fn main() {
    let my_light = TrafficLight::Red(true);
    let instruction = Vehicle::CheckLight(my_light);

    match instruction {
        Vehicle::Stop => println!("Stop"),
        Vehicle::Drive(speed) => println!("Drive at speed: {}", speed),
        Vehicle::CheckLight(light) => match light {
            TrafficLight::Red(is_active) => println!("Red light: {}", is_active),
            TrafficLight::Yellow(is_active) => println!("Yellow light: {}", is_active),
            TrafficLight::Green(is_active) => println!("Green light: {}", is_active),
        },
    }
}

```

In Database world, commonly usages are

```
enum RightClick {
    Copy,
    Paste,
    Save,
    Quit
}

enum FileFormat {
    CSV,
    Parquet,
    Avro,
    JSON,
    XML,
}

enum LogLevel {
    Debug,
    Info,
    Warn,
    Error,
    Critical,
}


enum DataTier {
    Hot,
    Warm,
    Cold,
    Archived,
}
```

### Enum Implements

Similar to Struct, you can implement an interface in Enum.

The Implement interface can be helpful when we need to implement some business logic tightly coupled with a discriminatory property of a given enum.

```rust
// Modified from Source: Barron Stone Git Repository

#[derive(Debug)]
enum Shape {
    Circle(f64), // radius
    Rectangle(f64, f64), // width, height
    Triangle(f64, f64, f64) // sides a, b, c
}

impl Shape {
    fn get_perimeter(&self) -> f64 {
        match *self {
            Shape::Circle(r) => r * 2.0 * std::f64::consts::PI,
            Shape::Rectangle(w, h) => (2.0 * w) + (2.0 * h),
            Shape::Triangle(a, b, c) => a + b + c
        }
    }
}

fn main() {
    let my_shape = Shape::Circle(1.2);
    println!("my_shape is {:?}", my_shape);

    let perimeter = my_shape.get_perimeter();
    println!("perimeter is {}", perimeter);
    
    let my_shape1 = Shape::Triangle(3.0,4.0,5.0);
    println!("my_shape is {:?}", my_shape1);

    let perimeter1 = my_shape1.get_perimeter();
    println!("perimeter is {}", perimeter1);
    
    
    let my_shape2 = Shape::Rectangle(4.0,5.0);
    println!("my_shape is {:?}", my_shape2);

    let perimeter2 = my_shape2.get_perimeter();
    println!("perimeter is {}", perimeter2);
    
}
```

## Commonly used standard Enums

### Option

Many languages use NULL to indicate no value.

Errors often occur when using a NULL.

Rust does not have a traditional null value.

```rust
// Sample Option Enum

fn main() {
    let x = Some(5);  //Option <i32>
    let y = Some(4.0); // Option <f64>
    let z = Some("Hello"); //Option <&str>
    let a = None; //N should be upper case
    let a_vec: Option<Vec<i32>> = Some(vec![0, 1, 2, 3]);
}
```

```rust
// Simple Division

fn try_division(dividend: i32, divisor: i32) -> i32 {
    dividend / divisor
}

fn main() {
    println!("{}",try_division(4, 2));
    //println!("{}",try_division(4, 0));
}
```

Sometimes it's desirable to catch the failure of some parts of a program instead of calling `panic!`; this can be accomplished using the `Option` enum.

```
// Common Enum

enum Option <T>{
    Some(T),
    None
}
```

This achieves the same concept as a traditional null value, but implementing it in terms of an enum data type compiler can check to make sure you are handling it correctly.

It's commonly used and included in the prelude. That means additional use statements are needed.

```rust
// Error Handling

// An integer division that doesn't `panic!`
fn checked_division(dividend: i32, divisor: i32) -> Option<i32> {
    if divisor == 0 {
        // Failure is represented as the `None` variant
        None
    } else {
        // Result is wrapped in a `Some` variant
        Some(dividend / divisor)
    }
}

fn try_division(dividend: i32, divisor: i32) {
    // `Option` values can be pattern matched, just like other enums
    match checked_division(dividend, divisor) {
        None => println!("{} / {} failed!", dividend, divisor),
        Some(quotient) => {
            println!("{} / {} = {}", dividend, divisor, quotient)
        },
    }
}

fn main() {
    //try_division(4, 2);
    try_division(4, 0);
    
}
```

### Result

```
// Another Prelude

enum Result<T, E>{
  Ok(T),
  Err(E)
}
```

#### `Ok(T)` <a href="#variant.ok" id="variant.ok"></a>

It contains the success value.

#### `Err(E)`

Contains the error value

```rust
// Simple Simple Interest Function

fn si(p:f32,n:f32,r:f32) -> f32 {
	(p * n * r )/100 as f32
}


fn main(){
	let p:f32 = 10000.00;
	let n:f32 = 3.00;
	let r:f32 = 1.4;

	let si = si(p,n,r);
	println!("Simple Interest = {si}");
}
```

**How to handle if the parameter is Zero?**

```rust
// SI with conditions

fn si(p:f32,n:f32,r:f32) -> f32 {
    if p <= 0. {
        println!("p cannot be zero");
    }
    
    if n <= 0.{
        println!("n cannot be zero");
    }
    
    if r <= 0. {
        println!("r cannot be zero");
    }
    
	(p * n * r )/100 as f32
}


fn main(){
	let p:f32 = 10000.00;
	let n:f32 = 3.00;
	let r:f32 = 0.0;

	let si = si(p,n,r);
	println!("Simple Interest = {si}");
}
```

Do you notice any issues with this?

Yes, the message is displayed, but still, the calculation takes place, and the Error message is only for informational purposes.

How does Result enum help in this case?



```rust
// using Result

fn si(p: f32, n: f32, r: f32) -> Result<f32, String> {
    if p <= 0. {
        return Err("Principal cannot be less or equal to zero".to_string());
    }

    if n <= 0. {
        return Err("Number of years cannot be less or equal to zero".to_string());
    }

    if r <= 0. {
        return Err("Rate cannot be less or equal to zero".to_string());
    }

    Ok((p * n * r) / 100.0)
}

fn main() {
    let p: f32 = 10000.0;
    let n: f32 = 3.0;
    let r: f32 = 1.4;

    match si(p, n, r) {
        Ok(result) => println!("si = {result}"),
        Err(e) => println!("error occured {:?}", e),
    }
}
```

**Difference when using Result and Option Example**

```rust
// using Result

fn si_using_result(p: f32, n: f32, r: f32) -> Result<f32, String> {
    if p <= 0. {
        return Err("Principal cannot be less or equal to zero".to_string());
    }

    if n <= 0. {
        return Err("Number of years cannot be less or equal to zero".to_string());
    }

    if r <= 0. {
        return Err("Rate cannot be less or equal to zero".to_string());
    }

    Ok((p * n * r) / 100.0)
}

fn si_using_option(p: f32, n: f32, r: f32) -> Option<f32> {
    if p <= 0. {
        return None;
    }

    if n <= 0. {
        return None;
    }

    if r <= 0. {
        return None;
    }

    Some((p * n * r) / 100.0)
}

fn main() {
    let p: f32 = 10000.0;
    let n: f32 = 0.0;
    let r: f32 = 1.4;

    match si_using_result(p, n, r) {
        Ok(result) => println!("si = {result}"),
        Err(e) => println!("Result ENUM - Error occured {:?}", e),
    }
    
    match si_using_option(p, n, r) {
        Some(result) => println!("si = {result}"),
        None => println!("Option ENUM - Error occurred: one of the inputs is non-positive"),
    }
}
```

### The ? operator

**? is used for Error Propogation**

There is an even shorter way to deal with Result (and Option), shorter than a match and even shorter than if let. It is called the "**question mark operator**."

After a function that returns a result, you can add ?. This will:

If its Ok, return the result

If its Err, return the error


```rust
fn calc_si(p: f32, n: f32, r: f32) -> Result<f32, String> {
    if p <= 0. {
        return Err("Principal cannot be less or equal to zero".to_string());
    }

    if n <= 0. {
        return Err("Number of years cannot be less or equal to zero".to_string());
    }

    if r <= 0. {
        return Err("Rate cannot be less or equal to zero".to_string());
    }

    Ok((p * n * r) / 100.0)
}

fn print_si(p: f32, n: f32, r: f32) -> Result<f32, String>{
    let result_si = calc_si(p,n,r)?;
    Ok(result_si)
}

fn main() {
    let p: f32 = 10000.0;
    let n: f32 = 3.;
    let r: f32 = 1.4;

    println!("{:?}",print_si(p,n,r));

}
```

Skip the intermediate print\_si function


```rust

fn si(p: f32, n: f32, r: f32) -> Result<f32, String> {
    if p <= 0. {
        return Err("Principal cannot be less or equal to zero".to_string());
    }

    if n <= 0. {
        return Err("Number of years cannot be less or equal to zero".to_string());
    }

    if r <= 0. {
        return Err("Rate cannot be less or equal to zero".to_string());
    }

    Ok((p * n * r) / 100.0)
}

fn main() -> Result<(), String> {
    let p: f32 = 10000.0;
    let n: f32 = 3.0;
    let r: f32 = 1.4;

    let result = si(p, n, r)?;
    println!("si = {result}");
    Ok(())
}
```

### Another Simple Example

```rust
// Simple Parse Example

fn parse_str(input: &str) -> Result<i32, std::num::ParseIntError> {
    let parsed_number = input.parse::<i32>()?;
    Ok(parsed_number)
}

fn main() {
    let str_vec = vec!["Seven", "8", "9.0", "nice", "6060"];
    for item in str_vec {
        let parsed = parse_str(item);
        println!("{:?}", parsed);
    }
}
```