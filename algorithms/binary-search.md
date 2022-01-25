# Binary Search

Use on a sorted collection to discard half of the collection with each iteration. This narrows the collection down to the target value if one exists. If the loop runs to completion then the target value is not in the collection.

Time complexity: O(log n)

Space complexity: O(1) for iterative algorithm. O(log n) for recursive algorithm.

## Iterative Algorithm

```python
def binary_search(nums: List[int], target: [int]) -> int | None:
    left = 0
    right = len(nums) - 1
    # Less than or equal check is used in while condition to handle the case when there is one element
    while left <= right:
        # the middle (or average) of the range
        mid = (right + left) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return None
```

Note:

* The `mid = (right + left) // 2` formula is fine for Python, where we don't need to worry about Integer overflow errors. In Java the formula should be `mid = left + (right - left) / 2`. See [Integer Overflow error in this article.](https://realpython.com/binary-search-python/#integer-overflow)

## Recursive Algorithm

```python
def binary_search_recursive(nums: List[int], target: [int]) -> int | None:
    def recursive(left, right):
        if left > right:
            return None
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            return recursive(mid + 1, right)
        else:
            return recursive(left, mid - 1)

    return recursive(0, len(nums) - 1)
```



## Resources

[https://realpython.com/binary-search-python/](https://realpython.com/binary-search-python/)
