**Tuple**
- A tuple is an object capable to hold a collection of elements where each element can be of a different type.
- Class template `std::tuple` is a fixed-size collection of heterogeneous values
`tuple<int, int, char> foo(int n1, int n2)`
`{`
    `// Packing values to return a tuple`
    `return` `make_tuple(n2, n1,'a');`             
`}`

**Pair**
- This class couples together a pair of values, which may be of different types
- A pair is a specific case of a std::tuple with two elements
`std::pair<int, int> foo1(int num1, int num2)`
`{`
    `// Packing two values to return a pair` 
    `return` `std::make_pair(num2, num1);`            
`}`

