## Square root Roundoff

For general $x$, the square root must lie in range 
$[1,x]$ (actually $[1,x/2]$ for $x≥2$, since
$x≤x/2$ when $x≥4$).

```go

func sqrt(x int) int {
    if x < 2 {
        return x
    }

    left, right := 1, x/2
    ans := 0
    for left <= right {
        mid := left + (right-left)/2
        square := mid * mid

        if square == x {
            return mid
        } else if square < x {
            ans = mid
            left = mid + 1
        } else {
            right = mid - 1
        }
    }

    return ans
}
```
