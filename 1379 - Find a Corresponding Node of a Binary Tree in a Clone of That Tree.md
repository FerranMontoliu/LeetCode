
## Problem

[1379 - Find a Corresponding Node of a Binary Tree in a Clone of That Tree](https://leetcode.com/problems/find-a-corresponding-node-of-a-binary-tree-in-a-clone-of-that-tree/)

## Problem Description
Given two binary trees `original` and `cloned` and given a reference to a node `target` in the original tree.

The `cloned` tree is a __copy of__ the `original` tree.

Return _a reference to the same node_ in the `cloned` tree.

__Note__ that you are __not allowed__ to change any of the two trees or the `target` node and the answer __must be__ a reference to a node in the `cloned` tree.

__Follow up:__ Solve the problem if repeated values on the tree are allowed.

__Example 1:__
```
Input: tree = [7,4,3,null,null,6,19], target = 3
Output: 3
Explanation: In all examples the original and cloned trees are shown. The target node is a green node from the original tree. The answer is the yellow node from the cloned tree.
```

__Example 2:__
```
Input: tree = [7], target =  7
Output: 7
```

__Example 3:__
```
Input: tree = [8,null,6,null,5,null,4,null,3,null,2,null,1], target = 4
Output: 4
```

__Example 4:__
```
Input: tree = [1,2,3,4,5,6,7,8,9,10], target = 5
Output: 5
```

__Example 5:__
```
Input: tree = [1,2,null,3], target = 2
Output: 2
```


## My solution

In this case, my first approach was to implement a recursive function in order to get to the `target` node while traversing both trees at the same time.

So, for this function I start by thinking which are the _base cases_. In this case I thought that the 2 base cases that could exist were that the `original` node was `null` or that the `original` node was the `target` (assuming that the target node can't be null, which could be another _base case_). If `original == null`, then we will return `null`. If `original == target`, then we will return `cloned`, because the variable `clone` will point to the target node but in the cloned tree.

If this iteration is not a base case, then we will create a new _TreeNode_ called `res` and we will make a recursive call but using the left node of the `original` and the `cloned` trees.

If `res` is `null` after this recursive call, it will mean that the result is not in the left subtree, and then we will check the right subtree by doing another recursive call, but this time we will use the right node of both trees.

Finally, we will return `res` as the answer.

## Code

- Language: Java

```java
class Solution {
    public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
        if (original == null)
            return null;

        if (original == target)
            return cloned;

        TreeNode res = getTargetCopy(original.left, cloned.left, target);

        if (res == null)
            res = getTargetCopy(original.right, cloned.right, target);

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(1)_
