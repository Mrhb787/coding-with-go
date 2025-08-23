# Tree Basics

## Undirected Tree (Simple Graph Representation)

```go
type Tree struct {
    adj map[int][]int // adjacency list
}

func NewTree() *Tree {
    return &Tree{adj: make(map[int][]int)}
}

func (t *Tree) AddEdge(u, v int) {
    t.adj[u] = append(t.adj[u], v)
    t.adj[v] = append(t.adj[v], u) // undirected
}
```

## Directed Tree (Rooted Tree)

```go
type Node struct {
    Value int
    Children []*Node // for general trees
}

func NewNode(val int) *Node {
    return &Node{Value: val}
}

// For binary trees:
type BinaryNode struct {
    Value int
    Left, Right *BinaryNode
}
```

## Tree Representation using Adjacency Matrix (2D Array)

You can represent a tree using a 2D slice (adjacency matrix) in Go. This is useful for small or dense trees.

```go
package main
import "fmt"

func main() {
    n := 5 // number of nodes
    adj := make([][]int, n)
    for i := range adj {
        adj[i] = make([]int, n)
    }

    // Add edges (undirected tree)
    edges := [][2]int{
        {0, 1},
        {0, 2},
        {1, 3},
        {1, 4},
    }
    for _, e := range edges {
        u, v := e[0], e[1]
        adj[u][v] = 1
        adj[v][u] = 1 // for undirected
    }

    // Print adjacency matrix
    fmt.Println("Adjacency Matrix:")
    for i := 0; i < n; i++ {
        fmt.Println(adj[i])
    }
}
```

- For a directed tree, only set `adj[u][v] = 1`.
- For an undirected tree, set both `adj[u][v]` and `adj[v][u]` to 1.
