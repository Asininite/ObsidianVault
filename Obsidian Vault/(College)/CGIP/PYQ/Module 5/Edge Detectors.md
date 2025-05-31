In the context of digital image processing and computer vision, **edges** are defined as:

**Significant local changes or discontinuities in image intensity (brightness).**

More specifically, edges correspond to points or sets of points in an image where:

1.  **Intensity Changes Sharply:** There is a relatively large difference in the brightness values of adjacent pixels or pixels across a small neighborhood.
2.  **Discontinuities Occur:** They mark the locations where the image intensity function changes abruptly.

**What Edges Typically Represent:**

*   **Object Boundaries:** The most common interpretation – edges often mark the outline separating an object from its background or from other objects in the scene.
*   **Surface Detail:** Changes in surface texture or material within an object.
*   **Surface Orientation Changes:** Abrupt changes in how a surface is angled relative to the light source or viewer.
*   **Illumination Changes:** Boundaries of shadows or highlights.

**Key Characteristics:**

*   **Local Phenomenon:** Edges are defined by changes within a small neighborhood of pixels.
*   **Gradient-Related:** Mathematically, edges correspond to locations with a high **gradient magnitude** (steep slope in the intensity function).
*   **Information Rich:** Edges carry a significant amount of structural information about the image content, often allowing for object recognition and scene understanding even when other information (like color or texture) is removed.

Therefore, edge detection algorithms aim to identify these locations of significant intensity change to produce an edge map, which highlights the structural outlines and details within an image.

![[Pasted image 20250502013345.png]]
**What is Edge Detection?**

Edge detection is a fundamental technique in digital image processing and computer vision used to **identify points in an image where the image brightness changes sharply or has discontinuities**. These points typically correspond to:

1. **Boundaries between objects:** Separating an object from its background or from other objects.
    
2. **Boundaries between different materials or parts of an object.**
    
3. **Changes in surface orientation or illumination.**
    

Essentially, edges represent significant variations in pixel intensity values packed into a small area. The goal of edge detection is to produce an "edge map" – typically a binary image where edge pixels are marked (e.g., as white) and non-edge pixels are unmarked (e.g., as black) – or an image where the brightness of a pixel corresponds to the strength of the edge at that location.

Edge detection is crucial because edges carry a lot of semantic information about the image content and are often used as a preliminary step for higher-level tasks like:

- Image segmentation (dividing an image into meaningful regions)
    
- Feature extraction (identifying key points or shapes)
    
- Object recognition and tracking
    
- Image registration and matching
    

Most edge detection techniques work by calculating an approximation of the **gradient** (the rate of change of intensity) of the image. High gradient values indicate rapid changes in intensity, signifying potential edges.

---

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

- input image is convoluted separately with $Gx$ and $Gy$ 
	  magnitude of gradient G at each pixel is calculated

## Prewitt Operator
- similar to Sobel
- uses two convolution masks $3 * 3$ 

**Gx (Detects Vertical Edges):**

```
[-1  0  +1]
[-1  0  +1]
[-1  0  +1]
```

**Gy (Detects Horizontal Edges):**

```
[-1 -1 -1]
[ 0  0  0]
[+1 +1 +1]
```

1. Convolve the image with Gx and Gy masks separately.
    
2. Calculate gradient magnitude: G = sqrt(Gx² + Gy²) or G ≈ |Gx| + |Gy|.
    
3. Calculate gradient direction: Θ = atan2(Gy, Gx).