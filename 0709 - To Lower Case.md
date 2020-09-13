
## Problem

[709 - To Lower Case](https://leetcode.com/problems/to-lower-case/)

## Problem Description
Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.

__Example 1:__
```
Input: "Hello"
Output: "hello"
```

__Example 2:__
```
Input: "here"
Output: "here"
```

__Example 3:__
```
Input: "LOVELY"
Output: "lovely"
```

## My solution
The solution that I expose is the first approach that I tried. It starts by converting the given String to an array of characters and then iterates through the given array, adding `32` to each position that is an uppercase letter.

It finally returns a new String that is constructed using the modified array of chars.


## Code

- Language: Java

```java
class Solution {
    public String toLowerCase(String str) {
        char[] strArr = str.toCharArray();

        for(int i = 0; i < strArr.length; i++)
            if(strArr[i] >= 'A' && strArr[i] <= 'Z')
                strArr[i] += 32;

        return new String(strArr);
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
