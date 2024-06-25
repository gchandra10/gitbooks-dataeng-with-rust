# Cargo Publish

**Note: Once you publish a crate, there is no removal.**

Visit [https://crates.io/](https://crates.io/)

- Login with GitHub
- Verify the email address
- Goto Account > API Settings and Generate a new token.

[Epoch to human](https://github.com/gchandra10/rust-epoch-to-human-lib)


**Sample Libraries**

[Epoch to Human](https://crates.io/crates/epoch_to_human)

[Hello Lib](https://crates.io/crates/hello_lib)

```
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
