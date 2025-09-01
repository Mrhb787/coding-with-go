# Binary Exponentiation

Raising $a$  to the power of $n$  efficiently.

## Reference

[Binary Exponentation](https://cp-algorithms.com/algebra/binary-exp.html)

## Code

### Iterative Method

```go
func power(a, b int64) (res int64) {
    res = 1;
    for b > 0 {
        if b & 1 == 1 {
            res = res * a;
        }
        a = a * a;
        b = b >> 1;
    }
    return res;
}
```

### Iterative Method With Mod

```go
func power(a, b, mod int64) (res int64) {
    a = a % mod
    res = 1;
    for b > 0 {
        if b & 1 == 1 {
            res = res * a % mod;
        }
        a = a * a % mod;
        b = b >> 1;
    }
    return res;
}
```

## Time Complexity

$O(\log n)$

We have to compute $\log n$  powers of $a$ , and then have to do at most $\log n$  multiplications to get the final answer from them.

## Miscellaneous

$a^{10x+y} = (a^x)^{10} \cdot a^y$