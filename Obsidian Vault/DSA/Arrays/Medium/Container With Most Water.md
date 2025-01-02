You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return _the maximum amount of water a container can store_.

**Notice** that you may not slant the container.

```cpp BRUTE FORCE
class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxarea = 0;
        for (int left = 0; left < height.size(); left++) {
            for (int right = left + 1; right < height.size(); right++) {
                int width = right - left;
                maxarea = max(maxarea, min(height[left], height[right]) * width);
            }
        }
        return maxarea;
    }
};
```
- this is inefficient and for larger areas can result in a TLE error. What this does is go through every combination of area of the rectangle

- we can optimize solution by using two pointers, left and right
- left is initialized to first index, right to last
- this will be the widest rectangle, and any movement of pointers will reduce the width
  ![[Pasted image 20250102232522.png]]
- the area is determined by the shortest height, since even if the other height is longer it can only hold water upto the shorter height
	  so if left_height is shorter, we will increment left and bring it towards right since eventhough width decreases, there is a potential for left_height to increase and grab more area
	  if right_height is shorter, we will decrement right and bring it towards left

```cpp
class Solution {
public:
    int maxArea(vector<int>& height) {
        int maxArea = 0;
        int left = 0;
        int right = height.size() - 1;

        while (left < right) {
            int width = right - left;
            maxArea = max(maxArea, min(height[left], height[right]) * width);
            if (height[left] <= height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return maxArea;
    }
};
```