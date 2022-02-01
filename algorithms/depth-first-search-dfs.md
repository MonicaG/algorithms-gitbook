# Depth First Search (DFS)

## Description

This algorithm is used to search or traverse a tree or graph. It explores as far as possible along  each branch before back tracking. Use this when you think the data you are looking for is far away from the starting node, rather than close to it. If you think it is close to it use a [breadth first search](breadth-first-search-bfs.md) instead.

Time complexity is O(V + E) where V = number of vertices and E = number of edges.

Space complexity is O(V). A stack (whether the call stack in the recursive solution or a stack defined in the logic in the iterative) is used to store the vertices to search, plus the structure to store the previously visited vertices.

## Graph DFS

Assume we have a graph described as follows:

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

### Recursive

Depth first search is a good candidate for recursion.

#### Search

Note: this search assumes the graph is a [connected graph](../data-structures/graph.md#connected-graph). If the graph is disconnected then you would need to search from each vertex in the graph to ensure you encountered all vertices.

```python
def dfs(graph: Dict, start: str, target: str, visited=None) -> bool:
    """
    Keep track of the vertices visited. If we come across a vertex that has not been processed, then iterate over its
    list of adjacent vertices. Recursively call the dfs function for each of the adjacent vertices.
    :param graph: A simple graph definition using a dict. The key is the vertex, the value is an array of adjacent vertices.
    :param start: The vertex to start searching at
    :param target: The vertex to find
    :param visited: Used by the recursion to mark which vertices we have already processed
    :return: True if the target is in the graph, false otherwise
    """
    if graph is None or start is None or target is None or start not in graph:
        return False
    # Why visited=None and this? See https://docs.python-guide.org/writing/gotchas/
    if visited is None:
        visited = {}
    if target == start:
        return True
    visited[start] = True
    for vertex in graph[start]:
        if vertex not in visited:
            return dfs(graph, vertex, target, visited)
    return False

```

#### Traversal

Walk a graph to find all the vertices. Note, this assumes a connected graph. For a disconnected graph, you would need to iterate through all the vertices to ensure you discovered all the nodes.

```python
def dfs_traverse(graph: Dict, start: str, visited=None, result=None) -> List[str]:
    if graph is None or start is None or start not in graph:
        return []
    if result is None:
        result = []

    if visited is None:
        visited = {}
    visited[start] = True
    for vertex in graph[start]:
        if vertex not in visited:
            result.append(vertex)
            dfs_traverse(graph, vertex, visited, result)
    return result

```

### Iterative

The iterative appoach uses a stack (replacing the call stack of the recursive solution). The logic of keeping track of the visited vertices and iterating through the list of adjacent vertices is similar to the recursive solution.

I've only implemented the traversal algorithm for the iterative approach. The search algorithm would be similar.

#### Traversal

```python
def dfs_traversal_iterative(graph: Dict, start: str) -> List[str]:
    if graph is None or start is None or start not in graph:
        return []

    result = []
    stack = []
    visited = {}
    stack.append(start)
    visited[start] = True
    while stack:
        item = stack.pop()

        if item not in visited:
            result.append(item)
            visited[item] = True

        # reversed is used here to give the same result as the recursive traversal. If reversed is not used, then the
        # algorithm would walk from last item in the adjacent vertices list to the first. This is because of the order
        # in which vertices are pushed onto the stack
        for vertex in reversed(graph[item]):
            if vertex not in visited:
                stack.append(vertex)

    return result

```



## Resources

* [https://en.wikipedia.org/wiki/Graph\_traversal](https://en.wikipedia.org/wiki/Graph\_traversal)
* [https://en.wikipedia.org/wiki/Depth-first\_search](https://en.wikipedia.org/wiki/Depth-first\_search)
