### **Intuition:** 

Here, the idea is to use the Binary Search algorithm to optimize the approach. The primary objective of Binary Search is to efficiently determine the appropriate half to eliminate, thereby reducing the search space by half. It achieves this by identifying a specific condition that ensures the target is not present in that half. Now, let’s observe how to apply binary search in this problem. First, we'll solve the problem where the sum of the sizes of both arrays is even; we'll consider the odd case later.

**Observation:** Assume, n = sum of size of both the arrays. Characteristics of each half is that it contains (n/2) elements. Each half contains x elements from the first array and [(n/2)-x] elements from the second array. The value of x might be different for the two halves. The unique configuration of halves: Considering different values of x, one can get different left and right halves(x = the number of elements taken from the first array for a particular half). Some different configurations for the above example are shown below: Median creates a partition on the final merged array: Upon closer observation, we can easily show that the median divides the final merged array into two halves. For example, **How to solve the problem using the above observations:**

1. For a valid merged array, the configurations of the two halves are unique. So, we can try to form the halves with different values of x, where x = the number of elements taken from arr1[] for a particular half.
2. There's no need to construct both halves. Once we have the correct left half, the right half is automatically determined, consisting of the remaining elements not yet considered. Therefore, our focus will solely be on creating the unique left half.
3. How to form all configurations of the left half: We know that the left half will surely contain x elements from arr1[] and (n/2)-x elements from arr2[]. Here the only variable is x. The minimum possible value of x is 0 and the maximum possible value is n1(i.e. The length of the considered array).
4. For all the values,[0, n1] of x, we will try to form the left half and then we will check if that half’s configuration is valid.

  
**Check if the formed left half is valid:**

1. For a valid left half, the merged array will always be sorted. So, if the merged array containing the formed left half is sorted, the formation is valid. How to check if the merged array is sorted without forming the array: In order to check we will consider 4 elements, i.e. l1, l2, r1, r2.
2. l1 = the maximum element belonging to arr1[] of the left half.
3. l2 = the maximum element belonging to arr2[] of the left half.
4. r1 = the minimum element belonging to arr1[] of the right half.
5. r1 = the minimum element belonging to arr2[] of the right half.

  
**How to apply binary search to form the left half:**

1. We will check the formation of the left half for all possible values of x. Now, we know that the minimum possible value of x is 0 and the maximum is n1(i.e. The length of the considered array). Now the range is sorted. So, we will apply the binary search on the possible values of x i.e. [0, n1].

  
**How to eliminate the halves based on the values of x:**

1. Binary search works by eliminating the halves in each step. Upon closer observation, we can eliminate the halves based on the following conditions:
2. If l1 > r2: This implies that we have considered more elements from arr1[] than necessary. So, we have to take less elements from arr1[] and more from arr2[]. In such a scenario, we should try smaller values of x. To achieve this, we will eliminate the right half (high = mid-1).
3. If l2 > r1: This implies that we have considered more elements from arr2[] than necessary. So, we have to take less elements from arr2[] and more from arr1[]. In such a scenario, we should try bigger values of x. To achieve this, we will eliminate the left half (low = mid+1).

  
![](https://static.takeuforward.org/premium/Binary%20Search/FAQs/Median%20of%202%20sorted%20arrays/image1-RBcAGXBm)  
**Until now, we have learned how to use binary search but with the assumption that (n1+n2) is even. Let’s generalize this.**

1. If (n1+n2) is odd: In the case of even, we have considered the length of the left half as (n1+n2) / 2. In this case, that length will be (n1 + n2 + 1) / 2. This much change is enough to handle the case of odd. The rest of the things will be completely the same. As in the code, division refers to integer division, this modified formula (n1+n2+1) / 2 will be valid for both cases of odd and even.

  
**What will be the answer i.e. the median:**

1. If l1 <= r2 && l2 <= r1: This condition assures that we have found the correct elements.
2. If (n1+n2) is odd: The median will be max(l1, l2). Otherwise, median = (max(l1, l2) + min(r1, r2)) / 2.0

  
**Note:** We are applying binary search on the possible values of x i.e. [0, n1]. Here n1 is the length of arr1[]. Now, to further optimize it, we will consider the smaller array as arr1[]. So, the actual range will be [0, min(n1, n2)].

### **Approach:** 

1. First, make sure that the arr1 is the smaller array. If not by default, just swap the arrays. Our main goal is to consider the smaller array as arr1[]. Calculate the length of the left half as (n1+n2+1) / 2.
2. Initialize two pointers: low and high, low will point to 0 and the high will point to n1(i.e. The size of arr1). Calculate the ‘mid1’ i.e. x and ‘mid2’ i.e. [left-x]. Now, inside the loop, calculate the value of ‘mid1’ using the following formula, mid1 = (low+high) // 2 ( ‘//’ refers to integer division) and mid2 = left-mid1.
3. Calculate l1, l2, r1, and r2: Generally,

4. l1 = arr1[mid1-1]
5. l2 = arr2[mid2-1]
6. r1 = arr1[mid1]
7. r2 = arr2[mid2]

8. The possible values of ‘mid1’ and ‘mid2’ might be 0 and n1 and n2 respectively. So, to handle these cases, store some default values for these four variables. The default value for l1 and l2 will be INT_MIN and for r1 and r2, it will be INT_MAX.
9. Eliminate the halves based on the following conditions:
10. If l1 is less than or equal to r2 and l2 less than or equal to r1, the answer has been found.
    1. If sum of size of the arrays is odd, return the median as maximum of (l1, l2). Otherwise, return median as the average of max(l1, l2)+min(r1, r2).
11. If l1 is greater than r2. This implies that more elements from arr1 have been considered than needed. So, try to take less elements from arr1 and more from arr2. In such a scenario, take smaller values of x. To achieve this, eliminate the right half (high = mid1-1).
12. If l2 greater than r1. This implies that we have considered more elements from arr2 than needed. So, try to take less elements from arr2 and more from arr1. In such a scenario, take bigger values of x. To achieve this, eliminate the left half (low = mid1+1).
13. Finally, outside the loop, include a dummy return statement just to avoid warnings or errors.

  

![Image 1](https://static.takeuforward.org/premium/Binary%20Search/FAQs/Median%20of%202%20sorted%20arrays/1.png-jN5z8oXb)

![Image 2](https://static.takeuforward.org/premium/Binary%20Search/FAQs/Median%20of%202%20sorted%20arrays/2.png-U2wKvA9E)

![Image 3](https://static.takeuforward.org/premium/Binary%20Search/FAQs/Median%20of%202%20sorted%20arrays/3.png-oL48E9Qj)


```cpp
class Solution {
public:
    double findMedianSortedArrays(vector<int>& A, vector<int>& B) {
        int na = int(A.size()), nb = int(B.size());
        int n = na + nb;
        if (n % 2) {
            return solve(A, B, n / 2, 0, na - 1, 0, nb - 1);
        } else {
            return 1.0 *
                   (solve(A, B, n / 2 - 1, 0, na - 1, 0, nb - 1) +
                    solve(A, B, n / 2, 0, na - 1, 0, nb - 1)) /
                   2;
                   /// average = 1.0*(a + b)/2  | 1.0 is used to typecast to float
        }
    }
    int solve(vector<int>& A, vector<int>& B, int k, int aStart, int aEnd,
              int bStart, int bEnd) {
        // If the segment of on array is empty, it means we have passed all
        // its element, just return the corresponding element in the other
        // array.
        if (aEnd < aStart) {
            return B[k - aStart];
        }
        if (bEnd < bStart) {
            return A[k - bStart];
        }

        // Get the middle indexes and middle values of A and B.
        int aIndex = (aStart + aEnd) / 2, bIndex = (bStart + bEnd) / 2;
        int aValue = A[aIndex], bValue = B[bIndex];

        // If k is in the right half of A + B, remove the smaller left half.
        if (aIndex + bIndex < k) {
            if (aValue > bValue) {
                return solve(A, B, k, aStart, aEnd, bIndex + 1, bEnd);
            } else {
                return solve(A, B, k, aIndex + 1, aEnd, bStart, bEnd);
            }
        }
        // Otherwise, remove the larger right half.
        else {
            if (aValue > bValue) {
                return solve(A, B, k, aStart, aIndex - 1, bStart, bEnd);
            } else {
                return solve(A, B, k, aStart, aEnd, bStart, bIndex - 1);
            }
        }
        return -1;
    }
};
```