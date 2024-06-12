# Traits

A trait defines a particular type's functionality and can share with other types. We can use traits to define shared behavior abstractly.

Traits allow us to define interfaces or shared behaviors on types. To implement a trait for a type, we must implement methods of that trait.

When working with Structs, we have enabled Debug and Display traits.&#x20;

Rust supports defining and using custom traits.


```rust
// Display Struct without Trait

#[derive(Debug)]

struct Show {
    name: String,
    total_seasons: u8 
}

#[derive(Debug)]
struct Season {
    season_name: String,
    season_id: u8,
    year: u16
}


fn main(){
	let friends = Show {
		name:String::from("Friends"),
		total_seasons:10
	};

	let currseason = Season {
		season_name:String::from("Last Season"),
		season_id:10,
		year:2004
	};
	
	println!("{:?}", friends);
	println!("{:?}", currseason);
}

```

```rust
// Implementing the same using Traits

struct Show {
    name: String,
    total_seasons: u8 
}

struct Season {
    season_name: String,
    season_id: u8,
    year: u16
}

//We will list the method signature for all the methods that a type 
// implementing the Info trait will need to have.

trait Info {
	// Any datatype that implements this "detail" trait will return a string.

	fn detail(&self) -> String;
}

impl Info for Show{
	fn detail(&self) -> String{
		format!("{} contains {} seasons",self.name,self.total_seasons)
	}
}

impl Info for Season{
	fn detail(&self) -> String{
		format!("you are watching {} ({}) telecasted in {}", self.season_name, self.season_id, self.year)
	}
}

fn main(){
	let friends = Show {
		name:String::from("Friends"),
		total_seasons:10
	};

	let currseason = Season {
		season_name:String::from("Last Season"),
		season_id:10,
		year:2004
	};
	
	
	println!("{}", friends.detail());
	println!("{}", currseason.detail());
}
```

### Polymorphism & Generics

```rust

struct Show {
    name: String,
    total_seasons: u8 
}

struct Season {
    season_name: String,
    season_id: u8,
    year: u16
}

//We will list the method signature for all the methods that a type 
// implementing the Info trait will need to have.

trait Info {
	// Any datatype that implements this "detail" trait will return a string.

	fn detail(&self) -> String;
}

impl Info for Show{
	fn detail(&self) -> String{
		format!("{} contains {} seasons",self.name,self.total_seasons)
	}
}

impl Info for Season{
	fn detail(&self) -> String{
		format!("you are watching {} ({}) telecasted in {}", self.season_name, self.season_id, self.year)
	}
}

// A generic function that works with any type that implements the Describe trait
fn print_description<T: Info>(item: T) {
    println!("{}", item.detail());
}

fn main(){
	let friends = Show {
		name:String::from("Friends"),
		total_seasons:10
	};

	let currseason = Season {
		season_name:String::from("Last Season"),
		season_id:10,
		year:2004
	};
	
	print_description(friends);
	print_description(currseason);
}
```

**Defining Shared Behavior**: Traits allow you to define a set of methods that can be shared across multiple types. Any type that implements a trait must provide the specified behavior, ensuring consistency across types.

**Abstraction**: Traits enable abstraction by allowing you to write generic code that can operate on any type that implements a particular trait.

**Polymorphism**: Traits support polymorphism, which allows you to write code that can work with different types in a uniform manner.

**Extensibility**: Traits provide a way to extend existing types with new behavior without modifying their original implementation.



### Default Implementation

In some cases, it's useful to have a default implementation for one or more of the methods in a trait.

Especially when you have a trait with many methods, you can implement only some of them for every datatype.

```rust
// Default Trait

struct Show {
    name: String,
    total_seasons: u8 
}

struct Season {
    season_name: String,
    season_id: u8,
    year: u16
}


trait Info {
	fn detail(&self) -> String;

	fn description(&self) -> String {
		String::from("No description available")
	}
}

impl Info for Show{
	fn detail(&self) -> String{
		format!("{} contains {} seasons",self.name,self.total_seasons)
	}

}

impl Info for Season{
	fn detail(&self) -> String{
		format!("you are watching {} ({}) telecasted in {}", self.season_name, self.season_id, self.year)
	}

	fn description(&self) -> String{
		format!("Its the series finale episode.")
	}
}



fn main(){
	let friends = Show {
		name:String::from("Friends"),
		total_seasons:10
	};

	let currseason = Season {
		season_name:String::from("Last Season"),
		season_id:10,
		year:2004
	};
	
	
	println!("Friends - Detail : {}", friends.detail());
	println!("Current Season - Detail {}", currseason.detail());
    	println!("---------------------");
	println!("Printing Default Description : {}", friends.description());
	println!("Printing specific Description : {}", currseason.description());

}
```

### Derivable Traits

Provide default implementations for several common traits

The compiler will generate default code for the required methods when you derive traits.

If you need something specific, you'll need to implement the methods yourself.

List of commonly used derivable traits

* Eq
* PartialEq
* Ord
* PartialOrd
* Clone
* Copy
* Hash
* Default
* Debug

```rust
// Comparison

#[derive(PartialEq,PartialOrd)]

struct Show {
    name: String,
    total_seasons: u8 
}

fn main(){
	let friends = Show {
		name:String::from("Friends"),
		total_seasons:10
	};

	let bbt = Show {
		name:String::from("BBT"),
		total_seasons:12
	};
		
	println!("{}", friends == bbt);
	println!("{}", friends > bbt);	

}
```

What if we need to have custom comparison on specific items

```rust
// Custom Comparison

#[allow(dead_code)]

struct Show {
    name: String,
    total_seasons: u8,
}

// self = self: Self and &self = self: &Self

trait Comparison {
    fn eq(&self, obj1:&Self) -> bool;
}

impl Comparison for Show {
    fn eq(&self, obj1: &Self) -> bool {
        if self.total_seasons == obj1.total_seasons {
            true
        } else {
            false
        }
    }
}

fn main() {
    let friends = Show {
        name: String::from("Friends"),
        total_seasons: 10,
    };

    let bbt = Show {
        name: String::from("BBT"),
        total_seasons: 12,
    };

    println!("Custom Comparison {}", friends.eq(&bbt));
}
```

### Another Example with Numerical values

```rust
//declare a structure

struct Circle {
    radius: f32,
}

struct Rectangle {
    width: f32,
    height: f32,
}

struct Square {
    width: f32,
}

//declare a trait

trait Area {
    fn shape_area(&self) -> f32;
}

//implement the trait

impl Area for Square {
    fn shape_area(&self) -> f32 {
        self.width * self.width
    }
}

impl Area for Circle {
    fn shape_area(&self) -> f32 {
        3.14 * self.radius * self.radius
    }
}

impl Area for Rectangle {
    fn shape_area(&self) -> f32 {
        self.width * self.height
    }
}

fn main() {
    //create an instance of the structure
    let c = Circle { radius: 2.0 };

    let r = Rectangle {
        width: 2.0,
        height: 2.0,
    };

    let s = Square { width: 5.0 };

    println!("Area of Circle: {}", c.shape_area());
    println!("Area of Rectangle:{}", r.shape_area());
    println!("Area of Rectangle:{}", s.shape_area());
}
```
