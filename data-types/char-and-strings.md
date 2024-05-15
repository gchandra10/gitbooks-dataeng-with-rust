# Char & Strings

The value assigned to a char variable is enclosed in a single quote(`''`) .

**Unlike some other languages, a character in Rust takes up 4 bytes rather than a single byte**. It does so because it can store a lot more than just an ASCII value like emojis, Korean, Chinese, and Japanese characters.

```
fn main() { 
    // implicitly & explicitly define
    let char_2:char = 'a';
    let char_3 = 'b';
    println!("character2: {}", char_2);
    println!("character3: {}", char_3);
}
```

### **String Literal**

Used when the value of the string is known at compile time. Literals are set of characters that are hardcoded to a variable at compile time. String literals are found in the module `std::str`

String literals are stored in the Stack portion of the memory so retrieval is fast.

```
fn main() {
    // explicitly define 
    let str_1:&str = "Rust Programming";
    println!("String 1: {}", str_1);
 
    // implicitly define
    let str_2 = "Rust Programming";
    println!("String 2: {}", str_2);
}

```

### String Object

String objects are dynamic and can be changed during runtime.

A String object is allocated in the heap memory. Its slower but has more features.

String::new() - Creates an empty string.

String::from() - Default value passed as parameter.

```
fn main(){
   let empty_string = String::new();
   println!("length is {}",empty_string.len());

   let content_string = String::from("Rachel Green");
   println!("length is {}",content_string.len());
}
```

String Operations

variable.push() - to push a single character

```
// Push Single Character

fn main(){
   let mut name1 = String::from("Hello");
   println!("{}",name1);
   name1.push('!');
   println!("{}",name1);
}
```

variable.push\_str() - to push a set of characters

```
// Push a string

fn main(){
   let mut name1 = String::from("Hello");
   println!("{}",name1);
   name1.push_str("World");
   println!("{}",name1);
}
```

variable.replace("","")

```
fn main(){
   let name1 = String::from("Hello!");
   let name2 = name1.replace("Hello","Howdy");    //find and replace
   println!("{}",name2);
}
```

**Convert String Literal to String Object (to\_string())**

```

fn main(){
   let name1 = "Hello!".to_string();              //String object
   let name2 = name1.replace("Hello","Howdy");    //find and replace
   println!("{}",name2);
}
```

**Convert String Object to String Literal (as\_str())**

```
fn main() {
    let name1 = String::from("hello");
    let name2 = name1.as_str();
    println!("{},{}", name1, name2);
}
```

### Script to find the data type

```
fn print_type_of<T>(_: &T) {
    println!("{}", std::any::type_name::<T>())
}

fn main() {
    let name = "StringSample";
    let name1 = String::from("Hello");
    print_type_of(&name);
    print_type_of(&name1);
}    
```

