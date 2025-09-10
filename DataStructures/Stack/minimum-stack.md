# Minimum Stack

A minimum stack is a special stack data structure that, in addition to standard stack operations (push, pop, top), can return the minimum element in constant time $O(1)$.

## Go Implementation

```go
// StackPair is a helper struct to store both the value and the minimum value
// found so far up to this point in the stack.
type StackPair struct {
	Value    int
	MinValue int
}

// MinStack is a stack that supports push, pop, top, and
// retrieving the minimum element in constant time.
type MinStack struct {
	Stack []StackPair
}

// Constructor initializes and returns a new MinStack.
func NewMinStack() *MinStack {
	return &MinStack{
		Stack: make([]StackPair, 0),
	}
}

// Push adds an element to the stack.
// It handles the special case of the first element and updates the MinValue
// for subsequent elements by comparing the new value with the current minimum.
func (ms *MinStack) Push(x int) {
	// If the stack is empty, the first element's MinValue is itself.
	if len(ms.Stack) == 0 {
		ms.Stack = append(ms.Stack, StackPair{Value: x, MinValue: x})
		return
	}

	// For subsequent elements, the MinValue is the minimum of the new value
	// and the previous MinValue from the top of the stack.
	currentMin := ms.Stack[len(ms.Stack)-1].MinValue
	ms.Stack = append(ms.Stack, StackPair{Value: x, MinValue: min(currentMin, x)})
}

// Pop removes and returns the top element from the stack.
func (ms *MinStack) Pop() (int, error) {
	if ms.IsEmpty() {
		return 0, fmt.Errorf("stack is empty")
	}
	// Get the value to be returned
	topValue := ms.Stack[len(ms.Stack)-1].Value
	// Reslice the stack to remove the top element.
	ms.Stack = ms.Stack[:len(ms.Stack)-1]
	return topValue, nil
}

// Top returns the value of the top element without removing it.
func (ms *MinStack) Top() (int, error) {
	if ms.IsEmpty() {
		return 0, fmt.Errorf("stack is empty")
	}
	return ms.Stack[len(ms.Stack)-1].Value, nil
}

// GetMin returns the minimum element in the stack.
// This operation is O(1) due to the precomputed MinValue in each StackPair.
func (ms *MinStack) GetMin() (int, error) {
	if ms.IsEmpty() {
		return 0, fmt.Errorf("stack is empty")
	}
	return ms.Stack[len(ms.Stack)-1].MinValue, nil
}

// IsEmpty checks if the stack is empty.
func (ms *MinStack) IsEmpty() bool {
	return len(ms.Stack) == 0
}
```
