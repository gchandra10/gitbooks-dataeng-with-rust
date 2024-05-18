# Owner Borrower Stack Heap

```
// Owner - Borrower - Stack - Heap - Slices

fn main() {
    //Create a String Object o with the value Rachel Green

    let o = String::from("Rachel Green");
    println!("Value of the variable 'o' is {o}");

    // .len() - returns the actual length
    println!("\nString Length: {}", o.len());
    // .capacity() - memory reserved for String Object
    println!("String Capacity: {}", o.capacity());

    // as_ptr(): Returns a raw pointer to the underlying data in this cell.
    println!("Heap location of {o} starts at {:p}", o.as_ptr());

    ////////////

    //Slicing variable o and get the second portion of the variable, that is, Green
    let s = &o[7..12];

    println!("\nValue of the variable 's' is {s}");
    println!("Heap location of {s} starts at {:p}", s.as_ptr());

    // Get the stack location of variables o and s
    println!("\nStack location of owner 'o' {:p}", &o);
    println!("Stack location of owner 's' {:p}", &s);

    //////////

    // o is the owner, and b is the borrower.
    let b = &o;

    println!("\nBorrower 'b' is {}", b);
    println!("Borrower 'b' points to Owner 'o' {:p}", b);
    println!("Stack location of borrower 'b' {:p}", &b);
    println!("Value borrower 'b' pointing to 'o' location {:p}",b.as_ptr());
}
```
