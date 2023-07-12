---
title: " Opencv colorspace change"
date: 2023-07-01T09:31:32+08:00
---


## 1. basic color model

RGB: using the (red, green, blue) to describe the color, uses 8 bits each.

HSV: using the Hue, Saturation, and values to describe the color.

## 2. Color-Space

There are many colorspaces, using the code blow to get these flags.
```python
import cv2 as cv

flags = [i for i in dir(cv) if i.startswith('COLOR_')]

print(flags)
```

## 3. Object Tracking

We can change the rgb image to hsv image an extract a colored object from.