```python
new_list = [expression_for_loop_or_one_or_more_conditions]

numbers = [1,2,3,4]
squares = []
for n in numbers:
	squares.append(n**2)

#using LIST COMPREHENSION
squares = [n**2 for n in numbers]
```