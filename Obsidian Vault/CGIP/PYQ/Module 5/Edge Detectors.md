## Sobel Operator
- calculates approximate gradient of the image intensity function
- identifies areas of rapid change

- uses two **convolution masks $3 * 3$ **
- **Gx (Detects Vertical Edges):** This mask calculates the difference in intensity across the central pixel in the horizontal direction.

```
[-1  0  +1]
[-2  0  +2]
[-1  0  +1]
```
- **Gy (Detects Horizontal Edges):** This mask calculates the difference in intensity across the central pixel in the vertical direction. (Note: Conventions can vary slightly, sometimes this mask is transposed or negated, but the principle is the same).

```
[-1 -2 -1]
[ 0  0  0]
[+1 +2 +1]
```