# Problem Description

```
Given two strings s and t, return true if t is an anagram of s, and false otherwise.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```

## Samples

### Example 1
- **Input:** s = "anagram", t = "nagaram"
- **Output:** true
- **Explanation:** 

### Example 2
- **Input:** s = "rat", t = "car"
- **Output:** false
- **Explanation:** 

## Constraints
- 1 <= s.length, t.length <= 5 * 104
- s and t consist of lowercase English letters.

## Solution 1 : Using Map
```java
    public boolean isAnagram(String s, String t) {
        Map<Character, Integer> map = new HashMap<>();
        for(char ch : s.toCharArray()){
            map.put(ch, map.getOrDefault(ch, 0)+1);
        }
        
        for(char ch : t.toCharArray()){
            if(map.containsKey(ch)){
                map.put(ch, map.getOrDefault(ch, 0)-1);
            }else{
                map.put(ch, map.getOrDefault(ch, 0)+1);
            }
            
        }
        
        for(Character c : map.keySet()){
            if(map.get(c) > 0){
                return false;
            }
        }
        
        return true;
    }
```

## Observations
- 


## Time and Space Complexity
- ** Time Complexity ** : O(n)
- ** Space Complexity ** : O(n)


## Solution 2 : Using Array

```java
    public boolean isAnagram(String s, String t) {
        public boolean isAnagram(String s, String t) {
        if(s.length() != t.length()) return false;
        int[] arr = new int[26];
        for(int i=0; i<s.length(); i++){
            arr[s.charAt(i)-'a']++;
            arr[t.charAt(i)-'a']--;
        }
        for(int i : arr){
            if(i != 0){
                return false;
            }
        }
        return true;
    }
    }
```

## Observations
- 


## Time and Space Complexity
- ** Time Complexity ** : O(n), where n is length of string s
- ** Space Complexity ** : O(1)
