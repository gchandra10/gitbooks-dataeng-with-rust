# Concurrency & Parallelism

Concurrency and parallelism are both about handling multiple tasks at the same time, but they approach the problem differently.

**Concurrency**

Definition: Concurrency is the ability of a program to manage multiple tasks at once. It doesn't necessarily mean these tasks are running at the same exact time, but that the system can handle multiple tasks in progress.

**Example:** Think of it as a chef preparing several dishes at once. The chef switches between tasks, chopping vegetables, stirring a pot, and checking the oven.

**Parallelism**

Definition: Parallelism is about executing multiple tasks simultaneously, typically on multiple CPU cores. This is a subset of concurrency where tasks are literally running at the same time.

**Example:** Imagine multiple chefs in a kitchen, each preparing a different dish at the same time.

## How It Works in Rust

**Concurrency in Rust**

Rust achieves concurrency through threads and async/await.

**Threads**: Rust's standard library provides native support for threads, which are the basic unit of concurrency. 

```rust
use std::thread;

fn main() {
    let handle = thread::spawn(|| {
        // This is the code that will run in a new thread.
        for i in 1..10 {
            println!("Hello from the spawned thread! {}", i);
        }
    });

    // Meanwhile, the main thread continues.
    for i in 1..5 {
        println!("Hello from the main thread! {}", i);
    }

    // Wait for the spawned thread to finish.
    handle.join().unwrap();
}
```

**Async/Await**: Rust's async/await syntax allows you to write asynchronous code that looks like synchronous code.

```
use tokio; // Using the Tokio async runtime

#[tokio::main]
async fn main() {
    let future1 = async_task();
    let future2 = async_task();

    // `join!` runs multiple futures concurrently
    tokio::join!(future1, future2);
}

async fn async_task() {
    // Some asynchronous work
    println!("Doing async work");
}
```

**Parallelism in Rust**

Rust achieves parallelism primarily through the Rayon library, which provides data parallelism through easy-to-use abstractions.

**Rayon**: Rayon makes it easy to parallelize data processing tasks.

**Key Points**

**Safety**: Rust ensures thread safety and data race prevention through its ownership and borrowing system.

**Ease of Use**: Libraries like Rayon and Tokio make it easier to work with concurrency and parallelism without delving too deep into low-level details.

```
git clone https://github.com/gchandra10/rust-concurrency-parallelism.git
```
