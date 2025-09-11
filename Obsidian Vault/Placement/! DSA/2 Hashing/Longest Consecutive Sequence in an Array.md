Given an array nums of n integers, return the length of the **longest sequence** of consecutive integers. The integers in this sequence can appear in any order.

Examples:

Input: nums = [100, 4, 200, 1, 3, 2]

Output: 4

Explanation: The longest sequence of consecutive elements in the array is [1, 2, 3, 4], which has a length of 4. This sequence can be formed regardless of the initial order of the elements in the array.

Input: nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]

Output: 9

Explanation: The longest sequence of consecutive elements in the array is [0, 1, 2, 3, 4, 5, 6, 7, 8], which has a length of 9.


### Approach
1. First we initialize a hashset or unordered_set and store all the array elements in it
2. we optimize for the search by discarding anything that is **not** the start of a sequence
	   aka in 2 1 3 4, 2 cannot start a sequence since 2 - 1 == 1 exists and 4 cannot since 4 - 1 == 3 exists
	   so we search in the set until we find one that **can start** a sequence
3. when we find one, we initialize a count variable to keep track of the next consecutive element, if we find them in the set
4. ans is the max of the count and the previous ans which we stored

```cpp
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int longest = 1;
        set<int> st;

        if(nums.size() < 2){
            return nums.size();
        }

        for(auto& val : nums){
            st.insert(val);
        }

        for(auto it : nums){
            if(st.find(it-1) == st.end()){
                int count = 1;
                int x = it + 1;
                while(st.find(x) != st.end()){
                    x++;
                    count++;
                }

                longest = max(longest,count);
            }
        }
        return longest;
    }
};
```