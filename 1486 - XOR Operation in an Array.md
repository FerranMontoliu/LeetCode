
## Problem

[1486 - XOR Operation in an Array](https://leetcode.com/problems/xor-operation-in-an-array/)

## Problem Description

Given an integer `n` and an integer `start`.

Define an array `nums` where `nums[i] = start + 2*i` (0-indexed) and `n == nums.length`.

Return the bitwise XOR of all elements of `nums`.


__Example 1:__
```
Input: n = 5, start = 0
Output: 8
Explanation: Array nums is equal to [0, 2, 4, 6, 8] where (0 ^ 2 ^ 4 ^ 6 ^ 8) = 8.
Where "^" corresponds to bitwise XOR operator.
```

__Example 2:__
```
Input: n = 4, start = 3
Output: 8
Explanation: Array nums is equal to [3, 5, 7, 9] where (3 ^ 5 ^ 7 ^ 9) = 8.
```

__Example 3:__
```
Input: n = 1, start = 7
Output: 7
```

__Example 4:__
```
Input: n = 10, start = 5
Output: 2
```

## My solution

In order to solve the problem, I didn't use an extra array to store the values as the problem statement asks, because it can be solved without it, reducing the space complexity of the solution.

My first approach of the problem was to iterate from _0_ to `n` and doing `res ^= start + 2*i;` inside the _for_, and then finally, return `res`. This approach was correct but I wanted to optimize it a little more, by changing the `2*i` to a `i << 1`. I know that most compilers do this and this may be useless, but I thought this second approach was interesting.

## Code

- Language: Java

```java
class Solution {
    public int xorOperation(int n, int start) {
        int res = 0;

        for (int i = 0; i < n; i++)
            res ^= start + (i << 1);

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
