```python
import matplotlib.pyplot as plt
import numpy as np
import math

x = np.linspace(0, 2*math.pi, 100)
y_sin = np.sin(x)
y_cos = np.cos(x)

plt.plot(x, y_sin, label="sin x", linestyle='-')
plt.plot(x, y_cos, label="y wave", linestyle='--')

plt.xlabel("angle")
plt.ylabel("function val")
plt.title("since and cos")

plt.xticks=([0, math.pi/2, math.pi, math.pi*3/4, math.pi*2])
plt.yticks=([-1,0,1])

plt.legend()
plt.show()
```