##### 1. Create a Point class to handle a point (x,y). Use a constructor to initialize the Point( default (0,0)). Use __str__ function to display the point object using print function. Overload + ,- and < operator using appropriate function.
```python
import math

class Point:
    def __init__(self, x=0, y=0):
        self.x = x
        self.y = y
        
    def __str__(self):
        return f"({self.x}, {self.y})"
        
    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
        
    def __lt__(self, other):
        return (self.x*self.x + self.y*self.y) < (other.x*other.x + other.y*other.y)
    
p1 = Point(3, 4)
p2 = Point(1, 2)
print(p2 < p1)
print(p1 + p2)
```