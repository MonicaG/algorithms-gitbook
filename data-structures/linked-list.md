# Linked List

## Singly Linked List

A linked list is a node based structure that contains its data, plus a link to the next node in the list.

![Lasindi, Public domain, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/6/6d/Singly-linked-list.svg)

### Linked list vs array

An array stores its elements in contiguous memory cells.  This means the computer needs to find an entire block of contiguous cells to store the array data. This can get increasingly difficult as the array increases in size.

In contrast, linked lists may use non-contiguous memory cells to store its elements. This is an advantage over the array, because the linked list's data can be spread throughout the computer’s memory.



| Operation  | Array                                   | Linked List                             |
| ---------- | --------------------------------------- | --------------------------------------- |
| get item   | O(1)                                    | O(N)                                    |
| insert     | O(N) but O(1) for inserting at the end  | O(N) but O(1) for inserting at the head |
| delete     | O(N) but O(1) for deleting last element | O(N) but O(1) for deleting head element |
| get length | O(1)                                    | O(N)                                    |

### When to use a linked list

* If most of your operations will deal with the head element, as it has faster insertion/deletion times.
* If you are already iterating through a list and need to delete or add items as you go. Both array and linked list have the same O(N) times in the table above for insert and delete. In the array case, it is O(N) because the items need to be shifted in order to grow/shrink the array. This has a time of O(N). However, in the the linked list case, it has to be traversed to find the element to insert at or delete. This traversal is O(N). So, if you are already looping through the list, it will be faster to use a Linked list data structure as the insert/delete is only O(1) when you have the node. Especially if you have many nodes to delete/insert.

### Techniques

#### Runner

The runner technique uses two pointers to iterate through the list. The first pointer (the fast one) moves ahead of the second pointer (the slow one). The fast one may be ahead by a set amount or it might hop nodes for each node the second pointer iterates on.

This technique is used to [detect a cycle in a linked list](../problems/leetcode/141.-linked-list-cycle.md).

#### Recursion

Many linked list problems are easier solved by recursion then iteration. From [Wikipedia entry on linked lists](https://en.wikipedia.org/wiki/Linked\_list#Singly\_linked\_linear\_lists\_vs.\_other\_lists):

> A singly linked linear list is a recursive data structure, because it contains a pointer to a smaller object of the same type. For that reason, many operations on singly linked linear lists (such as merging two lists, or enumerating the elements in reverse order) often have very simple recursive algorithms, much simpler than any solution using iterative commands

## Doubly linked list

A doubly linked list contains links to both the next and previous nodes. This allow us to move both forward and back through the list. It also has O(1) operations for the tail and head nodes.

![Lasindi, Public domain, via Wikimedia Commons](https://upload.wikimedia.org/wikipedia/commons/5/5e/Doubly-linked-list.svg)



| Operation | Singly Linked List            | Doubly linked list                     |
| --------- | ----------------------------- | -------------------------------------- |
| get item  | O(N)                          | O(N)                                   |
| insert    | O(N) but O(1) at head         | O(N) but O(1) at head and tail         |
| delete    | O(N) but O(1) at head         | O(N) but O(1) at head and tail         |
| movement  | only forward through the list | move forward and backward through list |

Because of its O(1) time complexity for both head and tail elements, a linked list is a good structure for a Queue.

See [collections.deque](https://docs.python.org/3/library/collections.html#collections.deque) in Python.

## References

* [https://en.wikipedia.org/wiki/Linked\_list](https://en.wikipedia.org/wiki/Linked\_list)
* [Cracking the coding interview](https://www.crackingthecodinginterview.com/) - Chapter 2
* [A Common-Sense Guide to Data Structures and Algorithms, Second Edition](https://pragprog.com/titles/jwdsal2/a-common-sense-guide-to-data-structures-and-algorithms-second-edition/) - Chapter 14.
* [Time Complexity in Python](https://wiki.python.org/moin/TimeComplexity)
