```
#include <vector>

std::vector<int> numbers;
std::vector<std::string> words(5);
std::vector<double> prices{11.52, 22.43, 22.33};

// Accessing elements:
	cout << "First element: " << numbers[0] << endl; 
	cout << "Third element: " << numbers.at(2) << endl; 
	cout << "Last element: " << numbers.back() << endl;

// Adding elements (at the end):
    numbers.push_back(6);
    numbers.push_back(7);

// Inserting at a specific position (at index 2 in this case)
    numbers.insert(numbers.begin() + 2, 99);  // Insert 99 at index 2

// Size of the vector (number of elements):
    cout << "Size: " << numbers.size() << endl;  

// Removing the last element
    numbers.pop_back();

// Sorting the vector (using std::sort algorithm):
    sort(numbers.begin(), numbers.end());

// Iterating through the vector (modern approach with a range-based for loop):
    for (int num : numbers) {
        cout << num << " "; 
    } 

```