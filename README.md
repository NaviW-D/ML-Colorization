
# Colorful Image Colorization Project

**Last Update:** January 2026 (December 2025)

---

## Project Overview

This repository contains an updated implementation of the **Image Colorization** project originally developed by **Richard Zhang, Phillip Isola, and Alexei A. Efros**.

It also includes automatic colorization functionality from the **SIGGRAPH 2017** paper titled:

> *“Real-Time User-Guided Image Colorization with Learned Deep Priors”*

This version has been optimized for easy inference using the **PyTorch** framework.

![Sample Image](http://richzhang.github.io/colorization/resources/images/teaser4.jpg)

---

## Installation

To get started, clone the repository and install the required dependencies:

```bash
# Clone the repository
git clone https://github.com/NaviW-D/ml-colorization-project.git

# Navigate into the project directory
cd ml-colorization-project

# Install required libraries
pip install -r requirements.txt
```

---

## Usage (Colorization)

To colorize a custom image, run the following script.
The final results will be saved in the `imgs_out` folder.

```bash
python demo_release.py -i imgs/ansel_adams3.jpg
```

---

## Loading the Model in Python

You can directly load the pretrained models into your Python code.

The process includes:

* Converting the image to **Lab color space**
* Resizing it to **256×256**
* Running inference
* Converting the output back to **RGB space** at original resolution

```python
import colorizers

# Load ECCV 2016 model
colorizer_eccv16 = colorizers.eccv16().eval()

# Load SIGGRAPH 2017 model
colorizer_siggraph17 = colorizers.siggraph17().eval()
```

---

## Technical Details

* **Architecture:** Deep Convolutional Neural Network (CNN)
* **Framework:** PyTorch (legacy Caffe version is no longer supported)
* **Processing Pipeline:**
  Images are processed in **Lab color space**, separating:

  * **L channel** → luminance (brightness)
  * **ab channels** → chrominance (color information)
