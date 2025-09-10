# Bit Manipulation

## Nth Bit is Set in a number

```go
func isNthBitSet(num, n int) bool {
    return ((num >> n) & 1) == 1
}
```

## Swap Two Numbers Using XOR

You can swap two integer variables without using a temporary variable by using XOR:

```go
func swap(a,b *int) {
    *a = *a ^ *b
    *b = *a ^ *b
    *a = *a ^ *b
}
```

// After these operations, the values of a and b are swapped.

## Is power of 2

```go
func isPowerOfTwo(uint32 n) bool {
    return n && !(n & (n - uint32(1)));
}
```

## Divisble by power of 2

```go
func isDivisibleByPowerOf2(n,k int) bool {
    powerOf2 := 1 << k
    return (n & (powerOf2 - 1)) == 0;
}
```

## Clear the right-most set bit

```go
n = n & (n-1)
```

## Count Set Bits in a number

```go
func countSetBits(int n) int {
    count := 0;
    for n > 0 {
        n = n & (n - 1)
        count+=1
    }
    return count;
}
```

## Check number polarity (even or odd)

```go
func isEven(int n) bool {
    return (n & 1) == 0
}

func isOdd(int n) bool {
    return (n & 1) == 1
}

```
