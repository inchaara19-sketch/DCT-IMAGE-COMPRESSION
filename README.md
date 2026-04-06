# Image Compression using DCT (JPEG-like Method)

## Overview

This project implements a **Discrete Cosine Transform (DCT)-based image compression algorithm**, inspired by the standard JPEG compression technique. The method compresses images by transforming them into the frequency domain, reducing less important components, and reconstructing the image with minimal perceptual loss.

The implementation is written in Python and evaluates compression performance across multiple image formats such as **JPG, PNG, and BMP**.



## Methodology

The compression pipeline follows these steps:

1. **Image Preprocessing**

   * Input image is loaded and converted to RGB format to ensure consistency.

2. **Block Division**

   * The image is divided into non-overlapping **8×8 blocks**.

3. **Discrete Cosine Transform (DCT)**

   * Each block is transformed from spatial domain to frequency domain using 2D DCT.

4. **Quantization**

   * DCT coefficients are quantized using a standard quantization matrix scaled by a quality factor.

5. **Compression**

   * Many high-frequency coefficients become zero, reducing storage requirements.

6. **Reconstruction**

   * Dequantization and inverse DCT (IDCT) are applied to recover the image.



## Performance Metrics

The following metrics are used to evaluate performance:

### Compression Ratio

Compression Ratio = Original Size / Compressed Size

### Peak Signal-to-Noise Ratio (PSNR)

PSNR = 10 × log10 (255² / MSE)

Where MSE is the mean squared error between original and reconstructed images.



## Results and Observations

* **Compressed size remains nearly constant** for the same image regardless of input format.
* **Compression ratio varies significantly**:

  * Highest for **BMP (uncompressed format)**
  * Moderate for **PNG**
  * Lowest for **JPEG (already compressed)**
* **PSNR values (~30–35 dB)** indicate good reconstruction quality.
* Increasing quality factor:

  * Improves PSNR (better image quality)
  * Reduces compression ratio (larger file size)



## Graphs Generated

The implementation produces:

* **PSNR vs Quality Factor**
* **Compression Ratio vs Quality Factor**

These graphs demonstrate the trade-off between compression efficiency and image quality.



## Requirements

Install required libraries:

pip install numpy scipy pillow matplotlib



## How to Run

1. Place an image in the project directory (e.g., `test.jpg`)
2. (Optional) Convert into multiple formats:

from PIL import Image
img = Image.open("test.jpg")
img.save("test.png")
img.save("test.bmp")

3. Run the script or Jupyter Notebook to:

   * Compress the image
   * Display results
   * Generate graphs

 Project Structure

project/
│
├── main.py / notebook.ipynb
├── test.jpg
├── test.png
├── test.bmp
└── README.md

 Conclusion

The DCT-based compression method effectively reduces image size while maintaining acceptable visual quality. The results confirm that compression is most efficient for uncompressed image formats and highlight the trade-off between compression ratio and reconstruction quality.


References

1.JPG, PNG and BMP image compression using discrete cosine transform
Rostam Affendi Hamzah, Muttaqin Md Roslan, Ahmad Fauzan bin Kadmin, Shamsul Fakhar bin Abd Gani, Khairul Azha A. Azi

2. NumPy Developers, "NumPy Documentation." [Online]. Available: https://numpy.org/

3. SciPy Developers, "SciPy FFT Documentation." [Online]. Available: https://scipy.org/

4. Python Software Foundation, "Pillow (PIL) Documentation." [Online]. Available: https://pillow.readthedocs.io/

5. Matplotlib Development Team, "Matplotlib Documentation." [Online]. Available: https://matplotlib.org/


Acknowledgement
This project was developed as part of coursework in **Digital Signal Processing / Image Processing**.
