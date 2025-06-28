- Data Structures, DBMS, OOPS, CN
- implement basic data structures
- write queries to fetch data from database
- **implement file system using a tree in the form of a class with all required operations and methods**
	  - what are different HTTP methods
	  - SQL Queries based on project
	  - implement stack and queue with operations
	  - operations on linked lists and merge two sorted linked lists into single sorted linked list
	  - simulate file system using tree data structure
---
- theory taught in class
- code up questions based on strings and arrays
- SQL Queries and OOPS Concepts
- Popular interview questions
	  - reverse a number but leave the zeros in place

```cpp
class Solution{
public:
	int reverseArray(int num){
		vector<int> arr;
		int digit;
		while(num > 0){
			digit = num%10;
			num = num/10;
			arr.push_back(digit);
		}
		
		int l = 0;
		int r = arr.size() - 1;
		int ans = 0;
		while(l < r){
			if(arr[l] == 0){
				l++;
			} else if(arr[r] == 0){
				r--;
			} else {
				swap(arr[l], arr[r]);
				l++;
				r--:
			}
		}
		
		for(int i = 0; i < arr.size(); i++){
			ans = ans*10 + arr[i];
		}
		
		return ans;
	}
}
```