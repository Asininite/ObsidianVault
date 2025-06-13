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
#include <bits/stdc++.h>
using namespace std;

vector<int> countSort(vector<int>& inputArray){
	int N = inputArray.size();
	
	int M = 0
	for (int i = 0; i < N; i++){
		M = max(M, inputArray[i]);
	}

	vector<int> countArray(M+1, 0);

// we map the number of times each element in inputArray occurs by inputting that into countArray as the index and incrementing that using ++

	for(int i = 0; i < N; i++){
		countArray[inputArray[i]]++;
	}

//calculating prefix sum at every index of countArray[]

	for(int i = 0; i < M+1; i++){
		countArray[i] += countArray[i-1]; //similar to countArray[i] = countArray[i] + countArray[i-1];
	}

	vector<int> outputArray(N);

	for(int i = N-1; i >= 0; i--){
		outputArray[countArray[inputArray[i]] - 1] = inputArray[i];
		countArray[inputArray[i]]--;
    }

    return outputArray;
}




```