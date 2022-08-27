# Problem Description

```
Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
```

## Samples

### Example 1
- **Input:** strs = ["eat","tea","tan","ate","nat","bat"]
- **Output:** [["bat"],["nat","tan"],["ate","eat","tea"]]
- **Explanation:** 

### Example 2
- **Input:**  strs = [""]
- **Output:** [[""]]
- **Explanation:** 

### Example 3
- **Input:** strs = ["a"]
- **Output:** [["a"]]
- **Explanation:** 

## Constraints


## Solution
```java
   public List<List<String>> groupAnagrams(String[] strs) {
        if(strs.length == 0) return new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();
        for(String s : strs){
            char[] arr = new char[26];
            for(char ch : s.toCharArray()){
                arr[ch-'a']++;
            }
            String key = String.valueOf(arr);
            if(!map.containsKey(key)){
                map.put(key, new ArrayList<>());
            }
            map.get(key).add(s);
        }
        return new ArrayList<>(map.values());
    } 
```

## Observations
- 


## Time and Space Complexity
- ** Time Complexity ** : O (m*n) m -> strs length and n -> length of each string
- ** Space Complexity ** : O(m)