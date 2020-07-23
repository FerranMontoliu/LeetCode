
## Problem

[1108 - Defanging an IP Address](https://leetcode.com/problems/defanging-an-ip-address/)

## Problem Description

Given a valid (IPv4) IP `address`, return a defanged version of that IP address.

A defanged IP address replaces every period `"."` with `"[.]"`.


__Example 1:__
```
Input: address = "1.1.1.1"
Output: "1[.]1[.]1[.]1"
```

__Example 2:__
```
Input: address = "255.100.50.0"
Output: "255[.]100[.]50[.]0"
```

## My solution

My first approach was to create an extra _String_, iterate through the original _String_ and then copy every char that wasn't a `"."`, and when I found a `"."`, then add `"[.]"` to the _String_ instead. This approach was surprisingly slow so I decided to use existing _Java String_ tools.

So, in order to solve this problem I just call the function `"String replace(char oldChar, char newChar)"`, using `"."` as the _oldChar_ and `"[.]"` as the _newChar_, and return the value that it returns.

This way, we don't use extra variables, but since the _replace_ function has to iterate through the _String_, the complexity is still _O(N)_.

## Code

- Language: Java

```java
class Solution {
    public String defangIPaddr(String address) {
        return address.replace(".", "[.]");
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
