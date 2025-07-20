## Description

You are given an array non-negative integers `height` which represent an elevation map. Each value `height[i]` represents the height of a bar, which has a width of `1`.

Return the maximum area of water that can be trapped between the bars.

**Example 1:**

![](https://imagedelivery.net/CLfkmk9Wzy8_9HRyug4EVA/0c25cb81-1095-4382-fff2-6ef77c1fd100/public)

```java
Input: height = [0,2,0,3,1,0,1,3,2,1]

Output: 9
```

Copy

**Constraints:**

- `1 <= height.length <= 1000`
- `0 <= height[i] <= 1000`

---


### Core Idea

The amount of rainwater that can be trapped above any single bar is determined by the "walls" on its left and right. Specifically, the water level can only rise to the height of the **shorter** of the two walls.

The two "walls" for any given bar at index `i` are:
1.  The tallest bar to its left (`max_left`).
2.  The tallest bar to its right (`max_right`).

Therefore, the water trapped above bar `i` is: `min(max_left, max_right) - height[i]`. This value is only added if it's positive. The total trapped water is the sum of these values for all bars.

---

### Two Main Approaches

The video explains two efficient ways to implement this logic:

#### 1. Pre-computation Approach (O(n) Time, O(n) Space)

This is a more intuitive, multi-pass solution:
1.  **Create a `max_left` array:** Iterate from left to right, pre-computing the tallest bar to the left of each position.
2.  **Create a `max_right` array:** Iterate from right to left, pre-computing the tallest bar to the right of each position.
3.  **Calculate Total:** Iterate through the `height` array a final time. For each bar `i`, calculate the trapped water using the formula `min(max_left[i], max_right[i]) - height[i]` and add it to a running total.

#### 2. Two-Pointer Approach (O(n) Time, O(1) Space)

This is the most optimal solution, using constant extra memory:
1.  **Initialize:** Set a `left` pointer at the start of the array and a `right` pointer at the end. Also, initialize `max_left = 0` and `max_right = 0`.
2.  **Loop:** While `left < right`:
    *   Compare the heights at the pointers: `height[left]` and `height[right]`.
    *   **If `height[left]` is smaller**, process the left side. The `max_left` height is the limiting boundary. Calculate trapped water as `max_left - height[left]` and add it to the total. Then, move the `left` pointer one step to the right.
    *   **Otherwise**, process the right side. The `max_right` height is the limiting boundary. Calculate trapped water as `max_right - height[right]` and add it to the total. Then, move the `right` pointer one step to the left.
3.  **Update Maxes:** In each step, update `max_left` or `max_right` if a new taller bar is encountered.

This works because when we process a pointer (e.g., `left`), we know its `max_left` is smaller than or equal to the `max_right`, making `max_left` the bottleneck for trapping water at that position.

### Brute force
```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        if (height.empty()) {
            return 0;
        }
        int n = height.size();
        int res = 0;

        for (int i = 0; i < n; i++) {
            int leftMax = height[i];
            int rightMax = height[i];

            for (int j = 0; j < i; j++) {
                leftMax = max(leftMax, height[j]);
            }
            for (int j = i + 1; j < n; j++) {
                rightMax = max(rightMax, height[j]);
            }

            res += min(leftMax, rightMax) - height[i];
        }
        return res;
    }
};
```
### prefix and suffix arrays
```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        int n = height.size();
        if (n == 0) {
            return 0;
        }

        vector<int> leftMax(n);
        vector<int> rightMax(n);

        leftMax[0] = height[0];
        for (int i = 1; i < n; i++) {
            leftMax[i] = max(leftMax[i - 1], height[i]);
        }

        rightMax[n - 1] = height[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            rightMax[i] = max(rightMax[i + 1], height[i]);
        }

        int res = 0;
        for (int i = 0; i < n; i++) {
            res += min(leftMax[i], rightMax[i]) - height[i];
        }
        return res;
    }
};
```
### stack
```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        if (height.empty()) {
            return 0;
        }

        stack<int> stk;
        int res = 0;

        for (int i = 0; i < height.size(); i++) {
            while (!stk.empty() && height[i] >= height[stk.top()]) {
                int mid = height[stk.top()];
                stk.pop();
                if (!stk.empty()) {
                    int right = height[i];
                    int left = height[stk.top()];
                    int h = min(right, left) - mid;
                    int w = i - stk.top() - 1;
                    res += h * w;
                }
            }
            stk.push(i);
        }

        return res;
    }
};
```
### Most optimised using left and right pointer
```cpp
class Solution {
public:
    int trap(vector<int>& height) {
        if (height.empty()) {
            return 0;
        }

        int l = 0, r = height.size() - 1;
        int leftMax = height[l], rightMax = height[r];
        int res = 0;
        while (l < r) {
            if (leftMax < rightMax) {
                l++;
                leftMax = max(leftMax, height[l]);
                res += leftMax - height[l];
            } else {
                r--;
                rightMax = max(rightMax, height[r]);
                res += rightMax - height[r];
            }
        }
        return res;
    }
};
```