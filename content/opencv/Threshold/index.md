---
title: "Image Thresholding process"
date: 2023-07-01T20:31:32+08:00
---

# Image Thresholding

## Simple Thresholding

For the simple thresholding process, when the pixels smaller than the threshold, it will be set to the 0, otherwise it will be set to 1.

There are several types of simple thresholds

There are several parameters.

- src: The image source
- threshold: The threshold
- maxThreshold: The maximum threshold
- Type: the type of threshold
```python
ret,thresh1 = cv.threshold(img,127,255,cv.THRESH_BINARY)
```


