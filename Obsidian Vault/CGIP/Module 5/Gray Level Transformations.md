![[Pasted image 20250501200250.png]]
## Linear
- **Identity** : each value of input image directly mapped to output image
	  $s = r$
- **Negative Transformation** : each value of input image subtracted from $L-1$ and mapped onto output image
	  $s = (L-1) - r$ 
	  L is number of intensity levels

## Logarithmic Transformation
- **log** : $s = c.log(r + 1)$ 
  dark pixel values are expanded compared to higher pixel values
- **inverse log**

## Power Law
- $\gamma$ is a varying quantity 
- $s = c.r^\gamma$ 
- - **Case 1: γ = 1**
    
    - The transformation becomes s = c * r. If c = 1, then s = r.
        
    - **Effect:** This is the **identity transformation**. It produces no change in the image intensity levels. The transition between intensities remains linear.
        
- **Case 2: γ < 1 (Fractional Gamma)**
    
    - The transformation curve bends upwards (concave up).
        
    - **Effect:** This mapping **expands the range of dark intensity values** and **compresses the range of bright intensity values**. Darker pixels are spread out over a wider range of output values, while brighter pixels are pushed closer together.
        
    - **Visual Effect:** The image appears **brighter**. Transitions in the dark regions become more pronounced (details in shadows are enhanced), while transitions in the bright regions become less pronounced (highlights may appear slightly compressed).
        
- **Case 3: γ > 1**
    
    - The transformation curve bends downwards (concave down).
        
    - **Effect:** This mapping **compresses the range of dark intensity values** and **expands the range of bright intensity values**. Darker pixels are pushed closer together, while brighter pixels are spread out over a wider range of output values.
        
    - **Visual Effect:** The image appears **darker**. Transitions in the bright regions become more pronounced (details in highlights are enhanced), while transitions in the dark regions become less pronounced (shadows may appear crushed).

- **nth power transformation** : 

![[Pasted image 20250501200823.png]]
