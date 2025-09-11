```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> commonElements(vector<int> arr1, vector<int> arr2, vector<int> arr3){
	int n1 = arr1.size();
	int n2 = arr2.size();
	int n3 = arr3.size();

	vector<int> common;
	int i = 0, j = 0, k = 0;
	
	while(i < n1 && j < n2 && k < n3){
		if(arr1[i] == arr2[j] == arr3[k]){
			common.push_back(arr[i]);
			i++;
			j++;
			k++;
		
		while (i < n1 && arr1[i] == arr1[i - 1])
                i++;
            while (j < n2 && arr2[j] == arr2[j - 1])
                j++;
            while (k < n3 && arr3[k] == arr3[k - 1])
                k++;
        }
        
        else if (arr1[i] < arr2[j])
            i++;
        else if (arr2[j] < arr3[k])
            j++;
        else
            k++;
    }

    return common;
	}
}
```