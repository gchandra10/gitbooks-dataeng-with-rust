# Calculator

```
fn add(a: f32, b: f32) -> f32 {
    a + b
}

fn sub(a: f32, b: f32) -> f32 {
    if a < b {
        panic!("first value cannot be less than the second value");
    } else {
        a - b
    }
}

#[allow(dead_code)]
fn mul(a: f32, b: f32) -> f32 {
    a * b
}

#[allow(dead_code)]
fn div(a: f32, b: f32) -> f32 {
    a / b
}

fn main() {
    let a: f32 = 17.0;
    let b: f32 = 33.0;
    let op = "-";
    let mut result: f32 = 0.0;

    if op == "+" {
        result = add(a, b);
    } else if op == "-" {
        result = sub(a, b)
    }

    println!("{result}");
}

#[test]
fn test_add() {
    assert!(add(20.0, 10.0) == 30f32);
}

#[test]
fn test_add1() {
    assert!(add(10.0, 20.0) == 30f32);
}

#[test]
#[should_panic(expected = "cannot be less")]
fn test_sub() {
    assert!(sub(10.0, 20.0) == -10.0f32);
}

#[test]
fn test_sub1() {
    assert!(sub(20.0, 10.0) == 10.0f32);
}

#[test]
#[ignore]
fn test_sub2() {
    assert!(sub(20.0, 10.0) == 10f32);
}

```

### How to Test the code

```
cargo test
```

### How to Run the code

```
cargo run
```
