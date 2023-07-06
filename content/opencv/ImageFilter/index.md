# Image Filtering

## 2D Convolution

图像通常会被不同类型的滤波函数所处理，通常而言有两种

- low pass filter: used to filter the image noise
- high pass filter: used to find edges in the image

```python
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt

img = cv.imread('test.png')
assert img is not None, "file could not be read, check with os.path.exists()"
kernel = np.ones((5, 5), np.float32) / 25
dst = cv.filter2D(img, -10, kernel)
plt.subplot(121), plt.imshow(img), plt.title('Original')
plt.xticks([]), plt.yticks([])
plt.subplot(122), plt.imshow(dst), plt.title('Averaging')
plt.xticks([]), plt.yticks([])
plt.show()
```

## Image Bluring

