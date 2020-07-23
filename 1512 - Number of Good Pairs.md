
## Problem

[1512 - Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/)

## Problem Description

Given an array of integers `nums`.

A pair `(i,j)` is called good if `nums[i]` == `nums[j]` and `i` < `j`.

Return the number of good pairs.

__Example 1:__
```
Input: nums = [1,2,3,1,1,3]
Output: 4
Explanation: There are 4 good pairs (0,3), (0,4), (3,4), (2,5) 0-indexed.
```

__Example 2:__
```
Input: nums = [1,1,1,1]
Output: 6
Explanation: Each pair in the array are good.
```

__Example 3:__
```
Input: nums = [1,2,3]
Output: 0
```
## My solution

For this problem, we could implement a brute force algorithm which would have a time complexity of _O(N<sup>2</sup>)_. In this case, I thought it would be interesting to use a _HashMap_ in order to store a value associated with a key, being the key the number which is analyzed at each iteration of the _for_ loop and the value the number of times that this number appears in the array.

So my code starts by defining an empty _HashMap_ with an _Integer_ key and an _Integer_ value (you can't use primitive types such as _int_, because the _HashMap_ needs an object). After that I create a new _int_ and give it the value of 0. This _int_ (_res_) is the one which will store the number of good pairs.

Now we have a _for each_ with iterates through the given array. Inside, we check if we have encountered the number _n_ before. If we have, we add the value associated to this key in the _HashMap_ to _res_. After that, we increment the value by 1 in the _HashMap_. If we haven't encountered the number _n_ before, we just put the value _1_ using _n_ as the key in the _HashMap_, because now we have encountered the number once.

Finally, we return the _int_ storing the number of good pairs (_res_).

## Code

- Language: Java

```java
class Solution {
    public int numIdenticalPairs(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int res = 0;

        for (int n : nums) {
            if (map.containsKey(n)) {
                res += map.get(n);
                map.put(n, map.get(n) + 1);
            } else {
                map.put(n, 1);
            }
        }

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
