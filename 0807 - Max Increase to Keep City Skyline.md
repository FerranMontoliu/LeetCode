
## Problem

[807 - Max Increase to Keep City Skyline](https://leetcode.com/problems/max-increase-to-keep-city-skyline/)

## Problem Description

In a 2 dimensional array `grid`, each value `grid[i][j]` represents the height of a building located there. We are allowed to increase the height of any number of buildings, by any amount (the amounts can be different for different buildings). Height 0 is considered to be a building as well.

At the end, the "skyline" when viewed from all four directions of the grid, i.e. top, bottom, left, and right, must be the same as the skyline of the original grid. A city's skyline is the outer contour of the rectangles formed by all the buildings when viewed from a distance. See the following example.

What is the maximum total sum that the height of the buildings can be increased?
```
Example:
Input: grid = [[3,0,8,4],[2,4,5,7],[9,2,6,3],[0,3,1,0]]
Output: 35
Explanation:
The grid is:
[ [3, 0, 8, 4],
  [2, 4, 5, 7],
  [9, 2, 6, 3],
  [0, 3, 1, 0] ]

The skyline viewed from top or bottom is: [9, 4, 8, 7]
The skyline viewed from left or right is: [8, 7, 9, 3]

The grid after increasing the height of buildings without affecting skylines is:

gridNew = [ [8, 4, 8, 7],
            [7, 4, 7, 7],
            [9, 4, 8, 7],
            [3, 3, 3, 3] ]
```

__Notes:__
```
1 < grid.length = grid[0].length <= 50.
All heights grid[i][j] are in the range [0, 100].
All buildings in grid[i][j] occupy the entire grid cell: that is, they are a 1 x 1 x grid[i][j] rectangular prism.
```

## My solution

In order to solve this problem, I start by defining the variable that will store my result (`res`) and assigning a `0` to it. Then I create 2 arrays with the same length of the given grid (`verSky` and `horSky`), which will store the skyline if you look at the buildings vertically and horizontally.

Then, with 2 nested for loops, I go through all the given grid and put the values that I need inside `verSky` and `horSky`. After doing so, the only left thing to do is to calculate the result.

In order to calculate the result, with another 2 nested for loops, I go through all the grid again and then execute this line `res += Math.min(verSky[i], horSky[j]) - grid[i][j];`. What this line does is saying that the new height of the building will be the minimum between `verSky[i]` `horSky[j]`. Then I take this value and I subtract `grid[i][j]` from it, because `grid[i][j]` is the original height.

By doing so, I am getting the maximum increment of height that I can have in each position of the grid in order to not alter the skyline and I am adding it to `res`.

Finally, I return `res` as the final answer.

## Code

- Language: Java

```java
class Solution {
    public int maxIncreaseKeepingSkyline(int[][] grid) {
        int res = 0;
        int[] verSky = new int [grid.length];
        int[] horSky = new int [grid.length];

        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid.length; j++) {
                verSky[i] = Math.max(verSky[i], grid[i][j]);
                horSky[j] = Math.max(horSky[j], grid[i][j]);
            }
        }

        for (int i = 0; i < grid.length; i++)
            for (int j = 0; j < grid.length; j++)
                res += Math.min(verSky[i], horSky[j]) - grid[i][j];

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N<sup>2</sup>)_
- _Space Complexity: O(N)_
