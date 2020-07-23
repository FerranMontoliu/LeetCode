
## Problem

[1470 - Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/)

## Problem Description

Given the array `nums` consisting of `2n` elements in the form `[x1,x2,...,xn,y1,y2,...,yn]`.

Return the array in the form `[x1,y1,x2,y2,...,xn,yn]`.

__Example 1:__
```
Input: nums = [2,5,1,3,4,7], n = 3
Output: [2,3,5,4,1,7]
Explanation: Since x1=2, x2=5, x3=1, y1=3, y2=4, y3=7 then the answer is [2,3,5,4,1,7].
```

__Example 2:__
```
Input: nums = [1,2,3,4,4,3,2,1], n = 4
Output: [1,4,2,3,3,2,4,1]
```

__Example 3:__
```
Input: nums = [1,1,2,2], n = 2
Output: [1,2,1,2]
```

## My solution

For this problem, I think the easiest way to do it is using an extra array to store the answer. The array must have the same length as the original array, which can be obtained either using `nums.length` or `2*n`. In this case I created the new array using `2*n` as the length.

Now we use a _for_ loop to iterate `n` times (half of the size of the given array). At each iteration of the loop, we put the value of `nums[i]` inside `res[j]` and then we increment `j` by 1. After that, we put the value of `nums[n + i]` inside `res[j]` and then we increment `j` by 1 again. At each iteration of the _for_ loop, the value of `i` is incremented by 1.

Finally, we return `res`, which is the array that we created at the beginning.

## Code

- Language: Java

```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int[] res = new int[2*n];

        for(int i = 0, j = 0; i < n; i++) {
            res[j++] = nums[i];
            res[j++] = nums[n + i];
        }
        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
