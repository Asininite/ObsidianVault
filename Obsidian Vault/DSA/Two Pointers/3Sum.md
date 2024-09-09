Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

**Example 1:**

```
**Input:** nums = [-1,0,1,2,-1,-4]
**Output:** [[-1,-1,2],[-1,0,1]]
**Explanation:** 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```


### Solution
- We first sort the numbers index and initialize a result vector of int vectors `vector<vector<int>>`
- Three indices is hard, so we fix one index (i at 0) and use a for loop to keep iterating i
- We can't have duplicates, so we check if `i>0` and ``numbers[i] == numbers[i-1]`` If yes, we use a `continue` statement that skips this loop iteration and jumps to next value of i
- Inside the i for loop, we initialize `j = i + 1` for second element and `k = numbers.size() - 1` for second index and last index
- we then iterate for j and k
- while `j < k`, we create a total integer and `total = nums[i] + nums[j] + nums[k]` This total is then checked
- if `total > 0` means we have to decrement k to bring down the total to possibly zero.
  `if total > 0 {
	  `k--;`
	`}`
- if `total < 0` we have to increment j to bring up j and increase value to zero
`if total < 0 {j++;}
- if total is exactly zero, we `push_back` `nums[i] nums[j] nums[k]` to result vector, and increment j
- if `nums[j] == nums[j-1] && j < k` aka the next index of j is the same as previous index we try to skip it by incrementing j
  `if(nums[j] == nums[j-1] && j < k) {j++;}`
- We return `result`

```
class Solution {

public:

    vector<vector<int>> threeSum(vector<int>& nums) {

        vector<vector<int>> res;

        sort(nums.begin(), nums.end());

  

        for (int i = 0; i < nums.size(); i++) {

            if (i > 0 && nums[i] == nums[i-1]) {

                continue;

            }

            int j = i + 1;

            int k = nums.size() - 1;

  

            while (j < k) {

                int total = nums[i] + nums[j] + nums[k];

  

                if (total > 0) {

                    k--;

                } else if (total < 0) {

                    j++;

                } else {

                    res.push_back({nums[i], nums[j], nums[k]});

                    j++;

  

                    while (nums[j] == nums[j-1] && j < k) {

                        j++;

                    }

                }

            }

        }

        return res;        

    }

};
```