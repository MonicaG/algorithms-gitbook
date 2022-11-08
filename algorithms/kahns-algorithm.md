# Kahn's Algorithm

## Topological Sort

A topological sort is a graph traversal where each node is visited only after all its dependencies have first been visited.&#x20;

Topological sorting is used where things need to be scheduled based on their dependencies. For example, course schedules. A student needs to take CS101 before they can take CS201, and they need to take CS201 before they can take CS301. Other areas of applications are build programs in CS (a program's dependencies need to be built in a certain order), event scheduling, assembly instructions etc.

There can be more than one valid topological sort. In the following graph the following topological sorts are possible:

* A B C D
* A C B D
* A C D B

<figure><img src="../.gitbook/assets/Acyclic graph.png" alt=""><figcaption><p>Directed Acyclic Graph</p></figcaption></figure>

A topological sort is only possible on a [directed acyclic graph (DAG)](../data-structures/graph.md#directed-acyclic-graph-dag). This is because if the graph contained a cycle, then a sort order cannot be found. For example, in the following graph, C depends on A and B. But B depends on D which depends on C. C depends on a dependency (D) which depends on C! So, it is invalid.

<figure><img src="../.gitbook/assets/Cyclic graph.png" alt=""><figcaption><p>A graph which contains a cycle. A topological sort is not possible</p></figcaption></figure>

## Kahn's Algorithm

Kahn's Alogorithm finds a topological sort of a [DAG](../data-structures/graph.md#directed-acyclic-graph-dag). It works by repeatedly removing vertices that have no incoming edges. Those removed vertices are recorded to the topological sort set/array.

In the above DAG graph, vertex A is the only vertex with no incoming edges. It is the starting point for the algorithm. It is removed and put in the topological sort set. Now, B and C vertices have no incoming edges. One is picked arbitrarily to process. Say B. B is removed to the topolgoical sort set. Now C is the only vertice without any incoming edges. C is removed. And finally D. The topological sort in this example is A, B, C, D.

The code below is a simple implementation of Kahn's algorithm. It assumes the vertices value are integers in the range of 0...number of vertices. This allows for an array to track the number of incoming edges for each vertex.

{% code lineNumbers="true" %}
```python
'''
Kahn's algorithm - used for finding a topological sort (ordering) of a directed acyclic graph.
'''
from typing import List
from collections import defaultdict, deque


class Graph:

    __MIN_VALUE__ = 0
    
    def __init__(self, num_vertices):
        self.graph = defaultdict(list)
        self.num_vertices = num_vertices

    def __is_valid__(self, num: int) -> bool:
        return num >= Graph.__MIN_VALUE__ and num < self.num_vertices

    def add_edge(self, u: int, v: int):
        '''
        Add an edge from vertex u to vertex v
        '''
        if not self.__is_valid__(u) or not self.__is_valid__(v):
            raise Exception(f"Invalid vertex value. Must be between {Graph.__MIN_VALUE__}  and {self.num_vertices}")
        self.graph[u].append(v)

    def add_non_connected_vertex(self, u):
        self.graph[u].append(None)



class Kahns:
   def kahn(self, graph: Graph) -> List[int]:
        # this array keeps track of how many edges are incoming to a vertex (how many dependecies a course has)
        # because the vertices ints an array can be used. The array index is the vertex int
        incoming_edges = [0] * graph.num_vertices

        # populate the incoming_edges with the number of incoming edges for each vertex
        for u in graph.graph:
            for v in graph.graph[u]:
                if v:
                    incoming_edges[v] += 1


        # initialize the queue with any vertices that do NOT have any incoming edges (0 dependencies)
        processing_queue = deque()
        for vertex, edges in enumerate(incoming_edges):
            if edges == 0:
                processing_queue.append(vertex)

       
        topo_sort = []
        num_vertices_processed = 0
        while processing_queue:
            vertex = processing_queue.pop()
            num_vertices_processed += 1
            topo_sort.append(vertex)
            for v in graph.graph[vertex]:
                if v:
                    incoming_edges[v] -= 1
                    if incoming_edges[v] == 0:
                        processing_queue.append(v)

        # The graph contains a cycle if these two values do not match
        if num_vertices_processed != graph.num_vertices:
            raise Exception("Invalid graph")
        return topo_sort

```
{% endcode %}
