# Problem Description
```
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
```

## Samples

### Example 1
- **Input:** nums = [1,2,3,1]
- **Output:** true

### Example 2
- **Input:** nums = [1,2,3,4]
- **Output:** false

### Example 3
- **Input:** nums = [1,1,1,3,3,4,3,2,4,2]
- **Output:** true

## Constraints
- 1 <= nums.length <= 105
- -109 <= nums[i] <= 109

## Solution 1
```java
    public boolean containsDuplicate(int[] nums) {
        Arrays.sort(nums);
        for(int i=1; i<nums.length; i++){
            if(nums[i] == nums[i-1]){
                return true;
            }
        }
        return false;
    }
```

## Time and Space Complexity
- ** Time Complexity ** : O(nlogn)
- ** Space Complexity ** : O(1)


## Solution 2
```java
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> s = new HashSet<>();
        for(int i : nums){
            s.add(i);
        }
        return s.size() != nums.length;
    }
```

## Time and Space Complexity
- ** Time Complexity ** : O(n)
- ** Space Complexity ** : O(n)


## Solution 3 - Most Ideal
```java
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> s = new HashSet<>();
        for(int i : nums){
            if(!s.add(i)){
                return true;
            }
        }
        return false;
    }
```

## Time and Space Complexity
- ** Time Complexity ** : O(n)
- ** Space Complexity ** : O(n)


## Observations
- In Solution 2 even if you find duplicate on second element, you will be iterating over entire array
- In Solution 3, the moment you find duplicate you will return.