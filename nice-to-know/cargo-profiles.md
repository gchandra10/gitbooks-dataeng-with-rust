# Cargo Profiles

Profiles provide a way to alter the compiler settings, influencing things like optimizations and debugging symbols.

Cargo has 4 built-in profiles

* dev
* release
* test
* bench

[https://doc.rust-lang.org/cargo/reference/profiles.html](https://doc.rust-lang.org/cargo/reference/profiles.html)\


```
[profile.dev]
opt-level = 0
debug = true
debug-assertions = true
overflow-checks = true
incremental = true


[profile.release]
opt-level = 3
debug = false
debug-assertions = false
overflow-checks = false
incremental = false
```

**Custom Profiles**

```
// 

[profile.release-panic]
inherits = 'release'
panic = 'abort'
```

The specifications are selected based on the type of build.

```
// dev profile is chosen
cargo build  

//release profile is chosen
cargo build --release

//Custom Profile
cargo build --profile release-panic
```

