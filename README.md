# 🩺 Fine-Grained Skin Disease Classification with Multi-Scale Attention Mechanisms

This project presents an end-to-end solution for skin lesion classification using convolutional and attention-based deep learning models. It leverages both raw and segmented images to perform binary and multi-class classification of skin diseases, utilizing datasets like **ISIC 2018** and **HAM10000**. Attention-enhanced models like **Inception ResNet V2 with Soft Attention** showed high accuracy and clinical potential, while segmentation methods were explored for focused lesion analysis.

---

## 🎯 Objectives

- Detect and classify skin lesions from dermatoscopic images
- Compare performance between raw and segmented images
- Evaluate multiple deep learning architectures with attention mechanisms
- Train segmentation models to isolate skin lesion regions automatically

---

## 🧪 Dataset

- **HAM10000**: 10,015 high-resolution images labeled across 7 skin disease classes:
  - Melanoma, Melanocytic nevi, Basal cell carcinoma, Actinic keratosis, Benign keratosis, Dermatofibroma, Vascular lesions
- Includes metadata: lesion ID, patient age, gender, localization
- Dataset split: 70% training, 20% validation, 10% test

Segmentation tasks used subsets of ISIC 2018 with:
- 2,500 images for lesion boundary segmentation
- 2,594 images for lesion attribute detection with 5 mask labels per image

---

## 🧠 Methodology

### 🧪 Preliminary Tasks

1. **Lesion Boundary Segmentation**
   - Models: U-Net, ResNet50-based U-Net
   - Metric focus: Dice Coefficient, Jaccard Index, Sensitivity

2. **Lesion Attribute Detection**
   - Model: DeepLabV3
   - Features detected: Pigment network, Streaks, Cysts, Globules, etc.

### 🔍 Classification Tasks

- **Multi-Class (7 diseases)**
  - Basic CNN: Accuracy 52.5%
  - ResNet50 + Transformer: 79.4%
  - Inception ResNet V2 + Soft Attention: **82.5%**
  - ResNet50 + Advanced Soft Attention: 80.8%

- **Binary (Benign vs. Malignant)**
  - Inception ResNet V2 + Soft Attention: **Accuracy 89.6%**, Recall 84.62%

### 🎯 Auto-Segmentation Pipelines

- **Grounding DINO + SAM**: Used bounding box prompts + fine-tuned Segment Anything Model for lesion extraction
- **ResNet50-based U-Net**: Used pre-trained encoder for binary masks

---

## 📈 Results

| Model                              | Dataset Type      | Accuracy | F1-Score | Recall  |
|-----------------------------------|-------------------|----------|----------|---------|
| Inception ResNet V2 + Soft Attn   | Raw               | 82.5%    | 83.3%    | 82.5%   |
| Inception ResNet V2 + Soft Attn   | Segmented (SAM)   | 78.82%   | 79.78%   | 78.82%  |
| ResNet50 + Transformer            | Raw               | 79.4%    | 78.9%    | 79.4%   |
| Basic CNN                         | Raw               | 52.5%    | 60.3%    | 61.9%   |

Binary classification on raw data yielded the best results, particularly with **soft attention mechanisms**, which improved model focus on lesion-relevant features.

---

## 📌 Technologies Used

- Python, TensorFlow, Keras
- Deep Learning Architectures: CNN, ResNet50, Inception ResNet V2, Transformers
- Attention Mechanisms: Soft Attention, Multi-head Attention
- Segmentation Tools: Grounding DINO, Segment Anything Model (SAM), U-Net
- Data Visualization: Matplotlib, Seaborn

---

## 📄 Reports

- [📓 Final Project Report (PDF)](reports/DLS%20Final%20Project%20Report.pdf)

---

## 📃 License

This project is licensed under the [MIT License](LICENSE).
