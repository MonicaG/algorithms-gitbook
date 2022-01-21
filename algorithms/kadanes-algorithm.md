# Kadane's Algorithm

## Description

Kadane's algorithm solves the maximum subarray problem. LeetCode's describes the problem as: "_Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum."_

A subarray can be 1 element, any number of contiguous elements or the entire array.

### Examples&#x20;

| input array                      | max sum | sub array             |
| -------------------------------- | ------- | --------------------- |
| \[2, 3, -6, 1, 5, 3]             | 9       | \[1, 5, 3]            |
| \[-2, 1, -3, 4, -1, 2, 1, -5, 4] | 6       | \[4, -1, 2, 1]        |
| \[1]                             | 1       | \[1]                  |
| \[5, 8, -15, 7, 4, 2])           | 13      | \[5, 8] or \[7, 4, 2] |
| \[-5, -2, -8, -1, -7]            | -1      | \[-1]                 |
| \[2, 3, 4, 5, 6]                 | 20      | \[2, 3, 4, 5, 6]      |

Notes from the above examples:

* A negative number that causes the sum to be less than or equal to zero causes the start of a new subarray after that element. See the first example.
* A negative number that does not cause the sum to be less than or equal to zero may or may not be part of the solution subarray. See the second example.
* An input array with just one element has a solution subarray that is just that one element. See the third example
* An input array may have more than one subarray with the same sum. See example 4.
* An array that contains all negative numbers will have a subarray of one element containing the max element. See the fifth example.
* An array that contains all positive numbers will have a subarray that is the entire array. See the sixth example

## Resources

* [https://en.wikipedia.org/wiki/Maximum\_subarray\_problem](https://en.wikipedia.org/wiki/Maximum\_subarray\_problem)



## Example Problem

* [Maximum Subarray](../problems/leetcode/53.-maximum-subarray.md)
