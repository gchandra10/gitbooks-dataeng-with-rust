# Cargo Watch

This enables dynamic compilation as soon as the project is saved. This helps to save compilation time.

Goto command prompt or terminal and&#x20;

```
// How to install Cargo Watch

cargo install cargo-watch

```

Goto respective project

Dynamic Build

```
cargo watch -x check
```

Dynamic Build and Run

```
cargo watch -x check -x run
```

Dynamic Build, Run and Test

```
cargo watch -x check -x run -x test
```
