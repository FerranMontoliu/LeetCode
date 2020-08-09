
## Problem

[1282 - Group the People Given the Group Size They Belong To](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)

## Problem Description
There are `n` people whose __IDs__ go from `0` to `n - 1` and each person belongs __exactly__ to one group. Given the array `groupSizes` of length `n` telling the group size each person belongs to, return the groups there are and the people's __IDs__ each group includes.

You can return any solution in any order and the same applies for IDs. Also, it is guaranteed that there exists at least one solution.

__Example 1:__
```
Input: groupSizes = [3,3,3,3,3,1,3]
Output: [[5],[0,1,2],[3,4,6]]
Explanation:
Other possible solutions are [[2,1,6],[5],[0,4,3]] and [[5],[0,6,2],[4,3,1]].
```

__Example 2:__
```
Input: groupSizes = [2,1,3,3,3,2]
Output: [[1],[0,5],[2,3,4]]
```

## My solution

The first approach to this problem could be a brute force solution, but I thought that in this problem, using a _HashMap_ in order to split all the indexes depending on their `groupSize` could be useful.

So in my solution, I start by creating a _Map_ which has an _Integer_ as the _key_ and a _List_ of _Integer_ as the _value_. Then I create the _List_ of _List_ of _Integer_ which will be the result that I will return at the end of the function. I also create an _int_ which is called `gs`, which will store the value `groupSizes[i]` in the following _for loop_ to make the code more understandable, but this _int_ could be removed as it is not essential. I also define a variable called current, which is a _List_ of _Integer_, we will use it later inside the loop, but I create it outside the loop because else I would create a new _List_ at every iteration of the loop. Again, this is not an essential variable, we could create it inside the _for loop_.

Then there is a _for loop_ which iterates through the `groupSizes` array. Inside this loop, I start by checking if the group size that I am currently checking already exists in the _map_ that I created at the beginning. If it doesn't exist as a _key_, I create a new empty _ArrayList_ as the value to this _key_.

After this _if_, I assign the value associated to the key that I am checking to the variable `current`. Then I will add the index that I am checking to it. After this I will check if the `current` list has the size that it must have. If `current.size() == gs`, I will add `current` to `res` and then I will remove the key from the _map_.

This way, if the `current` array is smaller than it should be, we would have added the new index to it because the `current` list has the same reference as the array inside `map`, as it is not a copy of it.


## Code

- Language: Java

```java
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        Map<Integer, List<Integer>> map = new HashMap<>();
        List<List<Integer>> res = new ArrayList<>();
        int gs;
        List<Integer> current;

        for (int i = 0; i < groupSizes.length; i++) {
            gs = groupSizes[i];
            if (!map.containsKey(gs))
                map.put(gs, new ArrayList<>());

            current = map.get(gs);
            current.add(i);

            if (current.size() == gs) {
                res.add(current);
                map.remove(gs);
            }
        }

        return res;
    }
}
```

## Complexity Analysis

- _Time Complexity: O(N)_
- _Space Complexity: O(N*M)_
