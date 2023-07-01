---
title: "Opencv GetStart"
date: 2023-07-01T09:31:32+08:00
---

# Opencv environment configuration

## Host information

raspberry zerow with office camera.

To enable the camera in the raspberry os, running the `raspi-conifg` command to turn on the camera.

## Install the package

```shell
sudo apt-get install build-essential cmake pkg-config libjpeg-dev libtiff5-dev libjasper-dev libpng-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libfontconfig1-dev libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev libgtk2.0-dev libgtk-3-dev libatlas-base-dev gfortran libhdf5-dev libhdf5-serial-dev libhdf5-103 python3-pyqt5 python3-dev -y

pip3 install opencv-python
```

It will takes a long time .