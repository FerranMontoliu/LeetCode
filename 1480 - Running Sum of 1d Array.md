
## Problem

[1480 - Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/)

## Problem Description


Given an array `nums`. We define a running sum of an array as `runningSum[i] = sum(nums[0]…nums[i])`.

Return the running sum of `nums`.

__Example 1:__
```
Input: nums = [1,2,3,4]
Output: [1,3,6,10]
Explanation: Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].
```

__Example 2:__
```
Input: nums = [1,1,1,1,1]
Output: [1,2,3,4,5]
Explanation: Running sum is obtained as follows: [1, 1+1, 1+1+1, 1+1+1+1, 1+1+1+1+1].
```

__Example 3:__
```
Input: nums = [3,1,2,10,1]
Output: [3,4,6,16,17]
```

## My solution

We could come up with a solution that used an auxiliar array which stored the running sum in each position and it would be as efficient in time as the solution I programmed, but it would have a space complexity of _O(N)_ instead of _O(1)_, which is the space complexity of my solution.  
In my code, I start with a _for_ loop that goes from 1 to the length of the given array. That is because the first position of the answer will always be nums[0], so we can skip that, and because we skipped that, we saved some if statements to avoid null pointer exceptions in the _for_ loop.  
Inside the for loop, we add _nums[i - 1]_ and _nums[i]_, and we put that inside nums[i]. This way, each time we do this, we will have the previous running sum in _nums[i - 1]_, and we will add nums[i] and store the new running sum in _nums[i]_.  
Finally, we return _nums_ as the answer.

## Code

- Language: Java

```java
class Solution {
    public int[] runningSum(int[] nums) {        
        for (int i = 1; i < nums.length; i++) {
            nums[i] = nums[i - 1] + nums[i];
        }

        return nums;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
