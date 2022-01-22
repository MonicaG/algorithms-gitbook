# Kadane's Algorithm

## Description

Kadane's algorithm solves the maximum subarray problem: _given an array of n values (which can be positive, negative, or zero) find a contiguous subarray which has the maximum sum_.&#x20;

Kadane's original algorithm allows for empty subarrays (according to wikipedia). It will return 0 for an empty input array and for an array that contains only negative numbers.

### Examples&#x20;

| input array                      | max sum | sub array             |
| -------------------------------- | ------- | --------------------- |
| \[2, 3, -6, 1, 5, 3]             | 9       | \[1, 5, 3]            |
| \[-2, 1, -3, 4, -1, 2, 1, -5, 4] | 6       | \[4, -1, 2, 1]        |
| \[1]                             | 1       | \[1]                  |
| \[5, 8, -15, -3, 7, 4, 2])       | 13      | \[5, 8] or \[7, 4, 2] |
| \[-5, -2, -8, -1, -7]            | 0       | \[]                   |
| \[2, 3, 4, 5, 6]                 | 20      | \[2, 3, 4, 5, 6]      |
| \[]                              | 0       | \[]                   |

Notes from the above examples:

* A negative number that causes the sum to be less than or equal to zero will not be part of the solution. See the first example.
* A negative number that results with a sum that is greater than zero may or may not be part of the solution. See the second example.
* An input array with just one element has a solution that is just that one element. See the third example
* An input array may have more than one subarray with the same sum. See example 4.
* An array that contains all negative numbers will have a solution of 0. See the fifth example.
* An array that contains all positive numbers will have a solution that is the sum of the entire array. See the sixth example.
* An empty array will have a solution of 0. See the sixth example.

## Solution

### Brute Force

The brute force solution is to sum the elements for every subarray in the array. Give an array of \[2, 3, -6, 4], then the brute force algorithm would do the following:

* Calculate the sum of array \[2]&#x20;
* Calculate the sum of array \[2, 3]&#x20;
* Calculate the sum of array \[2, 3, -6]&#x20;
* Calculate the sum of array \[2, 3, -6, 4]&#x20;
* Calculate the sum of array \[3]
* Calculate the sum of array \[3, -6]
* Calculate the sum of array \[3, -6, 4]
* Calculate the sum of array \[-6]
* Calculate the sum of array \[-6, 4]
* Calculate the sum of array \[4]   &#x20;

An example implementation is below:

```python
 class Solution:
     def max_sub_array_brute(self, nums: List[int]) -> int:
        high_sum = 0
        for i in range(len(nums)):
            current_sum = 0
            for j in range(i, len(nums)):
                current_sum += nums[j]
                if current_sum < 0:
                    current_sum = 0
                high_sum = max(high_sum, current_sum)
        return high_sum
```

Time complexity is O(N^2). Space complexity is O(1).

### Kadane's Algorithm

The brute force solution is not efficient because it recalculates portions of the subarrays multiple times. In the above example \[-6,4] is calculated as part of \[2, 3, -6, 4], \[3, -6, 4] and \[6,4].

Kadane's algorithm iterates over the input array. It keeps track of two things: the maximum sum to this point and the current sum of the sub array.&#x20;

At each element it compares if the current sum (which includes the current element) is less than 0. It may be less than zero if a negative number has caused it to become negative (ex: the -10 in this array\[2, 4, -10, 3]).  Otherwise the current sum is the sum of the sub array. The maximum sum is either the stored maximum sum or the new current sum.

```python
class Solution:
    def max_sub_array_Kadane(self, nums: List[int]) -> int:
        high_sum = 0
        current_sum = 0
        for i in nums:
            current_sum = max(0, current_sum + i)
            high_sum = max(high_sum, current_sum)
        return high_sum
```

Time is O(N) and space is O(1).

Why does this work? When we are at iteration "i" the `current_sum` __ will contain the cumulative sum from A\[a]+...+A\[i-1]. We then assign `current_sum` to either 0 or `current_sum + i`. So, `current_sum` will always have the sum to this position, or it will have restarted. Then `high_sum` tracks the max value seen to that point.

## Resources

* [https://en.wikipedia.org/wiki/Maximum\_subarray\_problem](https://en.wikipedia.org/wiki/Maximum\_subarray\_problem)
* [https://cs.slu.edu/\~goldwamh/courses/slu/csci314/2012\_Fall/lectures/maxsubarray/](https://cs.slu.edu/\~goldwamh/courses/slu/csci314/2012\_Fall/lectures/maxsubarray/)
* [https://www.researchgate.net/publication/222665016\_Efficient\_Algorithms\_for\_the\_Maximum\_Subarray\_Problem\_by\_Distance\_Matrix\_Multiplication](https://www.researchgate.net/publication/222665016\_Efficient\_Algorithms\_for\_the\_Maximum\_Subarray\_Problem\_by\_Distance\_Matrix\_Multiplication)



## Example Problem

* [Maximum Subarray](../problems/leetcode/53.-maximum-subarray.md)
