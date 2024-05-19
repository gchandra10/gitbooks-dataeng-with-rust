# Structs

Popular custom datatype for grouping related values. Like a Tuple, Structs help to group related values of mixed data types.

Unlike a Tuple, you will assign a name to each value to indicate what it means. In the tuple, you will be using .0 .1 notation, but with struct, you can use the actual name.

### Classic Struct

```
- Most commonly used.
- Each field has a name and a type.
```

```rust
struct Students {
	id:i32,
	name:String,
	course:String
}

fn main(){
    let s:Students = Students{
        id:10,
        name:String::from("Rachel"),
        course:String::from("DB")
    };

    println!("{},{},{}",s.id,s.name,s.course);

}
```

Similar to Type alias, the name of the struct begins with an uppercase letter followed by lowercase characters.

Structs are usually declared outside the main function. If the scope is local, it can be declared inside the main.

#### Struct - Stack or Heap?

```rust
// Struct Stack or Heap

struct Students {
    id: i32
}

fn main() {
    let s: Students = Students {
        id: 10
    };

    let s4 = s; //Is this COPY or Move ?
    
    println!("{}",s.id)
    
}
```

```
// lets clone it so we can make a copy of the Struct

let s4 = s.clone();
```

What do we see now?

```
method `clone` not found for this struct
```

Let's set the Clone trait for the struct Students

```
// Adding Clone trait to the struct Students
#[derive(Clone)]
struct Students{id:i32}
```

Instead of printing s.id can you try printing the entire Struct?

```
// Using debug trait print the value of S

println!("{:?}",s);
```

Now, what do you see?

```
// Adding Clone and Debug trait to the struct Students

#[derive(Clone,Debug)]
struct Students{id:i32}
```

#### Struct inside Vector

```rust
#[derive(Debug, Clone)]
struct Students {
    id: i32,
    name: String,
    course: String,
}

fn main() {
    let s: Students = Students {
        id: 10,
        name: String::from("Rachel"),
        course: String::from("DB"),
    };

    let s1: Students = Students {
        id: 11,
        name: String::from("Monica"),
        course: String::from("DB"),
    };

    let s2: Students = Students {
        id: 12,
        name: String::from("Phoebe"),
        course: String::from("DB"),
    };

    let mut s_vec: Vec<Students> = Vec::new();

    s_vec.push(s);
    s_vec.push(s1);
    s_vec.push(s2);

    for v in s_vec.iter() {
         println!("{},{},{}", v.id, v.name, v.course);
    }
}
```

### Struct implementation

The implementation block has the keyword "impl" followed by the same name as Struct. It contains methods and functions. A struct can have more than one method or function.

Methods: methods are similar to functions with "fn" keyword. They can have parameters and return values. The only difference is, they are defined within the context of a struct and their first parameter is always self.

Let's see an example

```rust
#[derive(Debug, Clone)]
struct Students {
    id: i32,
    name: String,
    course: String,
}

impl Students {
    
    // either use self or self: &Self it all means the same
    //fn get_student_details(self){
    
    fn get_student_details(self: &Self){
        println!("{}", self.id);
        println!("{}", self.name);
        println!("{}", self.course);
    }

}

fn main() {
    let s: Students = Students {
        id: 10,
        name: String::from("Rachel"),
        course: String::from("DB"),
    };
    
    let s1: Students = Students {
        id: 11,
        name: String::from("Monica"),
        course: String::from("DB"),
    };
    
    s.get_student_details();
    s1.get_student_details();
}    
```

#### Using Associated Function

Functions inside the impl block that do not take "self" as a parameter.&#x20;

```rust

#[derive(Debug, Clone)]
struct Students {
    id: i32,
    name: String,
    course: String,
}

impl Students {
    fn get_student_details(self){
        println!("{}", self.id);
        println!("{}", self.name);
        println!("{}", self.course);
    }
    
    fn create_student(pid:i32,pname:String,pcourse:String) -> Students{
        Students{id:pid,name:pname,course:pcourse}
    }
}

fn main() {

    // let s: Students = Students {
    //     id: 10,
    //     name: String::from("Rachel"),
    //     course: String::from("DB"),
    // };
    
    // let s1: Students = Students {
    //     id: 11,
    //     name: String::from("Monica"),
    //     course: String::from("DB"),
    // };
    
    // s.get_student_details();
    // s1.get_student_details();
    
    // Creating Student using Associated Function and printing it via Method
    
    let s2 = Students::create_student(12,"Ross".to_string(),"C++".to_string());
    s2.get_student_details();
}    
```

#### Mutable Implementation

```rust
// Using Mutable & Borrow operator

#[derive(Debug, Clone)]
struct Students {
    id: i32,
    name: String,
    course: String,
}

impl Students {
    fn get_student_details(&self){
        println!("-------------------");
        println!("{}", self.id);
        println!("{}", self.name);
        println!("{}", self.course);
        println!("-------------------");
    }
    
    fn create_student(pid:i32,pname:String,pcourse:String) -> Students{
        Students{id:pid,name:pname,course:pcourse}
    }
    
    fn change_student_details(&mut self, id:i32, new_name:String, new_course:String){
        self.name=new_name;
        self.course=new_course;
    }
}

fn main() {

    let s = Students {
        id: 10,
        name: String::from("Rachel"),
        course: String::from("DB"),
    };
    
    let s1 = Students {
        id: 11,
        name: String::from("Monica"),
        course: String::from("DB"),
    };
    
    s.get_student_details();
    s1.get_student_details();
    
    // Creating Student using Associated Function and printing it via Method
    
    let mut s2 = Students::create_student(12,"Ross".to_string(),"C++".to_string());
    s2.get_student_details();
    
    s2.change_student_details(12,"Ross Geller".to_string(),"CPP".to_string());
    s2.get_student_details();
}    
```

### Tuple Struct

Tuple Structs - Similar to Classic but fields have no names.

```rust
// Tuple Struct

struct Coordinates(u32, u32);

fn main() {
    let xy = Coordinates(10, 20);
    //it behaves like Tuples
    println!("Value of the Tuple Struct xy {},{}", xy.0, xy.1);
    
    //Destructuring Tuple Struct

    let Coordinates(a,b) = xy;
    println!("Values of variables a & b {},{}", a, b);
}
```

