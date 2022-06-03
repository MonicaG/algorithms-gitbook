# Quickselect

Quickselect is often used to solve problems of the form "find kth something": kth smallest, kth largest, kth most frequent, kth less frequent, etc.

The idea is to pick a pivot index and do a partial sort of the array. Items less than the pivot are on the left of the pivot.  Items greater or equal than the pivot are on the right. After the sort the pivot index is in its correct position.&#x20;

Note that the items to the left and right are NOT sorted. However, this does not matter in the "find kth" scenario. What is important is whether the pivot is at the kth element. If it is than we've found the solution. The pivot and anything to the right of it will be the kth greatest. The pivot and anything to the left will be the kth least.&#x20;

If the pivot is not at the correct position then another sort is needed. But, the sort is only done on the part of the array where the kth position will be found. If the pivot is at a position greater than k, then only the left side of the array is sorted. So, the left index to the pivot - 1 position will be sorted. A new pivot based on those indexes will be used. If the pivot is less than k then the kth element will be found on the right side. So, pivot + 1 to the right index will be sorted.

### Choosing a pivot index

There are various schemes to choose a pivot point. Some are:

* Choose the left or right most element - this can lead to a poor pivot though, if the array is already sorted
* a random index&#x20;
* the midpoint
* median of 3 (median of first, middle and last element of the partition) - this is a good strategy.
* and median of medians - not used in production. Theoretically works but is too slow and doesn't handle duplicates.

### Partition Strategy

There are different algorithms to do the partition. Below is the [Lomuto Partition Scheme](https://en.wikipedia.org/wiki/Quicksort#Lomuto\_partition\_scheme) as it is simpler to implement than the original [Hoare Partition Scheme](https://en.wikipedia.org/wiki/Quicksort#Hoare\_partition\_scheme). However, it is less efficient than Hoare's partition when all the elements are the same. The Lomuto partition does not work well on arrays that contain [many repeated elements](https://en.wikipedia.org/wiki/Quicksort#Repeated\_elements).

The steps for the Lomuto Partition are:

* get the pivot index
* swap the the pivot with the right most element
* set a pointer to the left index
* loop through the left to right index range
  * if the current element is less than the pivot than swap the current element with the pointer
  * advance the pointer
* after the loop completes swap the pointer with the right most element (which holds the pivot)
  * the pivot will now be in its correct position

Example:

```python
from typing import List


def lomuto_partition(arr: List[int], left: int, right: int) -> int:
    pivot_index = (left + right) // 2
    arr[right], arr[pivot_index] = arr[pivot_index], arr[right]
    mark = left
    for i in range(left, right):
        if arr[i] < arr[right]:
            arr[i], arr[mark] = arr[mark], arr[i]
            mark += 1
    arr[mark], arr[right] = arr[right], arr[mark]
    return mark


def quick_select(k: int, arr: List[int], left, right) -> int:
    position = lomuto_partition(arr, left, right)
    if position < k:
        return quick_select(k, arr, position + 1, right)
    elif position > k:
        return quick_select(k, arr, left, position - 1)
    else:
        return position


def kth_smallest(k: int, arr: List[int]) -> int | None:
    if k <= 0 or k > len(arr):
        return None
    # k - 1 because arrays are zero based. So, if we want to find the first smallest item, it will be at index 0
    # If we want to find the 4th smallest item, it will be at index 3.
    kth_position = quick_select(k - 1, arr, 0, len(arr) - 1)
    return arr[kth_position]

```

### Time Complexity

The time complexity is O(n) with a worst case of O(n^2). The worst case occurs when a poor pivot is chosen which repeatedly reduces the partition size only by one element. This occurs when the array is already sorted. This can be mitigated by choosing a good pivot index. One strategy is to use the median-of-3 ([https://en.wikipedia.org/wiki/Quicksort#Choice\_of\_pivot](https://en.wikipedia.org/wiki/Quicksort#Choice\_of\_pivot)).
