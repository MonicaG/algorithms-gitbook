# Strings and Arrays



### Sliding Window

* Used to find subarrays within an array that satisfies certain conditions.
* An example:
  * given an array find the pair of contiguous numbers that have the greatest sum of all pairs
* Used when wanting to find some max, min, longest, shortest etc value from contiguous elements in an array or string

#### Reference:

* [Sliding Window](https://quanticdev.com/algorithms/dynamic-programming/sliding-window/)

#### Questions:

* [LeetCode: 3 - Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### Expand around the center

* Used for palindromes. The concept is the palindrome has a center point and you expand left and right pointers out from the center point. At each movement you check the values of left and right positions equal each other or not. This is similar to the sliding window concept above.

#### Reference:

* [longest-palindromic-substring](https://medium.com/@bhprtk/longest-palindromic-substring-a8190fab03ff)
* [youtube](https://www.youtube.com/watch?v=LgG2Km9GvJw)

#### Questions:

* [LeetCode 5 - Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)



### Two Pointers

When the brute force solution is nested arrays, see if a O(n) solution can be obtained using two pointers.



#### Questions:

* [LeetCode 11 - Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
