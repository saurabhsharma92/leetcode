# Problem Description

```
Given an integer array nums and an integer k, return true if there are two distinct indices 
i and j in the array such that nums[i] == nums[j] and abs(i - j) <= k.
```

## Samples

### Example 1
- **Input:** nums = [1,2,3,1], k = 3
- **Output:** true
- **Explanation:** 

### Example 2
- **Input:** nums = [1,0,1,1], k = 1
- **Output:** true
- **Explanation:** 

### Example 3
- **Input:** nums = [1,2,3,1,2,3], k = 2
- **Output:** false
- **Explanation:** 

## Constraints
- 1 <= nums.length <= 105
- -109 <= nums[i] <= 109
- 0 <= k <= 105

## Solution 1 - Brute Force

```txt

Run 2 for loop and check for value at indexes, if they are same then find the difference between the indexes and compare with k
    
```

## Time and Space Complexity
- ** Time Complexity ** : O(n^2)
- ** Space Complexity ** : O(n)


## Solution 2 - Using Map

```java

public boolean containsNearbyDuplicate(int[] nums, int k) {
        Map<Integer, Integer[]> map = new HashMap<>();
        for(int i=0; i <nums.length; i++){
            if(!map.containsKey(nums[i])){
                Integer[] ind = new Integer[2];
                ind[0] = i;
                map.put(nums[i], ind);
            }else{
                Integer[] temp = map.get(nums[i]);
                if(Math.abs(temp[0] - i) <= k){
                    return true;
                }else{
                    temp[0] = i;
                    map.put(nums[i], temp);
                }
            }            
        }
        return false;
    }
    
```
or

```java

public boolean containsNearbyDuplicate(int[] nums, int k) {
        Map<Integer, List<Integer>> map = new HashMap<>();
        for(int i=0; i<nums.length; i++){
            if(map.containsKey(nums[i])){
                List<Integer> temp = map.get(nums[i]);
                temp.add(i);
                map.put(nums[i], temp);
            }else{
                List<Integer> list = new ArrayList<>();
                list.add(i);
                map.put(nums[i], list);
            }
        }
        for(Map.Entry<Integer, List<Integer>> entry : map.entrySet()){
            List<Integer> vals = entry.getValue();
            if(vals.size() > 1){
                for(int i=1; i<vals.size(); i++){
                     if(vals.get(i)-vals.get(i-1) <= k){
                         return true;
                     }
                }
            }
        }
        
        return false;
    }
    
```

Maintain a map with Key as each value of array and for value maintain a list or array to record indices for a given value in array.
Itterate over map and compare the difference between indices for a given value if its less than or equal to k, return true

## Time and Space Complexity
- ** Time Complexity ** : O(n)
- ** Space Complexity ** : O(n)


## Solution 3 - Using Set

```java

public boolean containsNearbyDuplicate(int[] nums, int k) {
    Set<Integer> set = new HashSet<>();
    for(int i=0; i<nums.length; i++){
        if(i > k){
            set.remove(nums[i-k-1]);
        }
        if(!set.add(nums[i])){
            return true;
        }
    }
    return false;
}
    
```

Idea here is to maintain a queue of size k, keep processing new element and if the size of queue increases k, remove the first element. If the same element is present in the queue
at any given time that means the difference between the indices will be less than or equal to k.

## Time and Space Complexity
- ** Time Complexity ** : O(n^2)
- ** Space Complexity ** : O(n)