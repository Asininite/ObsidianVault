Given two sorted arrays, the task is to merge them in a sorted manner.  
****Examples:**** 

> ****Input****: arr1[] = { 1, 3, 4, 5}, arr2[] = {2, 4, 6, 8}   
> ****Output****: arr3[] = {1, 2, 3, 4, 4, 5, 6, 8}
> 
> ****Input****: arr1[] = { 5, 8, 9}, arr2[] = {4, 7, 8}   
> ****Output****: arr3[] = {4, 5, 7, 8, 8, 9}

### Use Merge Sort

```cpp
#include <iostream>
#include <vector>
using namespace std;

void mergeArrays(vector<int>& arr1, vector<int>& arr2){
	int i = 0, j = 0, k = 0;
	int n1 = arr1.size();
	int n2 = arr2.size();

	vector<int> arr3(n1+n2);

	while(i < n1 && j < n2){
		if(arr1[i] < arr2[j]){
			arr3[k++] = arr1[i++];
		} else {
			arr3[k++] = arr2[j++];
		}
	}

	while(i < n1){
		arr3[k++] = arr1[i++];
	}
	
	while(j < n2){
		arr3[k++] = arr2[j++];
	}
}
```