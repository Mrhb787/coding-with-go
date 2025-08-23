# DFS (Depth first search)

DFS (Depth-First Search) is a way to visit all nodes in a tree or graph by going as deep as possible along each branch before backtracking.

- Start at the root (or any node).
- Visit a node, then recursively visit its children (or neighbors) one by one.
- If you reach a node with no unvisited children, go back (backtrack) and continue with the next child.

DFS can be implemented using recursion or a stack. It’s useful for exploring all paths, finding connected components, and solving puzzles like mazes.

## Implementations

### Recursive

```go
func dfs(currentNode int, parentNode int, graph [][]int, visited []bool) {

    // mark current node as visited
    // to avoid infinite traversal
    // for an undirected graph
    visited[currentNode] = true

    // traverse the child
    for _, child := range graph[currentNode] {
        if child != currentNode && !visited[child] {
            dfs(child, currentNode, graph, visited)
        }
    }
}
```

### Iterative

```go
func dfs(start int, graph [][]int, visited []bool) {
    stack := []int{start}
    for len(stack) > 0 {
        node := stack[len(stack)-1]
        stack = stack[:len(stack)-1]
        if visited[node] {
            continue
        }
        visited[node] = true
        for _, neighbor := range graph[node] {
            if !visited[neighbor] {
                stack = append(stack, neighbor)
            }
        }
    }
}
```
