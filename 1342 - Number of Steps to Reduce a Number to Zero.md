
## Problem

[1342 - Number of Steps to Reduce a Number to Zero](https://leetcode.com/problems/number-of-steps-to-reduce-a-number-to-zero/)

## Problem Description


## My solution

In this case, I give 2 different solutions to the problem.

The first solution is the first one I programmed, using arithmetic operators, but the second one uses some bitwise operators (which is not necessary in Java, because the compiler does this task internally, but was an interesting approach to code).

Both solutions have the same logic. While the number is grater than zero, there is an if statement which checks if the number is even or odd. If it is even, then we divide it by 2 (which can be done by the arithmetic division operator or by using bitwise operators and shifting one bit to the right). If the number is odd, we substract one from it. After that, in either case, we increment the number of steps by one.

Finally, we return the number of steps.


## Code

- Language: Java

```java
class Solution {
    public int numberOfSteps (int num) {
        int steps = 0;

        while (num > 0) {
            if (num % 2 == 0)
                num/= 2;
            else
                --num;

            ++steps;
        }

        return steps;
    }
}
```

```java
class Solution {
    public int numberOfSteps (int num) {
        int steps = 0;

        while (num > 0) {
            if ((num & 1) != 1)
                num = num >> 1;
            else
                --num;

            ++steps;
        }

        return steps;
    }
}
```
## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
