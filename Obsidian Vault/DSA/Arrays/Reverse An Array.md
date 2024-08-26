#Arrays
### Using Extra Array (Non In-Place)
- Create another array
- Copy elements from original array to new array in reverse order

`void reverse_array(int arr[], int size){`
	`int reversed_array[size];`
	`for (int i = 0; i < size; i++)`
		`reversed_array[i] = array[size - i - 1];`
`}`	

- Time Complexity : O(n)
- Space Complexity : O(n) `uses another array for storing the reversed array`
### Using a loop (In-Place)
- iterate through array using two pointers
- swap elements at start and end pointers
- move start pointer to end and end pointer to start until they meet or cross each other

`void reverse_array(int arr[], int start, int end){`
	`while (start < end){`
		`int temp = arr[start];`
		`arr[start] = arr[end];`
		`arr[end] = temp;`
		`start++;`
		`end--;`
	`}`
`}`

- Time Complexity : O(n)
- Space Complexity : O(1)

### Using recursion (In or Non-In Place)
- recursive function that takes array as input
- swap first and last elements
- recursively call with the remaining sub-array

`int reverse_subarray(int array[], int start, int end){`
	`if (start >= end){`
		`return;`
	`int temp = arr[start];`
	`arr[start] = arr[end]`
	`arr[end] = temp;`
	`reverse_subarray(arr, start+1, end-1);`

- Time Complexity : O(n)
- Space Complexity : O(n) {Non in-place}, O(log n) {In place due to recursion stack}

### Array Reverse Stack
- push each array element into stack
- pop elements from stack to form array

`void reverseArrayUsingStack(int arr[], int size)
`{
  ``  std::stack<int> stack;

    // Push elements onto the stack
    for (int i = 0; i < size; i++) {
        stack.push(arr[i]);
    }

    // Pop elements from the stack to reverse the array
    for (int i = 0; i < size; i++) {
        arr[i] = stack.top();
        stack.pop();
    }
`}

