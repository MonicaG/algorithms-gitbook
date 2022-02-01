# Graph

## Description

A graph is a data structure that represents how data is connected. Think of a social network like FaceBook or Twitter.

## Graph terminology

* Vertex - a node
* Edge - the connection (line) between two vertices.
* Adjacent - Vertices connected by an edge are "adjacent" to each other.

## Types of graphs

### Connected Graph

A graph where all vertices are connected to each other in some way. Otherwise it is a disconnected graph.

![A connected graph. All vertices are connected to each other in some way](../.gitbook/assets/connected\_graph.svg)



![A disconnected graph. Here Fred is not connected to any other vertex.](../.gitbook/assets/disconnected\_graph.svg)

### Directed graph&#x20;

The edges indicate the direction of the relationship.&#x20;



![A connected, directed graph. Attribution: https://commons.wikimedia.org/wiki/File:Directed.svg](https://upload.wikimedia.org/wikipedia/commons/a/a2/Directed.svg)

### Weighted Graph

A number (weight) is assigned to each edge. These numbers could represents things such as distance, or costs, or whatever is appropriate for the problem. Weighted graphs are used in shortest path problems such as the traveling salesman problem.

Dijkstra's Algorithm is a famous algorithm to solve the shortest path problem.

![Attribution: Tore.opsahl, Public domain, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/9/9a/Weighted\_network.png)

## Tree vs Graph

A tree is a type of graph. All trees are graphs, but not all graphs are trees.

The difference between a tree and a graph is:

* A graph may have vertices (nodes) that are not connected.&#x20;
* A graph my contain cycles

## Algorithms

See[ DFS](../algorithms/depth-first-search-dfs.md) and [BFS](../algorithms/breadth-first-search-bfs.md) for algorithms to traverse/search a graph.

