# Cargo Example

```
cargo new osinfo

cd osinfo
```

Replace the main.rs code with the code given below

```
// Rust sample for displaying OS Info

fn main() {
    println!("Hello, world!");

    let info = os_info::get();

    // Print full information:
    println!("OS information: {}", info);

    // Print information separately:
    println!("Type: {}", info.os_type());
    println!("Version: {}", info.version());
    println!("Bitness: {}", info.bitness());
}

```

Run the following statements

```
cargo check

cargo fetch

cargo build
```

check the executable under target/debug

```
cargo build --release
```

check the executable under target/release

The release executable will be smaller in size than debug executable.

Because, debug contains symbols & backtraces

