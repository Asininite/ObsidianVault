### linear
- Output pixel is a **linear combination (weighted sum)** of the input pixels in its neighborhood. The weights are defined by the filter kernel.
- Convolution / Correlation
- eg : average filter (low pass filter), prewitt sobel

### non-linear
- Output pixel calculation involves **nonlinear operations** on the input pixels in the neighborhood (e.g., finding median, min, max, ranking, applying complex logic).
- Order Statistics, Morphology, Conditional Rules, etc.
- eg : median filter, max filter