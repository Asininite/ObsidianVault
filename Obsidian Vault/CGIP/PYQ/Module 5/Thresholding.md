![[Pasted image 20250501220942.png]]
![[Pasted image 20250502013650.png]]

### GLOBAL THRESHOLDING
1. Select an initial estimate of the threshold T.
2. Segment the image using T to form two groups G1 and G2: G1 consists of all pixels with intensity values > T, and G2 consists of all pixels with intensity values ≤ T. 
3. Compute the average intensity values m1 and m2 for groups G1 and G2.σ
4. Compute the new value of the threshold T as T = (m1 + m2)/2
5. Repeat steps 2 through 4 until the difference in the subsequent value of T is smaller than a pre-defined value δ.
6. Segment the image as g(x,y) = 1 if f(x,y) > T and g(x,y) = 0 if f(x,y) ≤ T.