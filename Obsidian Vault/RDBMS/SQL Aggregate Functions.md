function that performs calculation on a set of values, then returns single value

- `MIN()` - returns the smallest value within the selected column
  ```SQl
    SELECT MIN(_column_name_)  
	FROM _table_name_  
	WHERE _condition_;
```
- `MAX()` - returns the largest value within the selected column
  ```SQL
    SELECT MAX(_column_name_)  
	FROM _table_name_  
	WHERE _condition_;
```
- `COUNT()` - returns the number of rows in a set
- `SUM()` - returns the total sum of a numerical column
- `AVG()` - returns the average value of a numerical column