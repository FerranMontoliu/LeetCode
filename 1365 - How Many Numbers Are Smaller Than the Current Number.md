
## Problem

[1365 - How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/)

## Problem Description

Given the array `nums`, for each `nums[i]` find out how many numbers in the array are smaller than it. That is, for each `nums[i]` you have to count the number of valid j's such that `j != i` and `nums[j] < nums[i]`.

Return the answer in an array.

__Example 1:__
```
Input: nums = [8,1,2,2,3]
Output: [4,0,1,1,3]
Explanation:
For nums[0]=8 there exist four smaller numbers than it (1, 2, 2 and 3).
For nums[1]=1 does not exist any smaller number than it.
For nums[2]=2 there exist one smaller number than it (1).
For nums[3]=2 there exist one smaller number than it (1).
For nums[4]=3 there exist three smaller numbers than it (1, 2 and 2).
```

__Example 2:__
```
Input: nums = [6,5,4,8]
Output: [2,1,0,3]
```

__Example 3:__
```
Input: nums = [7,7,7,7]
Output: [0,0,0,0]
```

## My solution

In order to solve this problem, the first approach would be a brute force algorithm, with a time complexity of _O(N<sup>2</sup>)_. Given that this is not a very good idea, my approach is the following:

First, I clone the given array and then sort it in ascending order. This way, the lower numbers are the first ones. But this array can have duplicates and this is a problem, so I create a _HashMap_ (which can't have duplicates) and then I iterate through the sorted array. If the number that I am checking was already in the _HashMap_, then I only increment a variable called `j`, which was assigned to 0 at the beginning. Else, I put the value `j` associated with the key `copy[i]` in the _HashMap_ and then I increment `j`.

By doing this, at the end I will have a _HashMap_ in which the keys are all the __different__ numbers which appeared in the original array, and as their value they will have the number of smaller numbers in the original array.

Finally, I put this values from the _HashMap_ (using the numbers in the original array so they are in their original order) inside the `copy` array, which I created at the beginning of the program. I use the same array because I don't need that array anymore and by doing so, I don't have to create another one. Then, at the end of the loop, I return the variable `copy` as the final answer.

## Code

- Language: Java

```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        int len = nums.length, j = 0;
        int[] copy = nums.clone();
        Arrays.sort(copy);

        HashMap<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < len; i++) {
            if (!map.containsKey(copy[i]))
                map.put(copy[i], j);
            j++;
        }

        for (int i = 0; i < len; i++) {
            copy[i] = map.get(nums[i]);
        }

        return copy;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
