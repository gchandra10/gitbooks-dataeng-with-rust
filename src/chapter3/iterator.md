# Iterator

Iteration is the process of looping through a set of values.

How its different from Loops?

Loops are Imperative. You must mention how often to loop over and follow Procedural-style programming.

Iterators are Declarative. This means it specifies what to do instead of how to do it and follows Functional Style programming.

## Functional Programming:

**Declarative Style:** Developers describe what they want rather than specifying how step-by-step.

**Pure Functions:** Pure functions are functions that always return the same output for the same input, and they have no side effects. They don't modify any external state or data outside their scope, making them easier to reason about and less prone to bugs.

## Looping through an array using traditional method.

```rust
fn main() {
    let ages = [27, 35, 40, 10, 19];
    let mut index = 0;

    while index < ages.len() {
        let age = ages[index];
        println!("Age = {:?}", age);
        index += 1;
    }
}
```

```rust
// Using Iterator

fn main() {
    let ages = [27, 35, 40, 10, 19];
    let ages_iterator = ages.iter();

    for age in ages_iterator {
        println!("Age = {:?}", age);
    }
}
```

`Some(T)`: Indicates that there is a value, and it's of type `T`

We will discuss more about **Some** in next chapter. It's like you have Some(letter) in your mailbox.

The purpose is to replace the concept of Null and handle Null Safety. It also handles Type Safety.


```rust
fn main() {
    let ages = [27, 35, 40, 10, 19];
    let mut ages_iterator = ages.iter();
    
    println!("{:?}",ages_iterator.next());
    println!("{:?}",ages_iterator.next());
    println!("{:?}",ages_iterator.next());
    println!("{:?}",ages_iterator.next());
    println!("{:?}",ages_iterator.next());
    println!("{:?}",ages_iterator.next());

}
```

```rust
fn main() {
    let ages = [27, 35, 40, 10, 19];
    let mut ages_iterator = ages.iter();

    while let Some(x) = ages_iterator.next(){
        println!("{:?},{}",Some(x),x);
    }
}
```


```rust
fn main() {
    let ages = [27, 35, 40, 10, 19];
    let mut ages_iterator = ages.iter();

    // Looping thru Array
    for age in ages {
        println!("Age = {:?}", age);
    }

    println!("{:?}", ages_iterator.next());
    
    // Looping thru an Iterator. See the additional functionality it offers
    
    for age in ages_iterator {
        println!("Age = {:?}", age);
    }
}
```
