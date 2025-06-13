- it is a stable sorting algorithm as it preserves the order of the array

# Steps
1. find maximum element from array `max` 
2. initialize `countArray[]` with all 0s and length `max+1`
3. store count of each element in array at respective indices
	   eg :
		   store number of 2s at `2`
		   store number of 0s at `0` index
4. store cumulative sum/ prefix sum by using `countArray[i] = countArray[i-1] + countArray[i]`
5. iterate from **end of input array** to preserve order of elements

## Counting Sort Algorithm:
- Declare an auxiliary array ***countArray[]*** of size ***max(inputArray[])+1*** and initialize it with ****0****.
- Traverse array **inputArray[]*** and map each element of ***inputArray[]** as an index of **countArray[]*** array, i.e., execute ***countArray[inputArray[i]]++*** for **0 <= i < N**.
- Calculate the prefix sum at every index of array **inputArray**[].
- Create an array **outputArray[]*** of size **N**.
- Traverse array **inputArray[]** from end and update **outputArray[ countArray[ inputArray[i] ] - 1] = inputArray[i]****. Also, update **countArray[ inputArray[i] ] = countArray[ inputArray[i] ]- -**** 

```cpp
class Solution {
    void countingSort(vector<int> &arr) {
        // Create the counting hash map.
        unordered_map<int, int> counts;
        // Find the minimum and maximum values in the array.
        int minVal = *min_element(arr.begin(), arr.end());
        int maxVal = *max_element(arr.begin(), arr.end());

        // Update element's count in the hash map.
        for (auto& val : arr) {
            counts[val]++;
        }
        
        int index = 0;
        // Place each element in its correct position in the array.
        for (int val = minVal; val <= maxVal; ++val) {
            // Append all 'val's together if they exist.
            if (counts.find(val) != counts.end()) {
                while (counts[val] > 0) {
                    arr[index] = val;
                    index += 1;
                    counts[val] -= 1;
                }
            }
        }
    }

public:
    vector<int> sortArray(vector<int>& nums) {
        countingSort(nums);
        return nums;
    }
};

```