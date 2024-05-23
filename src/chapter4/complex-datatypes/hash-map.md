# Hash Map

A HashMap is a data structure that provides a highly efficient way to store and retrieve key-value pairs. It's often used when you need to associate unique keys with specific values and want fast access to the values based on their keys.

- Data type to store data in Key - Value pair.

- Keys are used to looking up corresponding values.

- Hashing: The keys are processed through a hash function, which converts the key into an index (or hash code) that determines where the key-value pair is stored in the underlying array.
  
- Dynamic Resizing: HashMap dynamically resizes its internal array to maintain performance as the number of elements grows.

- Non-Sequential: The order of elements in a HashMap is not guaranteed to be the same as the order in which they were inserted. The order is determined by the hash codes of the keys.

---

Example: Phone book - Search for the name and get the phone number

Under the hood, a hash function determines how to store data so the value can be quickly located.

In other languages, we have a similar feature.

Map / Dictionary / Associative Array

**Rules**

* All values must have the same data type.
* Each key can only have one value associated with it at a time.
* No duplicate keys.

```rust

## What is Hashing??

Hashing is a process of transforming any given input (such as a string or a file) into a fixed-size string of characters, which is typically a sequence of numbers and letters.

Fixed-Size Output: No matter the size of the input, the output (called the hash value) will always have a fixed size.

Uniqueness: Ideally, different inputs should produce different hash values, although collisions (where two different inputs produce the same hash value) can happen.

Efficiency: Hashing is designed to be fast and efficient, making it useful for quick data retrieval.



### Example

```rust
use std::collections::hash_map::DefaultHasher;
use std::hash::{Hash, Hasher};

fn main() {
    let s = "hello world";

    // Create a hasher
    let mut hasher = DefaultHasher::new();

    // Hash the string
    s.hash(&mut hasher);

    // Get the resulting hash as a u64
    let hash_value = hasher.finish();

    println!("Hash value for '{}': {}", s, hash_value);
}
```

## HashMap

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);
   
    println!("cities is {:?}", cities);
}
```

### Insert

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);
   
    println!("cities is {:?}", cities);

    //Option 1 - Insert / Overwrite Existing Value

    cities.insert("Paulsboro", 11000);
    cities.insert("Glassboro", 31000);

	println!("cities is {:?}", cities);
}
```

### Insert/Update/Get

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);
    
    //Option 1 - Update / Overwrite Existing Value
    cities.insert("Glassboro", 31000);
    
    //Option 2 - Insert a new entry if it doesn't exist
    cities.entry("Depford").or_insert(12000);
    
    //Option 3 - Get the value of the Key and perform a mathematical operation
    let gpopulation = cities.entry("Glassboro").or_insert(0);
    *gpopulation += 1;
    
    //print the hash map values. The print order may or may not be the same
    //as the insert. It changes from time to time.
    println!("cities is {:?}", cities);

    let glassboro_population = cities.get("Glassboro");
    
    if glassboro_population.is_some(){
        println!("glassboro_population is {:?}", glassboro_population);
    }
    else if glassboro_population.is_none(){
        println!("glassboro_population is not available", );
    }
}
```

### Remove

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);

    // Remove an entry
    cities.remove("Mullicahill");

    println!("After removal: {:?}", cities);
}
```

### Iterating Over the HashMap

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);

    // Iterating over the HashMap
    for (city, population) in &cities {
        println!("The population of {} is {}", city, population);
    }
}
```
### Check for Existence

```rust
use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);

    // Checking if a key exists
    if cities.contains_key("Swedesboro") {
        println!("Swedesboro is in the HashMap");
    } else {
        println!("Swedesboro is not in the HashMap");
    }
}
```

### Merge

```rust
use std::collections::HashMap;

fn main() {
    let mut cities1 = HashMap::new();
    cities1.insert("Glassboro", 30000);
    cities1.insert("Mullicahill", 25000);

    let mut cities2 = HashMap::new();
    cities2.insert("Swedesboro", 28000);
    cities2.insert("Depford", 12000);

    // Merging two HashMaps
    for (city, population) in cities2 {
        cities1.insert(city, population);
    }

    println!("Merged cities: {:?}", cities1);
}
```








