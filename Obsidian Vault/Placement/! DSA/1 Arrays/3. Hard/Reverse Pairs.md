Given an integer array **nums**. Return the **number** of **reverse pairs** in the array.

An index pair **(i, j)** is called a **reverse** pair if:

- 0 <= i < j < nums.length  
- nums[i] > 2 * nums[j]

Example 1
**Input**: nums = [6, 4, 1, 2, 7]
**Output**: 3
**Explanation**:
The reverse pairs are:
(0, 2) : nums[0] = 6, nums[2] = 1, 6 > 2 * 1
(0, 3) : nums[0] = 6, nums[3] = 2, 6 > 2 * 2
(1, 2) : nums[1] = 4, nums[2] = 1, 4 > 2 * 1

Example 2
**Input**: nums = [5, 4, 4, 3, 3]
**Output**: 0
**Explanation**:
No pairs satisfy both the conditons.

Example 3
**Input**: nums = [6, 4, 4, 2, 2]
Output:
2

Constraints
- 1 <= nums.length <= 5 * 104
- -231 <= nums[i] <= 231 - 1

# Brute
### **Intuition**

The straightforward approach to solve this problem is to iterate through each element in the array and run an inner loop say(j) to check all subsequent elements arr[j], if the condition arr[i] > 2 x arr[j] holds true, where i is the parent loop, then it is a reverse pair otherwise it's not a reverse pair.

### **Approach**

- iterate in the array from 0 to N-1 to select the arr[i]. As index j should be greater than index i, inside loop i, run another loop i.e. j from i+1 to N-1, and select the element arr[j].
- Inside this second loop, check if arr[i] is greater than 2*arr[j] i.e. if arr[i] and arr[j] can be a pair. If they satisfy the condition, increase the count by 1. Finally, return the count as our answer.
  

C++

```cpp
#include <bits/stdc++.h>
using namespace std;

class Solution {
public:
    /* Function to count reverse
    pairs where a[i] > 2 * a[j]*/
    int reversePairs(vector<int>& nums) {
        
        // Call countPairs with the vector and its size
        return countPairs(nums, nums.size()); 
        
    }

private:
    /* Helper function to count pairs
    satisfying the condition a[i] > 2 * a[j]*/
    int countPairs(vector<int>& nums, int n) {
        
        // Initialize count of reverse pairs
        int cnt = 0;
        
        /* Nested loops to check each
        pair (i, j) where i < j*/
        for (int i = 0; i < n; i++) {
            
            for (int j = i + 1; j < n; j++) {
                
                /* Check if the condition 
                a[i] > 2 * a[j] holds*/
                if ((long long)nums[i] > (long long)2 * nums[j]) {
                    
                    /* Increment count if
                    condition is satisfied*/
                    cnt++; 
                    
                }
            }
        }
        // Return the total count of reverse pairs
        return cnt; 
    }
};

int main() {
    
    vector<int> nums = {6, 4, 1, 2, 7}; 
    
    // Create an instance of the Solution class
    Solution sol; 
    
    int cnt = sol.reversePairs(nums); 
    
    // Output the result
    cout << "The number of reverse pairs is: " << cnt << endl;
    return 0; 
}
```

### **Complexity Analysis** 

**Time Complexity:** O(N2), where N is size of the given array. For using nested loops here and those two loops roughly run for N times.  
  
**Space Complexity:** O(1), no extra space is used to solve this problem.

# Optimal
```cpp
class Solution {
public:
    int merge(vector<int>& nums, int low, int mid, int high) {
        int count = 0;
        int j = mid + 1;

        // Count reverse pairs
        for (int i = low; i <= mid; i++) {
            while (j <= high && nums[i] > 2LL * nums[j]) {
                j++;
            }
            count += (j - (mid + 1));
        }

        // Merge step
        vector<int> temp;
        int left = low, right = mid + 1;

        while (left <= mid && right <= high) {
            if (nums[left] <= nums[right]) {
                temp.push_back(nums[left++]);
            } else {
                temp.push_back(nums[right++]);
            }
        }

        while (left <= mid) temp.push_back(nums[left++]);
        while (right <= high) temp.push_back(nums[right++]);

        for (int i = low; i <= high; i++) {
            nums[i] = temp[i - low];
        }

        return count;
    }

    int mergeSort(vector<int>& nums, int low, int high) {
        if (low >= high) return 0;

        int mid = (low + high) / 2;
        int count = 0;

        count += mergeSort(nums, low, mid);
        count += mergeSort(nums, mid + 1, high);
        count += merge(nums, low, mid, high);

        return count;
    }

    int reversePairs(vector<int>& nums) {
        return mergeSort(nums, 0, nums.size() - 1);
    }
};
```
