# GCD (Greatest Common Divisor)

GCD (greatest common divisor), i.e. the largest number which is a divisor of both  $a$  and  $b$ .

## Recursive method

```go
func gcd(a,b int) int {
    if (b == 0) {
        return a;
    }
    return gcd (b, a % b);
}
```

## Iterative method

```go
func gcd(a,b int) int {
    for (b > 0) {
        a = a % b;
        a, b = b, a // swap
    }
    return a;
}
```

# Least Common Multiple


## 
```go
func gcd(a,b int) int {
    if (b == 0) {
        return a;
    }
    return gcd (b, a % b);
}

func lcm(a,b int) int {
    return a / gcd(a, b) * b;
}
```