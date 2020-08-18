
## Problem

[1295 - Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)

## Problem Description

Given an array `nums` of integers, return how many of them contain an __even number__ of digits.

__Example 1:__
```
Input: nums = [12,345,2,6,7896]
Output: 2
Explanation:
12 contains 2 digits (even number of digits).
345 contains 3 digits (odd number of digits).
2 contains 1 digit (odd number of digits).
6 contains 1 digit (odd number of digits).
7896 contains 4 digits (even number of digits).
Therefore only 12 and 7896 contain an even number of digits.
```

__Example 2:__
```
Input: nums = [555,901,482,1771]
Output: 1
Explanation:
Only 1771 contains an even number of digits.
```

__Constraints:__
```
1 <= nums.length <= 500
1 <= nums[i] <= 10^5
```

## My solution

My first approach to this problem was to implement an iterative function to count the number of digits in a number, but I knew there was a better solution so I started to look for number theory information and I found that if you do a logarithm with `10` as the base and `n` as the number, and then add 1 to this and cast it to _int_, you get the number of digits of `n`. Then I replaced my iterative function with this line `(int) (Math.log10(n) + 1) % 2 == 0`, that counts the number of digits in `n` and returns `true` if the number is __even__. Then, if the number is even, I add 1 to a variable called `res`, which I assigned to `0` at the beginning.

After repeating this process with all the numbers, I finally return `res` as the answer.

_This solution only works with positive numbers. I implemented it because in the constraints of the problem it states that the numbers will always be positive. Else, I would have stayed with my first approach or I would have calculated the absolute value of the number before computing its logarithm and if it was 0, I would return directly 1._


## Code

- Language: Java

```java
class Solution {
    public int findNumbers(int[] nums) {
        int res = 0;

        for (int n : nums) {
            if ((int) (Math.log10(n) + 1) % 2 == 0)
                res++;
        }

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
