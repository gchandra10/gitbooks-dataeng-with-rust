# Cargo Publish

**Note: Once you publish a crate, there is no removal.**

Visit [https://crates.io/](https://crates.io/)

Login with GitHub

Verify the email address

Goto Account > API Settings and Generate a new token.

Create README.md at the same level as src folder

https://github.com/gchandra10/rust-epoch-to-human-lib


**Sample Libraries**

https://crates.io/crates/epoch_to_human

https://crates.io/crates/hello_lib


// Cargo Commands

cargo login <token>
cargo publish --dry-run

// git commands

git add Cargo.toml
git add README.md
git add src/lib.rs
git add .gitignore
git commit -m "Demo Crate"

// Publish

cargo publish
```
