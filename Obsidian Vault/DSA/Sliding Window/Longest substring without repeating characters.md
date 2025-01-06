O(2n) solution [ since we traverse the string twice using the two pointers in the worst case scenario]
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if(s.size() == 0){
            return 0;
        }
        
        int maxans = INT_MIN;
        int l = 0;
        unordered_set <int> set;
        
        for(int r = 0; r < s.size(); r++){
            if(set.find(s[r]) != set.end()){
                while(l<r && set.find(s[r]) != set.end()){
                    set.erase(s[l]);
                    l++;
                }
            }
            
            set.insert(s[r]);
            maxans = max(maxans, r - l + 1);
        }
        return maxans;
    }
};
```


O(n) solution
```cpp
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        unordered_map<char, int> map; // Use the declared map variable 'mapp'
        int start = 0, len = 0;
  
        for (int i = 0; i < s.size(); i++) {
            char c = s[i];
            
            if (mapp.count(c) && map[c] >= start) {
                start = map[c] + 1;
            }
            
            len = max(len, i - start + 1);
            map[c] = i; // Update the map with the latest index of the character
        }
        return len;
    }
};
```