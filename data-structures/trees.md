# Trees

## Properties of a Tree

* A tree is a node based data structure.&#x20;
* Each node can have links to multiple other nodes&#x20;
  * Compare this to a singly [linked list](linked-list.md) which can only link to the next node or a double linked list which can only link to the previous and next nodes.
* All the nodes in a tree must be connected
* There cannot be any cycles in a tree (i.e. two nodes cannot link to the same child node)
* A tree is balanced when the following 3 conditions are met:
  * The left and right subtrees heights differ by at most 1
  * The left subtree is balanced
  * The right subtree is balanced
* A tree is perfectly balanced when the left and right subtrees of any node are the same height.

![Example of a tree. This is NOT a binary tree as the 7 node has three child nodes. This is an imbalanced tree. Attribution: Paddy3118, CC BY-SA 4.0 https://creativecommons.org/licenses/by-sa/4.0, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/5/5f/Tree\_\(computer\_science\).svg)

![Example of a balanced binary tree. Attribution: User:Mikm, Public domain, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/0/06/AVLtreef.svg)

## Binary Tree

A binary tree is a tree where each node can have zero, one or two children.

![Unbalanced and not sorted binary tree. Attribution: Radke7CB, CC BY-SA 4.0 https://creativecommons.org/licenses/by-sa/4.0, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/5/5e/Binary\_tree\_v2.svg)

## Binary Search Trees

A binary search tree is a binary tree that has these properties:

* Each node can have at most one left and one right child
* The left descendants must only contain values that are less than the node
* The right descendants must only contain values that are greater than the node

[![Binary search tree](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary\_search\_tree.svg/256px-Binary\_search\_tree.svg.png)](https://commons.wikimedia.org/wiki/File:Binary\_search\_tree.svg)

## Trie

* A kind of tree that is good for text-based features such as autocomplete
* It is **NOT** a binary tree. It can have multiple child nodes.
*
