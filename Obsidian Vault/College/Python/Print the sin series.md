###  Print the sin series x-x^3/3!+x^5/5!....x^n/n! ( read n.)
```python
def series(x, n):
	result = 0
	sign = 1

	for i in range(1, n+1, 2):
		term = (x**i)/math.factorial(i)
		result += sign * term
		sign *= -1
	return result

x = float(input("enter the value of x"))
n = int(input("enter the value of n"))

value = series(x, n)
print(f"the value of sin({x}) using {n} terms is : {value}")
```