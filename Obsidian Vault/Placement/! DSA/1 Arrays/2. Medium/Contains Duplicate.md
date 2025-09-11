#Arrays 
Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]
**Output:** true

**Example 2:**

**Input:** nums = [1,2,3,4]
**Output:** false

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]
**Output:** true

### Brute Forcing (Results in TLE error for larger arrays)
- initiate a nested loop with i and j
- compare values at i and j and return true whenever both values are same
- Time Complexity : O(n^2)

### Sorting and Comparing Adjacent Elements
- sort the array (sort function is present in Java, C++ and python)
- initialize a single loop with i = 1 and compare the elements at i and i+1 (or vice versa, adjust as needed). Just compare adjacent elements
- If both elements are the same return true else false
- Time Complexity : O(n log n )
```cpp
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        for (int i = 1; i < n; i++) {
            if (nums[i] == nums[i - 1])
                return true;
        }
        return false;
    }
};
```

### Hash Set
- 