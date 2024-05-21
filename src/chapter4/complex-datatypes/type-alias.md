# Type Alias

A _type alias_ defines a new name for an existing type. Type aliases are declared with the keyword `type.`

1. Improving Readability
   
Type aliases can make complex types easier to read and understand.

2. Enhancing Maintainability
   
Type aliases can help centralize the definition of a type, making it easier to update the type across the codebase.

## Point to remember

The first letter of the type should be in upper case.

```rust
// type alias

type Bannertype = u32;

fn main() {
    let mut id: Bannertype = 91615214;
    println!("{id}");
    id = 91615200;
    println!("{id}");
}
```

## Another example

```rust
type Kilometers = i32;
type Meters = i32;

fn calculate_distance(distance: Kilometers) -> Meters {
    distance * 1000
}

fn main() {
    let distance: Kilometers = 5;
    let distance_in_meters: Meters = calculate_distance(distance);
    println!("Distance in meters: {}", distance_in_meters);
}




