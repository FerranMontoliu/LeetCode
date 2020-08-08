
## Problem

[771 - Jewels and Stones](https://leetcode.com/problems/jewels-and-stones/)

## Problem Description

You're given strings `J` representing the types of stones that are jewels, and `S` representing the stones you have.  Each character in `S` is a type of stone you have.  You want to know how many of the stones you have are also jewels.

The letters in `J` are guaranteed distinct, and all characters in `J` and `S` are letters. Letters are case sensitive, so `"a"` is considered a different type of stone from `"A"`.

__Example 1:__
```
Input: J = "aA", S = "aAAbbbb"
Output: 3
```
__Example 2:__
```
Input: J = "z", S = "ZZ"
Output: 0
```
## My solution

To solve this problem, I tried different implementations.

The first one was to use a _for_ loop to iterate through `J` and executing this line inside the loop res += `S.length() - S.replaceAll(String.valueOf(J.charAt(i)),"").length();`. This solution was extremely slow, so I jumped to a different implementation.

The second one was to use a _HashSet_ to store all the letters inside `J` using a _for_ loop. Then, in another _for_ loop, I would check if each char inside `S` was contained inside the _HashSet_, and if it was, I would increment the result by 1.

The third and final implementation was to do a _for_ loop iterating through `S`. Inside of the loop, there is an if statement checking if the specific char that is being checked in `S` is contained in `J`. If it is, then we increment the result by 1. Finally, we return `res`.

## Code

- Language: Java

```java
class Solution {
    public int numJewelsInStones(String J, String S) {
        int res = 0;

        for (int i = 0; i < S.length(); i++) {
            if (J.contains(String.valueOf(S.charAt(i))))
                ++res;

        }
        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
