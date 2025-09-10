# Stack

A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle. The last element added is the first one to be removed.

**Main operations:**

- `Push`: Add an element to the top of the stack
- `Pop`: Remove the top element
- `Peek`/`Top`: View the top element without removing it
- `IsEmpty`: Check if the stack is empty

## Stack Implementation in Go (using slice)

```go
type Stack[T any] []T

// Push adds an element to the top of the stack
func (s *Stack[T]) Push(item T) {
	*s = append(*s, item)
}

// Pop removes and returns the top element of the stack
func (s *Stack[T]) Pop() (T, bool) {
	if s.IsEmpty() {
		var zero T
		return zero, false
	}
	index := len(*s) - 1
	item := (*s)[index]
	*s = (*s)[:index]
	return item, true
}

// Peek returns the top element without removing it
func (s *Stack[T]) Peek() (T, bool) {
	if s.IsEmpty() {
		var zero T
		return zero, false
	}
	return (*s)[len(*s)-1], true
}

// IsEmpty checks if the stack is empty
func (s *Stack[T]) IsEmpty() bool {
	return len(*s) == 0
}
```

## Usage

```go

// Example usage of Stack[int]
func main() {
	var s Stack[int]
	s.Push(10)
	s.Push(20)
	s.Push(30)

	top, _ := s.Peek()
	fmt.Println("Top element:", top) // Output: 30

	for !s.IsEmpty() {
		val, _ := s.Pop()
		fmt.Println("Popped:", val)
	}
	// Output: Popped: 30, Popped: 20, Popped: 10
}
```
