- it is a stable sorting algorithm as it preserves the order of the array

# Steps
1. initialize a **hashmap** to store the **frequency** of each element in **array** 
2. find the **minimum** and **maximum** element in the array
3. iterate **values** from **min** element to **max** element including the max element 
4. check if the value is present in the **hashmap**
5. if yes, then while the **frequency is not 0**, using a `index = 0` variable add the values to input array and increment index whilst decrementing the frequency
6. return the input array

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