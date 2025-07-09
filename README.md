# NUS-FYP-CNN-on-tempered-glass-crack-patterns
This repository contains findings of my NUS final year project titled 'Evaluate feasibility of using Convolutional Neural Networks to determine  cause of damage of tempered glass'

# Predicting Impact Parameters from Tempered Glass Crack Patterns

This project explores the feasibility of using of Convolutional Neural Networks (CNNs) to infer the **velocity** and **angle** at which a projectile strikes tempered glass, purely from images of the resulting crack patterns.

It was developed as my **Final Year Project (FYP)** at the National University of Singapore (NUS). First, I designed a controlled experiment setup, conducted controlled drop tests of a metal ball onto tempered glass panels to build the dataset of fracture patterns. Next, I conduct data preprocessing, followed by training, testing and validation of CNN models and evaluate CNN preliminary feasibility to predict tempered glass impact parameters.

This project is a preliminary exploration and serves as a starting reference for future studies on the analysis of glass crack patterns using CNN modeling, or other ml modeling

---

## Repository contents

This GitHub repository contains:

1)📝 `README.md`: This page — summarising key insights, results, and tools used.
1) `glassCNN_shared.ipynb`: The full Google Colab code used in this project, including data loading, training, evaluation, and experiments.
> ⚠️ *Note:* This code is provided for **reference purposes** only. File paths are hardcoded for Google Colab, and no dataset is included.
1) [`Cleon_FYP_report_final.pdf`](./Cleon_FYP_report_final.pdf): My full thesis paper detailing the background, methodology, results, and conclusions.

---

## Tools & Techniques Used

To accomplish the task of predicting **impact velocity** and **angle**, I implemented and trained a **CNN-based regression model** using the following tools and components:

| Component | Details |
|----------|---------|
| **Architecture** | ResNeXt-101-32x8d (from PyTorch's `torchvision.models`) |
| **Output** | 2 regression targets: `[velocity_normalised, angle_normalised]` |
| **Loss Function** | Mean Squared Error (MSE) |
| **Training Method** | 3-fold Cross Validation |
| **Augmentation** | Optional horizontal flipping to generalize angle range |
| **Frameworks** | PyTorch, TorchVision, NumPy, Pandas, Scikit-learn, Matplotlib |

These components were combined into a pipeline that learns patterns in crack morphology to approximate the conditions under which the glass was fractured.

The hyperparameters used for most of the CNN models are shown below:
<details>
<summary>🔧 Training Settings</summary>

- Optimiser: Adam  
- Learning rate: 1e-5  
- Loss: MSE  
- Epochs: 60–120  
- Batch size: 16  
- Cross-validation: 3-fold  
- Augmentations: Horizontal flip (optional)

</details>

---

📊 Dataset Overview

| Property | Details |
|----------|---------|
| **Images** | 57 RGB images (336×448 px), manually captured under controlled conditions |
| **Labels** | Each image is labeled with two ground truth values: impact **velocity** and **angle** |
| **Label range** | Velocity ≈ 4.5 – 5.8 m/s, Angle ∈ {0°, 7.5°, 17.5°, 27.5°} |
| **Data format** | Images stored in folders, labels in CSV manifest |
| **Preprocessing** | Normalization to [-1, 1], optional cropping and flipping |

✅ *(Optional: add a few example image thumbnails here)*

---

## 📈 Results Summary

| Metric | MAE (normalised) | Note |
|--------|------------------|------|
| **Velocity** | 0.16 – 0.22 | Best results in full-frame config |
| **Angle** | 0.24 – 0.27 | Higher variation in cropped version |
| **Combined MAE** | **0.22** | Best overall model (augmented)

These results demonstrate that the CNN could **learn velocity-related features** reasonably well, but **angle prediction remained challenging** — likely due to limited training variation and subtle visual cues in the crack patterns.

✅ *(Optional: add MAE bar chart or predicted-vs-actual scatter plot here)*

---

## 📌 Key Contributions

- 📷 Designed and built the experimental drop setup to generate labeled fracture data
- 🗃️ Created a custom dataset of cracked tempered glass panels
- 🧠 Built and trained a CNN model to predict physical parameters
- 🧪 Conducted extensive tuning and validation (60–120 epochs, 10 configs)
- 📘 Authored full thesis documenting methodology, findings, and limitations

---

## 📄 Citation

