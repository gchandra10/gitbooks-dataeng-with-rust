# Big O Notation

## Algorithmic Complexity

When analyzing an algorithm,

**Time Complexity**: The time it takes to execute the code.

**Space Complexity**: The space taken in the memory to execute the code.


Following Notations are used to represent Algorithmic Complexity. Big O is what everybody is interested in.

Big - Omega = Best Case

Big - Theta = Average Case

**BIG O = Worst Case**

<figure><img src="../../assets/00_common_complexities.png" alt=""><figcaption></figcaption></figure>

Will try to use general algorithms not any specific programming syntaxes.

**Constant or Static Complexity - O(1)**

```
// Constant / Static

print("Enter Name:")
cen = (f - 32) * 1.8;
far = (cen * 1.8) + 32;
print (cen, far);
```

Each line is of complexity O(1). Because its handling only one item.

4 \* O(1)&#x20;

**While finding the pattern we ignore the constant values.**&#x20;

So we remove 4 and the complexity is O(1)

## Linear Complexity O(N)

In this case the time and size changes based on number of input values.

For example

```
// Linear Complexity

for i = 1 to N
print (i)
```

if N = 10 it will be print faster, if N = 1Million the time taken will be linear.

These kinds of Linear changes is called  O(N)

## Quadratic Complexity

```
// Quadratic Complexity

for i = 1 to N
    for j = 1 to M
        print (i,j)   

```

For every i, there is another loop called j

N \* N =  O(N Square)

If  N = 2 then the process will iterate  4 times.&#x20;

### What is the Complexity of these ?

```
//
for i = 1 to n
print (i)

for j = 1 to n
print (j)
```

```
// 
for i = 1 to N
    for j = 1 to M
        for k = 1 to 1000
            print (i,j,k)
        
```

```
// 
for (i = 0; i < N; i++) {
    for (j = 0; j < N; j++) {
        sequence of statements
    }
}
for (k = 0; k < N; k++) {
    sequence of statements
}
```

## Exponential Complexity

O(2 power N)

With the increase in input there is an exponential growth in Time and Space.

Typical example :&#x20;

```
// Some code

function fibonacci(n){
    if n = 0 return 0
    if n = 1 return 1
    else
    return fibonacci(n - 2) + fibonacci(n - 1)
```

For example

For input = 3, number of iteration is 4   2 power n-1

For input = 4, number of iteration is 8&#x20;

```
                                            Fibonacci(3)

                         Fibonacci(1)                            Fibonacci(2)

                                                    Fibonacci(0)         Fibonnaci(1)
```

## Logarithmic Complexity  O(Log N)

Increase in number of input is exponential but time and space growth is Linear.

```
for (i= 1; i< n; i = i **2)
    print(i)
```

or Binary Search

1  23  45  56  89  90  110  130

Pick mid point, search either left or right.



<figure><img src="../../assets/big-o-complexity-chart.png" alt=""><figcaption><p>bigocheatsheet.com</p></figcaption></figure>



Fore more visit

https://bigocheatsheet.com

