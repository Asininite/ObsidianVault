There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

**Input:** nums = [4,5,6,7,0,1,2], target = 0
**Output:** 4

In binary search we can discard half of the sorted array bcus both halves are sorted. Here that may not be the case. 
![[Pasted image 20240923182607.png]]
If mid is larger than nums[left] that means left array is sorted

![[Pasted image 20240923182747.png]]
If mid is smaller than nums[right] it means the right sub-array is sorted 

- Initialize two pointers left = 0 and right = n - 1, where n = nums.size()
- while left <= right (basic binary search), we open the while looop
- initialize mid = left + (right - left)/2 and 
  CASE 1 check if nums[mid] is the target, if yes return
- CASE 2 we check if mid element >= left element. 
  If yes we check if the target >= left AND target < mid. If yes, initialize new right to mid-1 (mid aint the target as we had checked). If no, initialize new left to mid + 1 (to check the other subarray as this array doesnt have target)
 - CASE 3 we dont have to check that mid <= right, we know it to be the sorted array
   we check if target >= mid AND target < right. If yes, initialize new left = mid + 1. 
   Else, we go to other subarray by initializing right = mid - 1
   
- This repeats until left is not <= right OR nums[mid] is target
  We put a return -1 outside all segments for edge cases
  
  ```cpp
  class Solution {
public:
    int search(vector<int>& nums, int target) {
        int n = nums.size();
        int left = 0, right = n - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            // Case 1: Find target
            if (nums[mid] == target) {
                return mid;
            }
            // Case 2: Subarray on mid's left is sorted
            else if (nums[mid] >= nums[left]) {
                if (target >= nums[left] && target < nums[mid]) {
                    right = mid - 1;
	                } else {
                    left = mid + 1;
                }
            }
            // Case 3: Subarray on mid's right is sorted
            else {
                if (target <= nums[right] && target > nums[mid]) {
                    left = mid + 1;
                } else {
                    right = mid - 1;
                }
            }
        }
        return -1;
    }
};
```