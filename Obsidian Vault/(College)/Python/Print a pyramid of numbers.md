print this
```

1 
1 2 
1 2 3 
1 2 3 4 
1 2 3 4 5 
* 
* * 
* * * 
* * * * 
* * * * *
```

```python
n = 5
for i in range(1,n+1):
  for j in range(1, i+1):
    print(j,end=" ")
  print()

print()

for i in range(1, n+1):
  for j in range(1, i+1):
    print('*', end=" ")
  print()
```