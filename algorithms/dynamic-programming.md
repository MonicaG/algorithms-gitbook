# Dynamic Programming

A process for optimizing recursive problems that have overlapping subproblems.

Generally accomplished with either memoization or 'going bottom up'.

## Memoization

Memoization is reducing the recursive calls by storing the result of a function call. That result is returned rather than recursing down the branches.

A typical example is the fibonacci sequence (0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...).

A naive implementation is:

```python
def fib(n):
    if n == 0 or n == 1:
        return n
    return fib(n - 2) + fib(n - 1)
```

Here, the fib(n) function is called twice in the body of the function. This means values are calculated multiple times. For example, if we are calculating fib(5), fib(3) will be calculated multiple times. Which also means the recursive calls fib(3) performs are also performed multiple times and each spawn their own recursive branches.

[![Fibonacci call tree 5](https://upload.wikimedia.org/wikipedia/commons/1/1a/Fibonacci\_call\_tree\_5.gif)](https://commons.wikimedia.org/wiki/File:Fibonacci\_call\_tree\_5.gif)

This function is O(2n), as the number of calls doubles for each level of the tree. This is exponential growth!

A solution is to use memoization to store the values as they are computed. This way the values can be reused instead of recalculated. This eliminates many recursive calls.

Example with memoization where a hash table is used to store the values.

```python
def fib(n, memo={}):
    if n == 0 or n == 1:
        return n
    if n not in memo:
        memo[n] = fib(n - 2, memo) + fib(n - 1, memo)

    return memo[n]
```

This solution is O(n).

A general pattern seems to be to assign the recursive call to `memo[n]` and then `return memo[n]` at the bottom of the function.

## Going Bottom Up

This technique is to rewrite the algorithm to not use recursion.

Example: fibonacci written with a loop

```python
def fib(n: int):
    if n == 0:
        return 0
    a = 0
    b = 1
    for i in range(1, n):
        temp = a
        a = b
        b = temp + a
    return b
```

This is also O(n).

Generally, 'going bottom up' is the better choice as recursion has the overhead of the call stack which consumes memory. When n is large this can lead to stack overflow errors. For some scenarios where recursion is more intuitive and n is small than recursion with memoization can be the better choice.
