
## Problem

[1281 - Subtract the Product and Sum of Digits of an Integer](https://leetcode.com/problems/subtract-the-product-and-sum-of-digits-of-an-integer/)

## Problem Description

Given an integer number `n`, return the difference between the product of its digits and the sum of its digits.


__Example 1:__
```
Input: n = 234
Output: 15
Explanation:
Product of digits = 2 * 3 * 4 = 24
Sum of digits = 2 + 3 + 4 = 9
Result = 24 - 9 = 15
```

__Example 2:__
```
Input: n = 4421
Output: 21
Explanation:
Product of digits = 4 * 4 * 2 * 1 = 32
Sum of digits = 4 + 4 + 2 + 1 = 11
Result = 32 - 11 = 21
```

## My solution

My approach to solve this problem was to iterate through the digits of the number in a _while_ loop and storing the result of the product of the digits and the sum of the digits in 2 different variables. I used a 3rd variable called `dig`, which represents the digit that is being used at the given iteration of the loop. This way, I don't have to do the operation `n % 10` twice, I have to do it once and then get the value from the variable twice.

Once I have iterated through all the digits in the number, I return `prod - sum`, which is the product of all the digits minus the sum of all the digits.

## Code

- Language: Java

```java
class Solution {
    public int subtractProductAndSum(int n) {
        int prod = 1, sum = 0, dig;

        while (n > 0) {
            dig = n % 10;
            prod *= dig;
            sum += dig;

            n /= 10;
        }

        return prod - sum;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(log(N))_
- _Space Complexity: O(1)_
