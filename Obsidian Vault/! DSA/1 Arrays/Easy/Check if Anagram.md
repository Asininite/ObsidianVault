## Description

Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An **anagram** is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example 1:**

```java
Input: s = "racecar", t = "carrace"

Output: true
```

Copy

**Example 2:**

```java
Input: s = "jar", t = "jam"

Output: false
```

Copy

**Constraints:**

- `s` and `t` consist of lowercase English letters.

```cpp
class Solution {
public:
    bool isAnagram(string s, string t) {
       
		unordered_map <int,int> count;
        if(s.length() != t.length()){
            return false;
        }

        for(auto& val1 : s){
            count[val1]++;
        }

        for(auto& val1 : t){
            count[val1]--;
        }

        for(auto& val : count){
            if(val.second != 0){
                return false;
            }
        }

        return true;
    }
};
```