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

This technique is used for finding palindromes. A way to visualize a palindrome is as a mirror image of itself based on a center point. For example: the string `aba` has a center point `b` and the letters are mirrored around that center point. So, we could set a left and right pointer to the letter `b`. Then we would increment the right pointer, decrement the left pointer and compare the letters. We keep doing this process until a mismatch is found or all letters are read.&#x20;

If there are an even number of letters in the palindrome, then the center point is the two center letters. Example: `abba` the center would be `bb`.&#x20;

#### Code to check if a string is a palindrome

```python
def is_string_a_palindrome(s: str) -> bool:
    # find the mid point, which is our mirror letter(s)
    mid = len(s) // 2
    right = mid
    # if the string has an even number of characters than the left pointer will be mid - 1 (the first b in the above example)
    if len(s) % 2 == 0:
        left = mid - 1
    else:
        left = mid
    # check that the left and right side of the mid point are "mirrors" of each other
    while left >= 0 and right < len(s):
        if s[left] != s[right]:
            return False
        left -= 1
        right += 1
    return True
```

To find a palindrome/palindromes within a string, we need to loop over the string and provide the index for the left and right pointers. We need to perform the expand twice, once for the odd size case and once for the even sized case. In this case the left and right pointer assignment is different as the mid point is the current index and not calculated. Here, for even length substrings, the left pointer is the index and the right pointer is index + 1.

#### Code template for substring expand around the center problems :

```python
class Example:
    def expand_around_center(self, s: str, left: int, right: int):
        while left >= 0 and right < len(s) and s[left] == s[right]:
            left -= 1
            right += 1
               
    def driver(self, s: str):
        # check at each character if the substring is a palindrome
        for index in range(len(s)):
            # Both of these calls need to be done. The first covers the case where the
            # mid point is 1 character. This is for odd length substrings (i.e. "aba").
            # The second covers the case where the mid point is two characters (for
            # even length substrings i.e. "abba").
            self.expand_around_center(s, index, index)
            self.expand_around_center(s, index, index + 1)
        
```

This code is O(n^2) as we have the for loop and then the while loop. This is compared to the brute force solution of O(n^3) which requires two loops to form all possible substrings plus the while loop to check if the substring is a palindrome.

#### Examples

* [5. Longest Palindromic Substring](../problems/leetcode/5.-longest-palindromic-substring.md)
* [647. Palindromic Substrings](../problems/leetcode/647.-palindromic-substrings.md)

## Reference:

* [Sliding Window](https://quanticdev.com/algorithms/dynamic-programming/sliding-window/)
* [How to Solve Sliding Window Problems](https://medium.com/outco/how-to-solve-sliding-window-problems-28d67601a66)
* [longest-palindromic-substring](https://medium.com/@bhprtk/longest-palindromic-substring-a8190fab03ff)
* [Longest Palindromic Substring - LeetCode 5 - Java Solution | Expand Around Center Approach](https://youtu.be/LgG2Km9GvJw)

