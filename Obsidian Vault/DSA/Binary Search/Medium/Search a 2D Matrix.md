You are given an `m x n` integer matrix `matrix` with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.

![[Pasted image 20250304011447.png]]
**Input:** `matrix = [[1,3,5,7],[10,11,16,20],[23,30,34,60]]`, target = 3
**Output:** true

## Binary Search

```cpp
class Solution {
public:
	bool searchMatrix(vector<vector<int>>& matrix, int target) {
		int ROWS = matrix.size();
		int COLS = matrix[0].size();
		
		int top = 0, bot = ROWS - 1;
		while (top <= bot){
			int row = (top + bot)/2;
			if (target > matrix[ROWS][COLS - 1]) {
				top = row + 1;
			} else if (target < matrix[row][0]) {
				bot = row - 1;
			}
		}
	}
}
```