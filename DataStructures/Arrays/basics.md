# Array Basics in Go

## Declaration

```go

// basic declaration
arr := []int{}

// nil declaration
var arr []int

// predefined size using make
arr := make([]int, n)
```

## Traversal

```go

// using range
for i, val := range arr {
    // i : index
    // val : arr[i]
}

// base for loop
for i := 0 ; i < len(arr) ; i++ {
    // val : arr[i]
}
```