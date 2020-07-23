
## Problem

[1431 - Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/)

## Problem Description

Given the array `candies` and the integer `extraCandies`, where `candies[i]` represents the number of candies that the __ith__ kid has.

For each kid check if there is a way to distribute extraCandies among the kids such that he or she can have the __greatest__ number of candies among them. Notice that multiple kids can have the __greatest__ number of candies.



__Example 1:__
```
Input: candies = [2,3,5,1,3], extraCandies = 3
Output: [true,true,true,false,true]
Explanation:
Kid 1 has 2 candies and if he or she receives all extra candies (3) will have 5 candies --- the greatest number of candies among the kids.
Kid 2 has 3 candies and if he or she receives at least 2 extra candies will have the greatest number of candies among the kids.
Kid 3 has 5 candies and this is already the greatest number of candies among the kids.
Kid 4 has 1 candy and even if he or she receives all extra candies will only have 4 candies.
Kid 5 has 3 candies and if he or she receives at least 2 extra candies will have the greatest number of candies among the kids.
```

__Example 2:__
```
Input: candies = [4,2,1,1,2], extraCandies = 1
Output: [true,false,false,false,false]
Explanation: There is only 1 extra candy, therefore only kid 1 will have the greatest number of candies among the kids regardless of who takes the extra candy.
```

__Example 3:__
```
Input: candies = [12,1,12], extraCandies = 10
Output: [true,false,true]
```

## My solution

In order to solve this problem, since I am using _Java_ as my programming language and the variables have static types, I need to create a _List_ of _Boolean_. After creating this empty list, I create a variable called `max` and assign the value __-1__ to it, because I imagine that the kids can't have negative candies (if they could have negative candies, we could assign the value __Integer.MIN_VALUE__ to the variable and change the `>` in the inside the following _for each_ loop to a `>=`).

Then, we have a _for each_ loop, which is used to find the maximum value inside the array. After this, we have another _for each_ loop, which iterates through the given array and checks if `c + extraCandies >= max` (we check if it is grater or equal because at the end of the problem description we are told that multiple kids can have the greatest number of candies), then stores the result of this operation (_true_ or _false_) inside the list that we created at the beginning (`res`).

Finally, we return `res` as the final answer.

## Code

- Language: Java

```java
class Solution {
    public List<Boolean> kidsWithCandies(int[] candies, int extraCandies) {
        List<Boolean> res = new ArrayList<>();
        int max = -1;

        for (int c : candies) {
            if (c > max)
                max = c;
        }


        for (int c : candies) {
            res.add(c + extraCandies >= max);
        }

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N)_
