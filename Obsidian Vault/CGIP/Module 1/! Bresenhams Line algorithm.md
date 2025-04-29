$\Delta x = x2 - x1$
$\Delta y = y2 - y1$

- Find Decision Parameter
  $Pk = 2\Delta y - \Delta x$ 

- **IF $Pk > 0$**
	  $P_{k+1} = P_k + 2\Delta y - 2\Delta x$
	  $x_{next} = x_1 + 1$
	  $y_{next} = y_1 + 1$

- **IF $Pk < 0$**
	  $P_{k+1} = P_k + 2\Delta y$
	  $x_{next} = x_1 + 1$
	  $y_{next} = y_1$

![[Pasted image 20250429184608.png]]
![[Pasted image 20250429184555.png]]
