# Map and Collect

**Map:** The map function is used to transform elements of an iterator. It takes a closure and applies this closure to each element of the iterator, producing a new iterator with the transformed elements.

**Collect:** The collect function is used to transform an iterator into a collection, such as a Vec, HashMap, or HashSet. It consumes the iterator and returns the new collection.

```rust
fn main() {
    let numbers = vec![1, 2, 3, 4, 5];
    println!("Mapping: {:?}",numbers.iter().map(|x| x * 2));
    
    
    let doubled: Vec<i32> = numbers.iter().map(|x| x * 2).collect();
    println!("Map and Collect {:?}", doubled);
}
```

- numbers.iter() creates an iterator over the elements of the numbers vector.
- .map(|x| x * 2) transforms each element by multiplying it by 2.
- .collect() collects the transformed elements into a new Vec<i32>.
