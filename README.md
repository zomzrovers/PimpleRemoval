# Hybrid Approach to Automated Facial Pimple Removal

##  Abstract

Facial pimples not only affect visual aesthetics but also challenge facial recognition systems. This project presents a hybrid pipeline that combines classical image processing with deep learning inpainting for automated facial pimple removal. Our method first detects pimples using adaptive LAB color thresholding and Gaussian-based local intensity difference, then removes them using OpenCV’s Telea algorithm and Deep Image Prior (DIP) based U-Net architecture.

---

##  Features

- **Facial Region Segmentation** using 68 dlib landmarks and 3 custom forehead points.
- **Dual Pimple Detection Methods**:
  - LAB color space adaptive thresholding.
  - Local intensity difference using Gaussian filtering.
- **Dual Inpainting Approaches**:
  - OpenCV Telea algorithm for fast inpainting.
  - Deep Image Prior (DIP) based U-Net for realistic texture generation.
- **Dynamic Selection** of the best detection method per image based on recall.
- **Quantitative & Qualitative Evaluation** with visual results and metrics.

---

##  Methodology

### 1. Facial Region Analysis
- Detect face using dlib HOG detector.
- Predict 68 facial landmarks + 3 additional forehead points.
- Compute convex hull to isolate the facial region.

### 2. Pimple Detection
- **LAB Color Thresholding**: Convert to LAB and threshold A channel.
- **Blur Difference**: Gaussian blur the A channel and compute difference.
- Morphological operations to clean masks.

### 3. Pimple Inpainting
- **OpenCV Telea**: Fast, diffusion-based filling.
- **DIP U-Net**: Self-supervised learning from noise input for realistic inpainting.

---

##  Experimental Results

| Method                     | Mean Recall | Comments                                |
|---------------------------|-------------|-----------------------------------------|
| Blurred 'A' Channel Diff  | 0.498       | Better for diverse intensity pimples    |
| LAB Color Thresholding    | 0.442       | Struggles with low contrast pimples     |

| Inpainting Method         | Visual Quality | Processing Time |
|---------------------------|----------------|-----------------|
| OpenCV Telea              | Good           | Fast            |
| Deep Image Prior (DIP)    | Excellent      | Slower          |

---

##  Novelty

- Combined classical + unsupervised deep learning.
- No external dataset required for DIP.
- Dynamic algorithm selection based on per-image performance.
- Extended facial region coverage via additional forehead points.

---

##  Resources

- 🔗 **Colab Notebook**: [Pimple Remover Model](https://colab.research.google.com/drive/12OPdjwGulsCcBHLo3dCcinmn9tyLUxN2?usp=sharing)  
- 🗃️ **Dataset**: [Google Drive Dataset Link](https://drive.google.com/drive/folders/1I0i2bxpgjzVXhpGR6oiD8Jy4OciE80j-?usp=sharing)

---

## Conclusion

Our pipeline achieves robust, adaptive, and realistic pimple removal by combining precise facial masking, adaptive detection methods, and dual inpainting strategies. The Deep Image Prior method excels in realism, while OpenCV provides fast alternatives—together enabling practical, dataset-free facial enhancement.

---

## References

Key references used in this project include:
- [Deep Image Prior – CVPR 2018](https://arxiv.org/abs/1711.10925)
- OpenCV, Dlib, FAN, and landmark detection literature  
(*Full reference list available in the PDF report*)

---

## License

This project is for academic purposes only. Please contact the authors for any non-academic use.

