
## Problem

[1528 - Shuffle String](https://leetcode.com/problems/shuffle-string/)

## Problem Description

Given a string `s` and an integer array `indices` of the same length.

The string `s` will be shuffled such that the character at the `ith` position moves to `indices[i]` in the shuffled string.

Return the _shuffled_ string.


__Example 1:__
```
Input: s = "codeleet", indices = [4,5,6,7,0,2,1,3]
Output: "leetcode"
Explanation: As shown, "codeleet" becomes "leetcode" after shuffling.
```

__Example 2:__
```
Input: s = "abc", indices = [0,1,2]
Output: "abc"
Explanation: After shuffling, each character remains in its position.
```

__Example 3:__
```
Input: s = "aiohn", indices = [3,1,4,2,0]
Output: "nihao"
```

__Example 4:__
```
Input: s = "aaiougrt", indices = [4,0,2,6,7,3,1,5]
Output: "arigatou"
```

__Example 5:__
```
Input: s = "art", indices = [1,0,2]
Output: "rat"
```

## My solution

In order to solve this problem, I thought there could be 2 possible approaches. One with a space complexity of _O(1)_ and one with a space complexity of _O(N)_. In this case, I thought about implementing both answers but the one with less space complexity was too slow, so I think that the second one is better.

In my solution, I start by declaring a new _array of chars_ the same length as the given _String_, then using a _for_ loop, I iterate through the given _String_ and put the chars one by one at their corresponding positions in the new array I created using as index `indices[i]`. After doing so, I have an _array of chars_ with the _String_ already _shuffled_, so I create a new _String_ from this _array of chars_ and then return it.

## Code

- Language: Java

```java
class Solution {
    public String restoreString(String s, int[] indices) {
        char[] aux = new char[indices.length];

        for(int i = 0; i < indices.length; i++) {
            aux[indices[i]] = s.charAt(i);
        }

        return new String(aux);        
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
