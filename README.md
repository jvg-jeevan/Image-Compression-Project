<!-- <h1 align="center">Image Compression</h1>

<p align="center">
  A unified image compression system combining <b>entropy</b>, <b>transform</b>, and <b>vector quantization</b> techniques  
  <br>Supports Huffman, Arithmetic, Rice, DCT, and VQ compression — fully automatic, CPU-friendly implementation.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12+-yellow" />
  <img src="https://img.shields.io/badge/UI-Gradio-orange" />
  <img src="https://img.shields.io/badge/Compute-CPU Only-blue" />
  <img src="https://img.shields.io/badge/Compression-Lossless & Lossy-green" />
</p>

---

## **Introduction**

This project implements a **complete image compression suite** featuring five classical and modern techniques:

### 🔹 **Entropy Coders**
- Huffman Coding  
- Arithmetic Coding  
- Rice Coding (auto-k)

### 🔹 **Transform Coder**
- Block DCT + Quantization + Huffman

### 🔹 **Vector Quantization**
- LBG (k-means) Codebook + Huffman

A full **Gradio Web App** allows users to upload an image and automatically:

✔ Compress using all 5 methods  
✔ Reconstruct images  
✔ Compare BPP, Compression Ratio, and Efficiency  
✔ View all reconstructions side-by-side  
✔ See a unified comparison graph  
✔ No manual parameter selection required  

---

## **Theory of Methods**

### 1. Huffman Coding (Entropy)
- Prefix-free  
- Optimal integer-bit coder  
- Builds binary tree from symbol frequencies  

### 2. Arithmetic Coding
- Encodes entire sequence into an interval  
- Bit-efficient, near entropy  
- Uses integer renormalization  

### 3. Rice Coding
- Unary quotient + binary remainder  
- Best for smooth images and residuals  
- Auto-selects **k = 0–8**

### 4. DCT Compression
- Block-wise DCT  
- Quantization  
- Huffman coding on coefficients  
- Lossy (JPEG-style)

### 5. Vector Quantization (VQ)
- Codebook via k-means (LBG)  
- Blocks replaced with nearest centroid index  
- Indices Huffman coded  
- Lossy  

---

## **Project Structure**

```

Image-Compression/
│
src/
│
├── __pycache__/            # Python bytecode cache
├── .gradio/                # Gradio session & cache files
│
├── arithmetic.py           # Arithmetic coding (encode/decode)
├── dct.py                  # DCT blocks, quantization, Huffman wrapper
├── huffman.py              # Huffman tree, codes, encoding & decoding
├── rice.py                 # Rice (Golomb–Rice) encoding & decoding
├── vq.py                   # Vector Quantization (LBG/k-means, encoding & decoding)
│
└── main.py                 # Full pipeline + Gradio front-end UI
│
└── README.md

````

---

## **Installation**

```bash
python -m venv venv
venv\Scripts\activate   # Windows
pip install numpy opencv-python matplotlib gradio bitarray
````

---

## **Run the App**

```bash
cd src
python main.py
```

Open browser:

```
http://127.0.0.1:7860
```

---

## **Gradio Web Interface**

### Interface Screenshot

![UI](assets/output_screen.jpeg)


### Program Output Window

![Output](assets/images_output.jpeg)


---

### **Input Image**

![Input](assets/input_image.png)


---

### **Reconstructed Outputs**

Huffman reconstruction <br>
![Huffman](assets/Huffman.png)<br>
Arithmetic reconstruction <br>
![Arithmetic](assets/Arithmetic.png)<br>
Rice reconstruction <br>
![Rice](assets/Rice.png)<br>
DCT reconstruction <br>
![DCT](assets/DCT.png)<br>
VQ reconstruction <br>
![VQ](assets/VQ.png)

---

## **Results: Size Comparison**

Input image size: **54 KB**

| Method     | Preview Size (KB) | CR (Preview) |
| ---------- | ----------------- | ------------ |
| Huffman    | 7                 | 7.71×        |
| Arithmetic | 7                 | 7.71×        |
| Rice       | 7                 | 7.71×        |
| DCT        | 7                 | 7.71×        |
| VQ         | 6                 | 9.00×        |

> ⚠️ Note: These are WebP preview sizes displayed by Gradio, not raw-compressed bitstreams.

---

# **Pseudocode (Main Pipeline)**

```text
function COMPRESS_AND_SHOW_ALL(image):
    gray = preprocess(image)
    pixels = flatten(gray)
    compute entropy and original_bits

    run: Huffman, Arithmetic, Rice, DCT, VQ
    for each method:
        compute Bits, BPP, CR, Efficiency
        store reconstructed image

    plot = generate_comparison_graph()
    return summary, reconstructions, plot
```

---

## **Summary**

* Entropy methods are **lossless**
* DCT & VQ provide **lossy** comparison
* Arithmetic achieves best entropy compression
* VQ gave smallest preview size (6 KB)
* PNG still outperforms classical methods

---

## **Limitations**

* Grayscale-only
* WebP preview affects visual file sizes
* Arithmetic is CPU-heavy
* DCT/VQ parameters fixed

---

## **Future Work**

* Add predictive coding (JPEG-LS style)
* Add Golomb-Rice residual coding
* Support RGB (YCbCr transform)
* Add LZ77 backend
* Export actual bitstreams
* Compute PSNR/SSIM

---

## Author

**Jeevan V Gowda**<br>
M.Tech – Signal Processing and Machine Learning<br>
National Institute of Technology, Karnataka<br>
[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jvg-jeevan)  
---
## License

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

This project is licensed under the **MIT License**.
---
 -->






# Hybrid Multi-Stage Image Compression System
### Classical Entropy Coders • Transform Coding • Neural Generative Models

This project implements a unified framework for comparing eight image compression techniques, including classical lossless/lossy algorithms and modern neural network–based models. A Gradio-based interface allows users to upload an image, run all compression methods, view reconstructed outputs, and compare compression metrics.

---

## 1. Overview

The system supports the following compression methods:

### Classical Methods
- Huffman Coding  
- Arithmetic Coding  
- Rice (Golomb–Rice) Coding  
- Block-DCT Compression (JPEG-style)  
- Vector Quantization (LBG / K-Means)

### Neural Network–Based Methods
- CNN Lossless Predictor  
- Autoencoder Compression  
- VQ-VAE (Vector-Quantized Variational Autoencoder)

This combination enables a comprehensive comparison between traditional hand-crafted techniques and learned generative models.

---

## 2. Project Structure

```

IMAGE-COMPRESSION/
│
├── data/                              # Optional dataset
│
├── Report/
│   └── EC761 Project Report.pdf       # Detailed project documentation
│
├── arithmetic.py                      # Arithmetic encoder/decoder
├── dct.py                             # Block-DCT transform + quantization
├── huffman.py                         # Huffman tree and prefix coding
├── rice.py                            # Golomb–Rice coder
├── vq.py                              # Classical Vector Quantization
│
├── lossless_predictor.py              # CNN-based residual predictor
├── train_lossless_predictor.py        # Training script
│
├── ml_autoencoder.py                  # Autoencoder model definition
├── train_autoencoder.py               # Autoencoder training script
│
├── ml_vqvae.py                        # VQ-VAE model
├── train_vqvae.py                     # Training script for VQ-VAE
│
├── autoencoder.pth                    # Trained autoencoder weights
├── lossless_predictor.pth             # Trained CNN predictor weights
├── vqvae.pth                          # Trained VQ-VAE weights
│
└── main.py                            # Gradio UI and full compression pipeline

````

---

## 3. Installation

```bash
python -m venv venv
source venv/bin/activate       # Linux/Mac
venv\Scripts\activate          # Windows

pip install numpy opencv-python matplotlib gradio torch torchvision bitarray
````

---

## 4. Usage

To launch the application:

```bash
python main.py
```

Then open the interface at:

```
http://127.0.0.1:7860
```

---

## 5. System Architecture

The system performs:

1. Input preprocessing (grayscale or RGB channel splitting).
2. Independent compression using all eight algorithms.
3. Reconstruction and merging (for RGB channels).
4. Calculation of compression ratio, bits-per-pixel, and size reduction.
5. Display of reconstructed outputs in a comparison grid.

This architecture is designed to enable fair evaluation across all compression families.

---

## 6. Summary of Algorithms

### Huffman Coding

Constructs an optimal prefix code based on symbol frequencies.

### Arithmetic Coding

Encodes the entire pixel sequence into a fractional interval, approaching Shannon entropy limits.

### Rice Coding

Unary quotient + binary remainder representation, effective for small residuals.

### Block-DCT Compression

Applies an 8×8 block transform, quantizes coefficients, and reconstructs via inverse DCT.

### Vector Quantization

Clusters fixed-size blocks into a codebook using k-means; blocks are replaced by index values.

### CNN Lossless Prediction

Uses a convolutional neural network to predict pixel values and encodes the residuals.

### Autoencoder Compression

Learns latent representations through encoder–decoder architecture.

### VQ-VAE

Quantizes latent vectors using learned discrete codebooks, producing compact representations.

---

## 7. Results Overview

Based on evaluation experiments:

| Method              | Output Size (KB) | Compression Ratio | Percentage Saving |
| ------------------- | ---------------- | ----------------- | ----------------- |
| Huffman             | 12 KB            | 7.50×             | 86.7 %            |
| Arithmetic          | 12 KB            | 7.50×             | 86.7 %            |
| Rice                | 12 KB            | 7.50×             | 86.7 %            |
| DCT                 | 11 KB            | 8.18×             | 87.8 %            |
| Vector Quantization | 10 KB            | 9.00×             | 88.9 %            |
| CNN Lossless        | 12 KB            | 7.50×             | 86.7 %            |
| Autoencoder         | 10 KB            | 9.00×             | 88.9 %            |
| VQ-VAE              | 6 KB             | 15.00×            | 93.3 %            |

VQ-VAE demonstrated the strongest compression ratio, whereas classical entropy coding ensured lossless reconstruction.

---

## 8. Limitations

* Preview images in the UI do not reflect exact compressed bitstream sizes.
* Neural models require training time and suitable hardware.
* Classical entropy coders may perform poorly on high-entropy images.
* RGB processing lacks colour decorrelation (e.g., YCbCr).
* No automatic parameter optimization (e.g., quantization strength or codebook size).

---

## 9. Future Enhancements

* Integration of zig-zag reordering and run-length encoding for DCT.
* Improved predictive coding for Rice (JPEG-LS style).
* Full YCbCr pipeline for colour compression.
* Entropy-aware neural network training.
* Saving raw compressed bitstreams for accurate measurements.
* Extensions to video compression using temporal prediction.

---

## 10. License

This project is released under the MIT License.

---

## 11. Acknowledgment

This work was completed as part of the EC761 — Information Processing and Compression course at the National Institute of Technology Karnataka (NITK).

```

```



