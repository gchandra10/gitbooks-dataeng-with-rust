# Type Alias

A _type alias_ defines a new name for an existing type. Type aliases are declared with the keyword `type.`

Point to remember

The first letter of the type should be in upper case.

```
// type alias

type Bannertype = u32;

fn main() {
    let mut id: Bannertype = 91615214;
    println!("{id}");
    id = 91615200;
    println!("{id}");
}
```
