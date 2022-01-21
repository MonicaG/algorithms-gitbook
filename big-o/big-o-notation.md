# Big O Notation

* Big O deals with classification of algorithms.
  * It does not help determine whether one algorithm is faster than another in a given classification.
  * Because it deals with classification, constants and non-determinate terms are dropped.
    * Example: an algorithm of O(n^2 + n) is considered O(n^2). Because, the growth rate is determine by the n^2.
    * Example: an algorithm of O(2n) becomes O(n). Because the growth is determined by n, not the constant 2.
* Big O categories, from fastest growth rate (bad) to slowest growth rate(good):
  * O(n!)
    * ex: Listing all permutations of an array
  * O(2^n)
    * ex: Recursive Fibonacci
  * O(n^2)
    * ex: Bubble Sort, Insertion Sort
  * O(n log(n))
    * ex: Merge Sort
  * O(n)
    * ex: iterating over an array
  * O(log(n))
    * ex: Binary search on sorted array
  * O(1)
    * ex: Accessing an array element

[![Comparison computational complexity](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Comparison\_computational\_complexity.svg/512px-Comparison\_computational\_complexity.svg.png)](https://commons.wikimedia.org/wiki/File:Comparison\_computational\_complexity.svg)

* Generally, if an algorithm has two loops that are not nested, the runtimes are added together. Example:

```python
def print_arrays(arr1: [int], arr2: [int]):
    for x in arr1:
        print(x)

    for y in arr2:
        print(y)
```

* The runtime of the above would be O(m + n), where m is the size of arr1 and n is the size of arr2. But this can be simplified to just O(n) if we consider n to be the total number of elements in both m and n.
* Generally, two nested loops are O(n^2)

```python
def multiply_items(arr:[int]):
    for i in range(len(arr)):
        for j in range(len(arr)):
            if i != j:
                print(arr[i]*arr[j])

multiply_items([1, 3, 5])
```

* The runtime of the above would be O(n^2).
* However, not all nested loops have a runtime of O(n^2), as in the examples below:
* Example1: (from [A Common-Sense Guide to Data Structures and Algorithms, Second Edition](https://pragprog.com/titles/jwdsal2/a-common-sense-guide-to-data-structures-and-algorithms-second-edition/) )

```python
def count_ones(arr: [[int]]):
    count = 0
    for inner_array in arr:
        for num in inner_array:
            if num == 1:
                count += 1
    return count

my_array = [
    [0, 1, 1, 1, 0],
    [1, 1, 1],
    [0, 0 ,0 , 0],
    [1, 0]
]

x = count_ones(my_array) 
print(f'number of 1s: {x}')
```

* In the above example the runtime is O(n). This is because the loops are iterating over different things. The outer loop is looping over the inner arrays. The inner loop is iterating over each inner array's numbers. Here each item of an array is only operated on once. So the growth is O(n).
  * This is in contrast to the previous example, where there was one array and each item in that array was looped over n times (where n is the size of the array).
* Example 2:

```python
def multiply(A: [int], B: [int]):
    for a in A:
        for b in B:
            print(f'{a * b}')

multiply([1, 2, 3, 4], [5, 6 , 7, 8, 9])
```

* In the above example the runtime is O(A \* B). Here, each element of the B array is operated on by every element of array A. So the runtime is the length of array A \* the length of array B.
