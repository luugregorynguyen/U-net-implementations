# Breast Cancer Ultrasound Image Segmentation using U-Net

This repository contains a Deep Learning solution for the segmentation of breast ultrasound images using the **U-Net** architecture. The model is designed to assist in the identification and localization of breast masses (benign and malignant).

## 📋 Project Overview

Breast cancer is one of the most common cancers among women worldwide. Early and accurate segmentation of ultrasound images is a critical step in CAD (Computer-Aided Diagnosis) systems. This project implements a full U-Net pipeline, from data preprocessing to performance evaluation.

## Dataset

The project uses the **Breast Ultrasound Images (BUSI) dataset**, which consists of 780 images among women between 25 and 75 years old. The dataset includes:
- **Benign cases**
- **Malignant cases**
- **Normal cases** (not used in this segmentation training)

**Data Source:** [Kaggle Breast ultrasound image](https://www.kaggle.com/datasets/aryashah2k/breast-ultrasound-images-dataset)

## Model Architecture

The model follows the standard **U-Net** architecture, consisting of a contracting path (encoder) and an expansive path (decoder).

### Key Features:
- **Input Size:** 128x128x1 (Grayscale).
- **Initialization:** `he_normal` kernel initializer for improved convergence in ReLU-based layers.
- **Optimization:** Mixed Precision training (`mixed_float16`) for accelerated performance on NVIDIA T4 GPUs.
- **Activation:** ReLU for hidden layers and Sigmoid for the output segmentation mask.

## Results

After training for 100 epochs, the model achieved the following performance on the test set:

- **Jaccard Score (IoU):** 0.6673
- **Mean IoU (mIoU):** 0.8154
- **Training Accuracy:** ~99.5% (Train) / ~94.7% (Val)

## How to use

1.  **Environment:** The code is optimized for Google Colab with GPU acceleration enabled.
2.  **Dataset:** The notebook automatically downloads the dataset via `kagglehub`.
3.  **Training:** Run the cells sequentially to build, compile, and train the model.
4.  **Visualization:** The final section provides a side-by-side comparison of the original ultrasound, the ground truth mask, and the model's prediction.

## Requirements

- TensorFlow 2.x
- OpenCV
- NumPy
- Matplotlib
- Scikit-learn
- Kagglehub

## References
1. [U_net clearly explained | Image segmentation](https://www.youtube.com/watch?v=oxcgx75k6yU)
2. [Dataset of breast ultrasound images (research paper)](https://doi.org/10.1016/j.dib.2019.104863)
3. [Letter to the Editor. Re: “Dataset of breast ultrasound images"](https://doi.org/10.1016/j.dib.2023.109247)
