# Matrix-Based Image Morphing using SVD

## Overview

This project explores how **linear algebra concepts** like **Singular Value Decomposition (SVD)** and **Low-Rank Approximation** can be applied to images.

Instead of treating images as visuals, we treat them as **matrices** and perform transformations mathematically.

The project demonstrates:

* Image reconstruction using low-rank approximation
* Differences between naive pixel blending and structure-based morphing
* How SVD affects image representation and transformation

---

## Core Concepts

### 1. Singular Value Decomposition (SVD)

Any matrix ( A ) can be decomposed as:

[
A = U \Sigma V^T
]

* ( U ): basis directions (row space)
* ( \Sigma ): importance (singular values)
* ( V^T ): basis directions (column space)

Geometric interpretation:

> **rotate → scale → rotate**

---

### 2. Low-Rank Approximation

Instead of using all components, we keep only top **k** singular values:

[
A_k = \sum_{i=1}^{k} \sigma_i u_i v_i^T
]

* Small ( k ) → only major patterns
* Large ( k ) → more details

This demonstrates **image compression and reconstruction**.

---

### 3. Morphing Approaches

#### Naive Blending

[
(1 - t)A + tB
]

* Pixel-wise interpolation
* Smooth transition
* Preserves spatial alignment

---

#### SVD-Based Morphing

* Decompose both images using SVD
* Interpolate ( U, \Sigma, V )
* Reconstruct intermediate frames

> This blends **structure**, not just pixels.

---

## Project Structure

### 1. Low-Rank Approximation

**File:** `low_rank_approximation.ipynb`

* Demonstrates reconstruction using different values of ( k )
* Shows how image quality improves as ( k ) increases
* Highlights compression vs detail trade-off

---

### 2. Color Morphing (BGR)

**File:** `svd_BGR.ipynb`

* Applies SVD morphing on each color channel (B, G, R)
* Includes:

  * Sign alignment
  * Frame interpolation
  * Real-time animation
* Displays comparison:

  * Naive blending vs SVD morphing

---

### 3. Grayscale Morphing

**File:** `svd_graysacle.ipynb`

* Simpler and cleaner implementation
* Removes color artifacts
* Focuses purely on structural transformation

---

## Key Observations

* **Naive blending** looks smoother because it operates directly on pixels
* **SVD morphing** may introduce distortions (ghosting, banding)
* This happens because:

  * SVD works on **global patterns**, not local pixels
  * Differences in structure lead to reconstruction artifacts

> **Naive blending preserves appearance, SVD reveals structure**

---

## Features

* Interactive control of **k (rank)**
* Side-by-side comparison (Naive vs SVD)
* Demonstrates both success and failure cases

---

## Requirements

```bash
pip install numpy opencv-python matplotlib
```
## Learning Outcomes

This project helped understand:

* How images can be represented as matrices
* How SVD decomposes structure
* How low-rank approximation enables compression
* Why different mathematical representations produce different visual results

---

## Final Insight

> This project is not about making better animations,
> but about understanding how **mathematical representations affect image transformation**.
