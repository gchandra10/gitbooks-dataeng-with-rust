# Terminologies

**Rustacean**: A person who codes in Rust.



**Cargo** - Rust package management tool.



**Crates** - A crate is a compilation unit in Rust. Whenever `rustc some_file.rs` is called, `some_file.rs` it is treated as the _crate file_.

Crates can be compiled into a binary file or a library.

www.crates.io - Official Rust package registry.



**Lint:** This tool analyzes code to catch possible errors, enforce coding guidelines, or highlight areas where the code could be improved.



**Attributes -**  It is the metadata applied to your code.

Used for&#x20;

* Conditional Compilations
* Disable Lits (Warnings)
* Link to foreign libraries
* Mark functions as Unit Tests

and so on...

\#\[allow(unused\_variables, unused\_mut)]



**Clippy** - A collection of **lints** to catch common mistakes and improve your _Rust_ code.

(Remember **pylint** for Python or **cppcheck** for c++)

**Rustfmt** - Tool reformats your code according to the community coding style.

(**pep8** for Python or **clang-format** for c++)

