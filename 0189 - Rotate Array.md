
## Problem

[189 - Rotate Array](https://leetcode.com/problems/rotate-array/)

## Problem Description
Given an array, rotate the array to the right by _k_ steps, where _k_ is non-negative.

__Follow up:__
- Try to come up as many solutions as you can, there are at least 3 different ways to solve this problem.
- Could you do it in-place with O(1) extra space?

__Example 1:__
```
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
```

__Example 2:__
```
Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation:
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```

__Constraints:__
- `1 <= nums.length <= 2 * 10^4`
- It's guaranteed that `nums[i]` fits in a 32 bit-signed integer.
- `k >= 0`


## My solution
My first approach to this problem was a solution in which I created an auxiliar array and placed each element to its correct position. It was a valid approach in terms of time complexity, as it was __O(N)__, but in terms of space complexity it was __O(N)__, too. So I wanted to implement a solution which was __O(1)__ in space, just as the problem description asks.

In order to do so, I implemented the solution that you can find below. It starts by assigning a new value to `k`, just in case `k` is larger than the given array's length. Then it calls the same function three times, but each time with different values:

- In the first call, I reverse all the items of the array.
- In the second call, I reverse the items of the array from `0` to `k-1`.
- In the third call, I reverse the items of the array from `k` to the end.

After doing so, the original array is rotated `k` steps and we only used one _int_ as extra space (`temp`).


## Code

- Language: Java

```java
class Solution {
    public void rotate(int[] nums, int k) {
        k %= nums.length;

        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k-1);
        reverse(nums, k, nums.length - 1);
    }

    private void reverse(int[] nums, int start, int end) {
        int temp;
        while (start < end) {
            temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
