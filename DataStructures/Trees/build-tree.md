# Build a tree

```go

// build the tree from given nodes and edges
func buildTree(nodes int, edges [][]int) (tree [][]int) {

    tree = make([][]int, nodes)
    for i := range adj {
        tree[i] = make([]int, nodes)
    }

    for i := range edges {
        u, v := edges[i][0], edges[i][1]
        tree[u][v] = 1
        tree[v][u] = 1
    }

    return tree
}
```
