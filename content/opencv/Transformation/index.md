---
title: "Geometric Transformations of Images"
date: 2023-07-01T10:31:32+08:00
---

# Geometric Transformations of Images

## 1. Transformations

cv.warpAffine and cv.warpPerspective are two functions used to transform the pictures.

The warpAffine can be used to rotate , translate and scale, transformed parallel lines are still parallel.

### 1.1 scaling

using the `cv.resize` function to resize the image.

when using the `cv.resize` function to resize the image, there are two ways.

- using the `fx` and `fy` to scale the x and y
- using the shape parameter to set the x and y directly

```python
import numpy as np
import cv2 as cv
img = cv.imread('messi5.jpg')
assert img is not None, "file could not be read, check with os.path.exists()"
res = cv.resize(img,None,fx=2, fy=2, interpolation = cv.INTER_CUBIC)
#OR
height, width = img.shape[:2]
res = cv.resize(img,(2*width, 2*height), interpolation = cv.INTER_CUBIC)
```

### 1.2 rotation

using `cv.wrapAffine` to rotate the image.

```python
img = cv.imread('messi5.jpg', cv.IMREAD_GRAYSCALE)
assert img is not None, "file could not be read, check with os.path.exists()"
rows,cols = img.shape
# cols-1 and rows-1 are the coordinate limits.
M = cv.getRotationMatrix2D(((cols-1)/2.0,(rows-1)/2.0),90,1)
dst = cv.warpAffine(img,M,(cols,rows))
```


### 1.3 Perspective Transformation

```python
img = cv.imread('sudoku.png')
assert img is not None, "file could not be read, check with os.path.exists()"
rows,cols,ch = img.shape
pts1 = np.float32([[56,65],[368,52],[28,387],[389,390]])
pts2 = np.float32([[0,0],[300,0],[0,300],[300,300]])
M = cv.getPerspectiveTransform(pts1,pts2)
dst = cv.warpPerspective(img,M,(300,300))
plt.subplot(121),plt.imshow(img),plt.title('Input')
plt.subplot(122),plt.imshow(dst),plt.title('Output')
```