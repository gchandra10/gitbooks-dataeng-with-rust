# Control Cargo Tests

### To test all the Test Cases

```
cargo test
```

### Test Arguments

```
cargo test [arguments1] -- [arguments2]

>arguments1 are the arguments for test utility like  help

cargo test --help

>arguments2 are the arguments for the application it's testing.


```

By default, cargo displays detailed output for failed test cases. To see the standard output for Success or Failure tests

```
// Some code

cargo test -- --show-output

Make sure there is no space between --show-output 
```

### Parallel Test Execution

By default, tests run in parallel by making use of the multi-core architecture.

In some situations (like file handling) there will be a race condition. To avoid that we can make them execute in sequential.

```
// Runs on single thread

cargo test -- --test-threads=1
```

Run test by name

```
cargo test <testname>

or

cargo test <string> 

cargo runs all tests containing the string in test name.
```

### Ignore specific tests

```
// Some code

#[test]
#[ignore]

adding this will ignore the test
```

### Run ignored tests only

```
cargo test -- --ignored
```
