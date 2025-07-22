13 -> 1 1 0 1

- convert integer to binary
```cpp
class Solution{
public:
	string IntToBinary(int number){
		string result = "";
		while(n > 0){
				if(n%2 == 1){
					result += "1";
				} else {
					result += "0";
				}
				
				n = n/2;
			}
		}
	}
}
```