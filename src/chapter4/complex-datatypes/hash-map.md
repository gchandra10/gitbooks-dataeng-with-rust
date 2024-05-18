# Hash Map

Data type to store data in Key - Value pair.

Keys are used to looking up corresponding values.

Example: Phone book - Search for the name and get the phone number

Under the hood, a hash function determines how to store data so the value can be quickly located.

In other languages, we have a similar feature.

Map / Dictionary / Associative Array

**Rules**

* All values must have the same data type.
* Each key can only have one value associated with it at a time.
* No duplicate keys.

```
// HashMap

use std::collections::HashMap;

fn main() {
    let mut cities = HashMap::new();
    cities.insert("Glassboro", 30000);
    cities.insert("Mullicahill", 25000);
    cities.insert("Swedesboro", 28000);
    
    //Option 1 - Update / Overwrite Existing Value
    //cities.insert("Glassboro", 31000);
    
    //Option 2 - Insert a new entry if it doesn't exist
    //cities.entry("Depford").or_insert(12000);
    
    //Option 3 - Get the value of the Key and perform a mathematical operation
    //let gpopulation = cities.entry("Glassboro").or_insert(0);
    //*gpopulation += 1;
    
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
