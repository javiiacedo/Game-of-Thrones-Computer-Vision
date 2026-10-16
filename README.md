# Computer Vision & Image Processing Laboratory: *Game of Thrones* Edition

An interactive, practical laboratory exploring foundational and advanced digital image processing techniques using Python, OpenCV, and NumPy, themed around imagery and characters from *Game of Thrones*.

---

## Table of Contents

- [Overview](#overview)
- [Topics & Modules](#topics--modules)
  - [1. Radiometric Transformations](#1-radiometric-transformations)
  - [2. Geometric Transformations](#2-geometric-transformations)
  - [3. Linear & Spatial Filtering](#3-linear--spatial-filtering)
  - [4. Noise Modeling & Denoising](#4-noise-modeling--denoising)
  - [5. Edge Detection & Sharpness Analysis](#5-edge-detection--sharpness-analysis)
- [Interactive Controls (`ipywidgets`)](#interactive-controls-ipywidgets)
- [Repository Structure](#repository-structure)
- [Installation & Setup](#installation--setup)
  - [Local Environment](#local-environment)
  - [Google Colab](#google-colab)
- [Dependencies](#dependencies)
- [License](#license)

---

## Overview

This repository provides hands-on implementations of essential digital image processing algorithms. The workbook guides you through pixel manipulation, frequency and spatial domain filtering, matrix-based geometric mapping, and feature gradient extractions—all tested against thematic imagery from the *Game of Thrones* universe (e.g., House sigils, landscape maps of Westeros, portraits).

---

## Topics & Modules

### 1. Radiometric Transformations
Point-wise pixel intensity manipulations and dynamic range adjustments:
- **Linear transformations:** Brightness and contrast modulation.
- **Logarithmic & Power-Law (Gamma) transformations:**
  $$I_{\text{out}}(x, y) = c \cdot I_{\text{in}}(x, y)^\gamma$$
- **Histogram analysis:** Calculation, visualization, and contrast stretching.
- **Histogram Equalization & CLAHE:** Global equalization vs. Contrast Limited Adaptive Histogram Equalization for non-uniform lighting conditions.

### 2. Geometric Transformations
Affine transformations and coordinate mapping via matrix operations:
- **Affine matrix transformation:**
  $$\begin{bmatrix} x' \\ y' \\ 1 \end{bmatrix} = \begin{bmatrix} a & b & t_x \\ c & d & t_y \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x \\ y \\ 1 \end{bmatrix}$$
- **Elementary operations:** Translation, scaling, rotation about an arbitrary center, and shearing.
- **Interpolation methods:** Nearest neighbor, bilinear, and bicubic interpolation comparison.

### 3. Linear & Spatial Filtering
Kernel convolution in the spatial domain:
- **Convolution formulation:**
  $$(I * K)(x, y) = \sum_{i=-k}^{k} \sum_{j=-k}^{k} I(x - i, y - j) \cdot K(i, j)$$
- **Smoothing filters:** Box / uniform blur filters and separable Gaussian kernels:
  $$G(x, y) = \frac{1}{2\pi\sigma^2} \exp\left(-\frac{x^2 + y^2}{2\sigma^2}\right)$$
- **Kernel property analysis:** Kernel size vs. variance $\sigma$, normalization, and spatial boundary handling (`BORDER_REFLECT`, `BORDER_CONSTANT`, etc.).

### 4. Noise Modeling & Denoising
Synthesis and mitigation of stochastic image degradation:
- **Additive Gaussian Noise:** Characterized by mean $\mu$ and variance $\sigma^2$.
- **Impulse (Salt-and-Pepper) Noise:** Non-linear corruption affecting random pixel distributions.
- **Restoration techniques:**
  - Gaussian and averaging filters for Gaussian noise.
  - Non-linear **Median Filtering** for rank-order impulse noise elimination without excessive edge blurring.
  - **Bilateral Filtering** for edge-preserving denoising.

### 5. Edge Detection & Sharpness Analysis
First- and second-order derivative operators for structural boundary detection:
- **Sobel Operators:** Approximating directional gradients:
  $$G_x = \begin{bmatrix} -1 & 0 & 1 \\ -2 & 0 & 2 \\ -1 & 0 & 1 \end{bmatrix}, \quad G_y = \begin{bmatrix} -1 & -2 & -1 \\ 0 & 0 & 0 \\ 1 & 2 & 1 \end{bmatrix}$$
  $$\|\nabla I\| = \sqrt{G_x^2 + G_y^2}, \quad \theta = \operatorname{arctan2}(G_y, G_x)$$
- **Laplacian Operator:** Second-order differential operator for zero-crossing analysis:
  $$\nabla^2 I = \frac{\partial^2 I}{\partial x^2} + \frac{\partial^2 I}{\partial y^2}$$
- **Unsharp Masking:** High-boost filtering to emphasize high-frequency texture and edges:
  $$I_{\text{sharp}} = I + \alpha \cdot (I - I_{\text{blurred}})$$

---

## Interactive Controls (`ipywidgets`)

To facilitate qualitative and quantitative observation, the notebook embeds dynamic controls:
- **Interactive sliders:** Tune kernel size $k \in [3, 31]$ (constrained to odd values), Gaussian standard deviation $\sigma$, and threshold values.
- **Live side-by-side rendering:** Compare raw corrupted inputs, intermediate feature maps, and processed outputs in real time.

---

## Repository Structure

```text
├── data/
│   ├── raw/                 # Source Game of Thrones images & assets
│   └── outputs/             # Exported processed figures and plots
├── notebooks/
│   └── computer_vision_got.ipynb   # Main Jupyter/Colab notebook
├── requirements.txt         # Python package dependencies
├── .gitignore
└── README.md                # Project documentation
```

---

## Installation & Setup

### Local Environment

1. **Clone the repository:**
   ```bash
   git clone https://github.com/<your-username>/cv-got-practica.git
   cd cv-got-practica
   ```

2. **Create and activate a virtual environment (recommended):**
   ```bash
   python -m venv venv
   # On macOS/Linux:
   source venv/bin/activate
   # On Windows:
   venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Lab or Notebook:**
   ```bash
   jupyter lab
   ```

### Google Colab

To run directly on Google Colab without local configuration:
1. Upload `computer_vision_got.ipynb` to your Google Drive or open it directly via GitHub integration.
2. Enable interactive widget extensions (enabled by default in modern Colab instances):
   ```python
   # Colab cell setup
   !pip install -q opencv-python-headless matplotlib ipywidgets
   ```

---

## Dependencies

- **Python** $\ge$ 3.8
- **OpenCV (`opencv-python` / `opencv-python-headless`)** $\ge$ 4.7
- **NumPy** $\ge$ 1.22
- **Matplotlib** $\ge$ 3.5
- **ipywidgets** $\ge$ 8.0

---

## License

This project is released under the [MIT License](LICENSE). Educational imagery from *Game of Thrones* is used strictly for non-commercial, instructional research purposes.
