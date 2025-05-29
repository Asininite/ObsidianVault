- it is a stable sorting algorithm as it preserves the order of the array

# Steps
1. find maximum element from array `max` 
2. initialize `countArray[]` with all 0s and length `max+1`
3. store count of each element in array at respective indices
	   store number of 2s at `2`
	   store number of 0s at `0` index
4. store cumulative sum/ prefix sum by using `countArray[i] = countArray[i-1] + countArray[i]`
5. iterate from **end of input array** to preserve order of elements