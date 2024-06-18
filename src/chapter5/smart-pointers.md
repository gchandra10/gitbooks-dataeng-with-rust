# Smart Pointers

## Box

A good use case for the Box type in Rust programming is when you have a large data structure that you want to **store on the heap rather than on the stack**.

The Box type allows you to store the data on the heap in a safe and efficient way.

One reason why using a **Box might be beneficial** is that it can **help you avoid stack overflows**. The stack is a fixed-size data structure, so if you try to store a large data structure on the stack, it can overflow and cause your program to crash.

## Use Cases

- Dynamic Sized DataTypes
- Recursive Data Structures
- Reducing Stack Usage
- Enforcing Single Ownership. (instead of splitting with Stack and Heap)

<figure><img src="../assets/toy_box.png" alt=""><figcaption><p>Toy Box</p></figcaption></figure>

What do you think about using a Toy Box?

Rust has a Smart Pointer called Box\<T>. It allows developers to store data on the heap rather than the stack. What remains on the stack is the pointer to the heap data.

Boxes don't have performance overhead other than storing their data on the heap instead of on the stack.

```rust

fn main() {
    let speed = 88;
    let box_speed: Box<i32> = Box::new(speed);
    println!("speed {}, Stack location of speed {:p}", speed, &speed);
    println!("Stack location of box_speed {:p}", &box_speed);
    println!(
        "Heap location of value stored inside box_speed {:p}",
        Box::into_raw(box_speed)
    );
}
```

**The as_ptr() method works on arrays and slices**

```rust
fn main() {

    let large_array: [i32; 5] = [1,2,3,4,5];
    let large_array1: Box<[i32; 5]> = Box::new([1, 2, 3, 4, 5]);

    println!("Stack Memory Location of variable large_array : {:p} {:p} {:?}", &large_array, large_array.as_ptr(), large_array);
    
    println!("Heap Memory Location of variable large_array1 : {:p} {:p} {:?}", &large_array1,  large_array1.as_ptr(), large_array1);

}
```

```rust
// Better use case for using Box

use std::mem;

#[allow(dead_code)]
#[derive(Debug)]

struct Class {
    id: i32,
    fname: String,
    lname: String,
}

fn main() {
    let c = Class {
        id: 34,
        fname: String::from("Rachel"),
        lname: String::from("Green"),
    };

    println! {"{:?}", c};

    // Find the Size of the Variable in the Stack
    println!("Class size on stack: {:p} {} bytes",&c,mem::size_of_val(&c));

    let boxed_class: Box<Class> = Box::new(c);
    // Size of the Boxed Variable in Stack pointing to Heap.
    println!("boxed_class size on stack: {:p} {} bytes",&boxed_class,mem::size_of_val(&boxed_class));

    // Size of the Boxed Variable in Heap
    println!("boxed_class size on heap: {} bytes", mem::size_of_val(&*boxed_class) );

    let unbox_class: Class = *boxed_class;
    println!("unbox class size on stack: {} bytes", mem::size_of_val(&unbox_class));
}
```

```rust
// Stack to Heap

#[allow(dead_code)]
#[derive(Debug)]
struct Class {
    id: i32,
    fname: String,
    lname: String,
}

fn main() {
    let c = Class {
        id: 34,
        fname: String::from("Rachel"),
        lname: String::from("Green"),
    };
    
    let a = 10;
    let s = String::from("Hello");
    
    // Stack
    println!("Sample Stack location {:p}", &a);
    // Heap
    println!("Sample Heap location {:p}", s.as_ptr());

    println!("\nBefore Boxing the Struct \n");
    println!("Stack Memory Location of Struct variable c : {:p}\nStruct Value : {:?}", &c, c);
    println!("Stack Location of c.id : {:p}", &c.id);
    println!("Stack c.fname pointing to : {:p} \nHeap c.fname {:p}", &c.fname,c.fname.as_ptr());
    println!("Stack c.lname pointing to : {:p} \nHeap c.lname {:p}", &c.lname,c.lname.as_ptr());
    
    println!("\nAfter Boxing the Struct \n");
    let b = Box::new(Class {
        id: 34,
        fname: String::from("Rachel"),
        lname: String::from("Green"),
    });
    println!("Heap Memory Location  {:p}\nStruct Value {:?}", b, b);
    println!("\n");
    println!("Heap Location of b.id : {:p}", &b.id);
    println!("Heap b.fname pointing to : {:p} \nHeap Location b.fname {:p}",&b.fname,b.fname.as_ptr());
    println!("Heap b.lname pointing to : {:p} \nHeap Location b.lname {:p}",&b.lname,b.lname.as_ptr());
}
```

## Linked List Example

```rust
// Linked List

Here is an example of a linked list that could be stored on the stack in Rust:

struct Node {
    value: i32,
    next: Option<Box<Node>>,
}

struct LinkedList {
    head: Option<Box<Node>>,
}
```

In this example, the Node struct represents a single node in the linked list, and the LinkedList struct represents the entire linked list. The head field of the LinkedList struct contains a reference to the first node in the list, and each Node struct has a next field that contains a reference to the next node in the list.

Because this data structure is relatively small, it can be stored on the stack without problems. However, if the linked list became very large, it could cause a stack overflow, in which case it would be better to store it on the heap using a Box type.

