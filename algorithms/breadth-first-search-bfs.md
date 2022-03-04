# Breadth First Search (BFS)

This algorithm is used to search or traverse a tree or graph. It explores all nodes at the current depth before moving on to nodes a the next level. Use this when you think the data you are looking for is close to the starting node, rather than far away from it. If you think it is far away use a [depth first search](depth-first-search-dfs.md) instead.

An iterative approach using a queue to keep track of the nodes to explore is generally used.

Time Complexity: O(V + E) where V is the number of verticies and E is the number of edges.

Space Complexity: O(V)

## Graph

Assume the following graph:

```python
 graph = {
        "A": ["B", "C", "D"],
        "B": ["A", "D", "E"],
        "C": ["A", "F"],
        "D": ["B", "D"],
        "E": ["B", "F"],
        "F": ["C", "E", "G"],
        "G": ["F"],
    }
```

![A visual depiction of the graph](../.gitbook/assets/graph\_example.svg)

A collections.deque is used to queue the vertices to search. The code is similar to the iterative implementation of the [depth first search ](depth-first-search-dfs.md#iterative)algorithm.&#x20;

### Traversal

```python
def bfs_traversal(graph: Dict, start: str) -> List[str]:
    if graph is None or start is None or start not in graph:
        return []
    result = []
    queue = deque()
    visited = {}
    queue.append(start)
    visited[start] = True
    while queue:
        item = queue.popleft()
        for vertex in graph[item]:
            if vertex not in visited:
                visited[vertex] = True
                queue.append(vertex)
                result.append(vertex)
    return result

```

### Search

```python
def bfs(graph: Dict, start: str, target: str) -> bool:
    if graph is None or start is None or target is None or start not in graph:
        return False
    if start == target:
        return True
    queue = deque()
    visited = {}
    queue.append(start)
    visited[start] = True
    while queue:
        item = queue.popleft()
        for vertex in graph[item]:
            if vertex == target:
                return True
            if vertex not in visited:
                visited[vertex] = True
                queue.append(vertex)
    return False

```

## Tree

### Traversal

Traversal of a tree is similar to a graph except the visited collection is not needed. This is because a tree does not have cycles in it. So, we do not need to keep track of the nodes we have already visited.

```python
class TreeNode(object):
    def __init__(self, x):
        self.val = x
        self.left = None
        self.right = None


def bfs_traversal(root: TreeNode) -> List[int]:
    if not root:
        return []
    queue = deque()
    queue.append(root)
    result = []
    while queue:
        node = queue.popleft()
        if node:
            result.append(node.val)
            queue.append(node.left)
            queue.append(node.right)
    return result
```

## Resources

* [https://en.wikipedia.org/wiki/Graph\_traversal#Breadth-first\_search](https://en.wikipedia.org/wiki/Graph\_traversal#Breadth-first\_search)
* [https://en.wikipedia.org/wiki/Breadth-first\_search](https://en.wikipedia.org/wiki/Breadth-first\_search)
