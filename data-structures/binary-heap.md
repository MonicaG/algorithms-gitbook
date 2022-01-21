# Binary Heap

A binary heap can be used as a priority queue, as the highest (or lowest) value node is always at the root of the tree.

## Types of Heaps

### max-heap

The value of each node is greater than all of its descendants

[![Max-Heap-new](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Max-Heap-new.svg/256px-Max-Heap-new.svg.png)](https://commons.wikimedia.org/wiki/File:Max-Heap-new.svg)

### min-heap

The value of each node is less than all of its descendants

[![Binary Heap with Array Implementation](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c4/Binary\_Heap\_with\_Array\_Implementation.JPG/512px-Binary\_Heap\_with\_Array\_Implementation.JPG)](https://commons.wikimedia.org/wiki/File:Binary\_Heap\_with\_Array\_Implementation.JPG)

## Heap Rules

1. Follow its heap condition (either max-heap or min-heap)
2. The tree must be complete
   1. It must not have any empty node positions. Although the bottom row can have empty positions. But there cannot be any nodes to the right of those empty nodes.

Example of incomplete heap (the 36 does not have a left child)

![Incomplete Heap](../.gitbook/assets/incomplete\_heap.svg)

## Heap properties

* Heaps are weakly ordered.
  * It's not ordered like a binary search tree where values less than a node are on the left branch, and values greater than the node are on the right branch.
  * We only know that the descendant nodes are smaller than a given node in a max-heap. And vice versa for a min-heap.
* In a max-heap, the greatest value will always be at the root node. In a min-heap the smallest value will be at the root node.

## Implementation

* Heaps are usually implemented as an array. This makes it easy to keep track of the root node and the last node in the 'tree'. The root node is the first element of the array. The last node is the last element of the array.
* The first two diagrams above show how the heap is represented in the array.
* To find the left child of a node:
  * (index \* 2) + 1
* To find the right child of a node:
  * (index \* 2) + 2
* To find the parent of a node:
  * (index - 1) / 2
    * Note: the above does integer division, so the remainder is thrown away

## Primary Operations

### Insertion

These steps are for a max-heap. Min-heap follows the same steps except a min comparison is done instead.

1. A new node is inserted into the last node
2. The new node is compared to its parent node
3. If the new node is greater than its parent, swap the nodes
4. repeat steps 2 - 3 until it has a parent that has a greater value than it.

### Deletion

These steps are for a max-heap. Min-heap follows the same steps except a min comparison is done instead.

**Important:** We only ever delete the root node.

1. Replace the root node with the last node
2. Trickle the root node down to its proper place
   1. Check both children of the trickle down node to see which one is bigger
   2. If the trickle node is smaller than the larger of the two child nodes, then swap the trickle node with the larger child
   3. repeat above two steps until the trickle node has no descendants that have a greater value than it

By repeatedly popping the root element, we get the list in sorted order (descending). It will be in ascending order for a min-heap.
