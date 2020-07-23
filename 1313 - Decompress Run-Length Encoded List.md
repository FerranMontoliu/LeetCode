
## Problem

[1313 - Decompress Run-Length Encoded List](https://leetcode.com/problems/decompress-run-length-encoded-list/)

## Problem Description

We are given a list `nums` of integers representing a list compressed with run-length encoding.

Consider each adjacent pair of elements `[freq, val] = [nums[2*i], nums[2*i+1]]` (with `i >= 0`).  For each such pair, there are `freq` elements with value val concatenated in a sublist. Concatenate all the sublists from left to right to generate the decompressed list.

Return the decompressed list.

__Example 1:__
```
Input: nums = [1,2,3,4]
Output: [2,4,4,4]
Explanation: The first pair [1,2] means we have freq = 1 and val = 2 so we generate the array [2].
The second pair [3,4] means we have freq = 3 and val = 4 so we generate [4,4,4].
At the end the concatenation [2] + [4,4,4] is [2,4,4,4].
```

__Example 2:__
```
Input: nums = [1,1,2,3]
Output: [1,3,3]
```

## My solution

In order to solve this problem, my approach is to first calculate the length of the final array.

Once I have that, I create the array that I will return as the final answer later. Now, using a _for_ loop, I iterate through all the even numbers of the original array. Inside this loop, we have a nested _for_ loop which goes from _0_ to `nums[i]` and adds `nums[i + 1]` to the `res` array that I created before. Finally I return `res`.

Another possible approach is to not start by calculating the final length and instead use a _List_ to store all the values and, at the end, convert the _List_ to a static array and then return it, though I tried this implementation and was less efficient in time.

## Code

- Language: Java

```java
class Solution {
    public int[] decompressRLElist(int[] nums) {
        int len = 0, k = 0;

        for (int i = 0; i < nums.length; i += 2)
            len += nums[i];


        int[] res = new int[len];

        for (int i = 0; i < nums.length; i += 2)
            for (int j = 0; j < nums[i]; j++)
                res[k++] = nums[i + 1];

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N*M)_
- _Space Complexity: O(N)_
