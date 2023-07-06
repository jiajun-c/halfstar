---
title: "Simple image process"
date: 2023-07-01T10:31:32+08:00
---
# start process the picture

## Read in the picture

using the cv2.imread you can get the img type result.
```python
import cv2
import numpy as np

img = cv2.imread('test.png')
print(img)
assert img is not None, "file could not be read, check with os.path.exists()"
```

The default image type is the rgb


## Image add

$dst = \beta \cdot img1 + \alpha\cdot img2$

将不同的图片按照不同的比例进行叠加，得到最终的图片

```python
import cv2 as cv
import numpy as np

img1 = cv.imread('test.png')
img2 = cv.imread('test1.png')
assert img1 is not None, "file could not be read, check with os.path.exists()"
assert img2 is not None, "file could not be read, check with os.path.exists()"
dst = cv.addWeighted(img1, 0.7, img2, 0.3, 0)
cv.imshow('dst', dst)
cv.waitKey(0)
cv.destroyAllWindows()
```

