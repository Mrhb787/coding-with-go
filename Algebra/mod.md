# Modulus

## Addition

```go
func addMod(a,b,mod int) int {
    return (a % mod + b % mod) % mod
}
```

## Subtraction

```go
func subtractMod(a,b,mod int) int {
    return (a % mod - b % mod + mod) % mod
}
```

## Multiply

```go
func multiplyMod(a,b,mod int) int {
    return (a % mod * b % mod) % mod
}
```