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
* Each subtree must be a valid binary search tree.

[![Binary search tree](https://upload.wikimedia.org/wikipedia/commons/thumb/d/da/Binary\_search\_tree.svg/256px-Binary\_search\_tree.svg.png)](https://commons.wikimedia.org/wiki/File:Binary\_search\_tree.svg)

### Deletion rules

* If the node to delete has no children, then just delete it
* If the node to delete has one child, delete the node, and put the child node where the deleted node was.
* If the node to delete has two children, then replace it with successor node. The successor node is the node with the least value of the child nodes that are greater than the deleted node.&#x20;
  * To find the successor node: visit the right child of the deleted node. Traverse down the left branch of all child nodes until a node does not have a left child. That node is the successor node.
* If the successor node has a right child, then after placing the successor node in its new spot, move the right child to the left side of the successor's former parent
* Example of finding the successor node:
  * Suppose we want to delete 3 from the above diagram. We would delete the 3, then move to the right child, 6. We, then traverse down the left branches. In this case, there is only one, 4. Node 4, moves to where node 3 was.&#x20;

## Tree Traversal

Four ways to traverse a tree are:

* Preorder
* Inorder
* Postorder
* Level order&#x20;

The first 3 traversals (preorder, inorder and postorder) use[ Depth First Search](../algorithms/depth-first-search-dfs.md) to traverse the tree. Where the node is processed in relation to traversing the children determines the type of traversal. Level order traversal uses [Breadth First Search ](../algorithms/breadth-first-search-bfs.md#traversal-1)to traverse the tree.

### Preorder

The tree is traversed in the order: Node -> Left -> Right

Using the above [binary search tree](trees.md#binary-search-trees) structure, the result of a preorder traversal would be:

```
8, 3, 1, 6, 4, 7, 10, 14, 13
```

Using preorder traversal means the root node will be processed first.

```python
def preorder(tree: TreeNode):
    if node is None:
        return
    print(node.value)
    preorder(node.left)
    preorder(node.right)

```

### Inorder

The tree is traversed in the order: Left -> Node -> Right

Using the above [binary search tree](trees.md#binary-search-trees) structure, the result of an inorder traversal would be:

```
1, 3, 4, 6, 7, 8, 10, 13, 14
```

Using inorder traversal on a binary search tree will traverse the nodes in ascending order.

```python
def inorder(tree: TreeNode):
    if node is None:
        return
    inorder(node.left)
    print(node.value)
    inorder(node.right)
    
```

### Postorder

The tree is traversed in the order: Left -> Right -> Node

Using the above [binary search tree](trees.md#binary-search-trees) structure, the result of an inorder traversal would be:

```
1, 4, 7, 6, 3, 13, 14, 10, 8
```

Using postorder traversal means the root node will be processed last.

```python
def postorder(tree: TreeNode):
    if node is None:
        return
    postorder(node.left)
    postorder(node.right)
    print(node.value)
    
```

### Level-order

The tree is traversed level by level: Level 0 -> Level 1 -> Level 2 etc

Using the above [binary search tree](trees.md#binary-search-trees) structure, the result of a level traversal would be:

```
8, 3, 10, 1, 6, 14, 4, 7, 13
```

```python
def level_order(tree: TreeNode) -> List:
    queue = deque()
    result = []
    queue.append(tree)
    while queue:
        node = queue.popleft()
        if node:
            result.append(node.value)
            queue.append(node.left)
            queue.append(node.right)
    return result
```

## Trie

* A kind of tree that is good for text-based features such as autocomplete
* It is **NOT** a binary tree. It can have multiple child nodes.
*
