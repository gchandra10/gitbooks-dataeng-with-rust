# Expression

```
 // Expression

fn main() {
    let x = 5u32;

    let y = {
        //demonstrate with semicolons and without semicolon
        let x_squared = x * x;
        let x_cube = x_squared * x;

        // This expression will be assigned to `y`
        x_cube + x_squared + x
    };

    let z = {
        2 * x
    };
    
    let zz = {
        // The semicolon suppresses this expression and `()` is assigned to `z`
        2 * x;
    };

    println!("x is {:?}", x);
    println!("y is {:?}", y);
    println!("z is {:?}", z);
    println!("zz is {:?}", zz);
}
```
