# Cargo dependency versions

While specifying the dependency version, you can either specify the exact one or mention the bottom range number.

Here are some more examples of version requirements and the versions that would be allowed with them:

You can mention the number given on the left-hand side instead for the range of versions given on the right-hand side.

```

1.2.3  :=  >=1.2.3, <2.0.0
1.2    :=  >=1.2.0, <2.0.0
1      :=  >=1.0.0, <2.0.0

0.2.3  :=  >=0.2.3, <0.3.0
0.2    :=  >=0.2.0, <0.3.0
0.0.3  :=  >=0.0.3, <0.0.4
0.0    :=  >=0.0.0, <0.1.0
0      :=  >=0.0.0, <1.0.0

//example using wildcards

*     := >=0.0.0
1.*   := >=1.0.0, <2.0.0
1.2.* := >=1.2.0, <1.3.0

// Comparison requirements

>= 1.2.0
> 1
< 2
= 1.2.3

// Multiple dependencies separated by comma

This means the version should be greater than or equal to 1.2 and less than 1.5

>= 1.2,  < 1.5
```

In the previous example (Cargo Example - 2), instead of mentioning

os-info = "3.5.0" we have mentioned&#x20;

os-info = "3"&#x20;



**Using crate.io repositories**

```
// Some code

[dependencies]
regex = { git = "https://github.com/rust-lang/regex" }

```
