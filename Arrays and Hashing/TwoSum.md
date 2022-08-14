# Problem Description

```
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

```

## Samples

### Example 1
- **Input:** nums = [2,7,11,15], target = 9
- **Output:** [0,1]
- **Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

### Example 2
- **Input:** nums = [3,2,4], target = 6
- **Output:** [1,2]
- **Explanation:** Because nums[1] + nums[2] == 6, we return [1, 2].

### Example 3
- **Input:** nums = [3,3], target = 6
- **Output:** [0,1]
- **Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

## Constraints
- 2 <= nums.length <= 104
- -109 <= nums[i] <= 109
- -109 <= target <= 109
- Only one valid answer exists.

## Solution
```java
    public int[] twoSum(int[] nums, int target) {
        int[] res = new int[2];
        if(nums == null || nums.length == 0){
            return res;
        }
        Map<Integer, Integer> map = new HashMap<>();
        for(int i=0; i<nums.length; i++){
            if(map.containsKey(target-nums[i])){
                res[0] = map.get(target-nums[i]);
                res[1] = i;
                break;
            }
            map.put(nums[i], i);
        }
        return res;
    }
```

## Observations
- There is always one solution exist
- Order of index is not a concern
- You can use either ``` target-nums[i]``` as key in map or ```nums[i]```. Based on what you choose as key the
    map assignment in line 46 will change.


## Time and Space Complexity

- ** Time Complexity ** - O(n)
- ** Space Complexity ** - O(n)