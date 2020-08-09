
## Problem

[1476 - Subrectangle Queries](https://leetcode.com/problems/subrectangle-queries/)

## Problem Description

Implement the class `SubrectangleQueries` which receives a `rows x cols` rectangle as a matrix of integers in the constructor and supports two methods:

1. `updateSubrectangle(int row1, int col1, int row2, int col2, int newValue)`

Updates all values with `newValue` in the subrectangle whose upper left coordinate is `(row1,col1)` and bottom right coordinate is `(row2,col2)`.

2. `getValue(int row, int col)`

Returns the current value of the coordinate `(row,col)` from the rectangle.

__Example 1:__
```
Input
["SubrectangleQueries","getValue","updateSubrectangle","getValue","getValue","updateSubrectangle","getValue","getValue"]
[[[[1,2,1],[4,3,4],[3,2,1],[1,1,1]]],[0,2],[0,0,3,2,5],[0,2],[3,1],[3,0,3,2,10],[3,1],[0,2]]
Output
[null,1,null,5,5,null,10,5]
Explanation
SubrectangleQueries subrectangleQueries = new SubrectangleQueries([[1,2,1],[4,3,4],[3,2,1],[1,1,1]]);  
// The initial rectangle (4x3) looks like:
// 1 2 1
// 4 3 4
// 3 2 1
// 1 1 1
subrectangleQueries.getValue(0, 2); // return 1
subrectangleQueries.updateSubrectangle(0, 0, 3, 2, 5);
// After this update the rectangle looks like:
// 5 5 5
// 5 5 5
// 5 5 5
// 5 5 5
subrectangleQueries.getValue(0, 2); // return 5
subrectangleQueries.getValue(3, 1); // return 5
subrectangleQueries.updateSubrectangle(3, 0, 3, 2, 10);
// After this update the rectangle looks like:
// 5   5   5
// 5   5   5
// 5   5   5
// 10  10  10
subrectangleQueries.getValue(3, 1); // return 10
subrectangleQueries.getValue(0, 2); // return 5
```

__Example 2:__
```
Input
["SubrectangleQueries","getValue","updateSubrectangle","getValue","getValue","updateSubrectangle","getValue"]
[[[[1,1,1],[2,2,2],[3,3,3]]],[0,0],[0,0,2,2,100],[0,0],[2,2],[1,1,2,2,20],[2,2]]
Output
[null,1,null,100,100,null,20]
Explanation
SubrectangleQueries subrectangleQueries = new SubrectangleQueries([[1,1,1],[2,2,2],[3,3,3]]);
subrectangleQueries.getValue(0, 0); // return 1
subrectangleQueries.updateSubrectangle(0, 0, 2, 2, 100);
subrectangleQueries.getValue(0, 0); // return 100
subrectangleQueries.getValue(2, 2); // return 100
subrectangleQueries.updateSubrectangle(1, 1, 2, 2, 20);
subrectangleQueries.getValue(2, 2); // return 20
```


## My solution
The first thing that I thought about this problem was the best data structure to use in this case. I think that in this case a matrix was the most adequate data structure, more than a map or even a list of lists.

Once I decided which data structure to use, I implemented a brute force algorithm in order to do the update query. This approach is formed by 2 nested for loops which change the old value of the given section to the new value.

For the other function, the get function just returns the value in the matrix in the given position.


## Code

- Language: Java

```java
class SubrectangleQueries {

    private int[][] rectangle;

    public SubrectangleQueries(int[][] rectangle) {
        this.rectangle = rectangle;
    }

    public void updateSubrectangle(int row1, int col1, int row2, int col2, int newValue) {
        for (int i = row1; i <= row2; i++) {
            for (int j = col1; j <= col2; j++) {
                this.rectangle[i][j] = newValue;
            }
        }
    }

    public int getValue(int row, int col) {
        return rectangle[row][col];
    }
}
```

## Complexity Analysis
__getValue__
- _Time Complexity: O(1)_
- _Space Complexity: O(1)_

__updateSubrectangle__
- _Time Complexity: O(N * M)_
- _Space Complexity: O(1)_
