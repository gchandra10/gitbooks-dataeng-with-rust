---
description: Tom's Obvious Minimal Language
---

# Cargo.toml

TOML is  Open Source, and case sensitive.

TOML aims to be a minimal configuration file format that’s easy to read due to precise semantics. TOML should be easy to parse into data structures in various languages.

* TOML is case-sensitive.
* A TOML file must contain only UTF-8 encoded Unicode characters.
* Whitespace means tab (0x09) or space (0x20).
* Newline means LF (0x0A) or CRLF (0x0D0A).



`Cargo.toml` is a [**manifest**](https://doc.rust-lang.org/cargo/appendix/glossary.html#manifest) file in which we can specify different metadata about our package.

Manifest: Description of a package.&#x20;

```
// Sample

[package]
name = "osinfo"
version = "0.1.0"
edition = "2021"

# See more keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

[dependencies]
os_info = "3"
```

```
// Some code

[package]
name = "hello_world"
version = "0.1.0"

[dependencies]
regex = { git = "https://github.com/rust-lang/regex.git" }


Alternatively, aa specific revision can be mentioned under dependency

[dependencies]
regex = { git = "https://github.com/rust-lang/regex.git", rev = "9f9f693" }


```
