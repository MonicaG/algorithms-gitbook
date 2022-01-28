# Sliding Window

## Overview

The sliding window is more of a technique than algorithm. It is a form of [dynamic programming](dynamic-programming.md) since it makes use of the problems overlapping subproblems.&#x20;

Two pointers are used to create a "window" over some data in the array or string. The window contains the data you are currently looking at. This data is usually compared against some previously calculated "best" data (like min, max, longest, shortest etc).

## Usage

* Used to find subarrays within an array that satisfies certain conditions.
* An example:
  * given an array find the pair of contiguous numbers that have the greatest sum of all pairs
* Used when wanting to find some max, min, longest, shortest etc value from contiguous elements in an array or string
* When the brute force solution is nested arrays, see if a O(n) solution can be obtained using a sliding window

## Types

### Fast/Slow

Have a fast pointer that grows the window and a slow pointer that shrinks the window. The fast pointer advances until the window contains the data you are looking for. Then the slow pointer increments, shrinking the window. The slow pointer keeps incrementing until the window no longer contains valid data.

Example:

* [Minimum Window Substring](../problems/leetcode/76.-minimum-window-substring.md) question.

### Fast/Catch-up

Similar to Fast/Slow but the slow pointer jumps to the fast pointer position rather than slowly incrementing to it.&#x20;

Example:

* [Longest Substring Without Repeating Characters](../problems/leetcode/3.-longest-substring-without-repeating-characters.md)

### Fast/Trailing

The slow pointer is a few indices behind the fast pointer. It is keeping track of some choice you have made.

Example:

* [House Robber](https://leetcode.com/problems/house-robber/)

### Front/Back

One pointer travels from the end of the array and one from the start of the array. One side is moved based on some condition.

Example:

* [Container With Most Water](../problems/leetcode/11.-container-with-most-water.md)

### Expand around the center

Used for palindromes. The concept is the palindrome has a center point and you expand left and right pointers out from the center point. At each movement you check the values of left and right positions equal each other or not. This is similar to the sliding window concept above.

Example:

* [Longest Palindromic Substring](../problems/leetcode/5.-longest-palindromic-substring.md)

## Reference:

* [Sliding Window](https://quanticdev.com/algorithms/dynamic-programming/sliding-window/)
* [How to Solve Sliding Window Problems](https://medium.com/outco/how-to-solve-sliding-window-problems-28d67601a66)
* [longest-palindromic-substring](https://medium.com/@bhprtk/longest-palindromic-substring-a8190fab03ff)
* [Longest Palindromic Substring - LeetCode 5 - Java Solution | Expand Around Center Approach](https://youtu.be/LgG2Km9GvJw)

