# Vector - Struct - Input

```rust
use std::io;

#[derive(Debug)]
struct User {
    id: String,
    first_name: String,
    last_name: String,
    status: String,
}

fn main() {
    let mut users: Vec<User> = Vec::new();

    loop {
        println!("Enter 'id', 'first name', 'last name', 'status' separated by SPAC:");
        let mut input = String::new();
        io::stdin().read_line(&mut input).unwrap();
        let parts: Vec<&str> = input.trim().split_whitespace().collect();

        if parts.len() != 4 {
            println!("Invalid input. Please enter 4 values.");
            continue;
        }

        let new_user = User {
            id: parts[0].to_string(),
            first_name: parts[1].to_string(),
            last_name: parts[2].to_string(),
            status: parts[3].to_string(),
        };

        users.push(new_user);

        println!("Do you want to add another user? (Yes/No/Y/N): ");
        let mut continue_input = String::new();
        io::stdin().read_line(&mut continue_input).unwrap();

        if continue_input.trim().eq_ignore_ascii_case("n") || continue_input.trim().eq_ignore_ascii_case("no")  {
            break;
        }
    }

    println!("\nAll users:");
    for user in users {
        println!("{},{},{},{}", user.id, user.first_name, user.last_name, user.status);
    }
}
```
