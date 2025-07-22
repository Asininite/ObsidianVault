13 -> 1 1 0 1

- convert integer to binary
```cpp
#include <bits/stdc++.h>
using namespace std;
class Solution{
public:
	string IntToBinary(int number){
		if(number == 0) return "0";
		
		int n = number;
		string result = "";
		while(n > 0){
			if(n%2 == 1){
				result += "1";
			} else {
				result += "0";
			}
				
			n = n/2;
	
		}
		int l = 0;
		int r = result.size() -1;
		
		while(l < r){
			swap(result[l], result[r]);
			l++;
			r--;
		}
		return result;
	}
};
```

### 1s Complement
- 1 1 0 1 -> 0 0 1 0
### 2s Complement
- add 1 to 1s complement
- 1 1 0 1 -> 0 0 1 1
### AND Operator
- all true -> true
- 1 false -> false
### OR Operator
- 1 true -> true
- all false -> false
### XOR Operator
- odd no: of 1s -> 1
- even no: of 1s -> 0

### Right Shift
- >> 
  13 >> 1
  1 1 0 1 -> 0 1 1 0