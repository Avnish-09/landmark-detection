# Landmark Recognition using MobileNetV2

A deep learning-based landmark recognition system that classifies architectural landmarks into six categories — Gothic, Modern, Mughal, Neoclassical, Pagodas, and Pyramids — using TensorFlow, Keras, and MobileNetV2 transfer learning.

## Overview

This project implements an image classification model for recognizing different architectural landmark categories from images.

The model uses a pretrained MobileNetV2 network with transfer learning and a custom classification head.

## Objective

The objective of this project is to develop a deep learning model capable of automatically recognizing the architectural category of a landmark image.

## Dataset

The dataset was obtained from Kaggle using the Kaggle API.

**Kaggle Dataset:**  
https://www.kaggle.com/datasets/kayvanshah/landmarks-dataset

The dataset contains **420 images** belonging to six classes:

- Gothic
- Modern
- Mughal
- Neoclassical
- Pagodas
- Pyramids

### Dataset Split

| Dataset | Images |
|---|---:|
| Training | 336 |
| Validation | 84 |
| Total | 420 |

An 80/20 validation split was used.

## Technologies Used

- Python
- TensorFlow
- Keras
- MobileNetV2
- NumPy
- Matplotlib
- Google Colab
- Kaggle API
- PIL

## Methodology

### 1. Dataset Download

The dataset was downloaded directly from Kaggle using the Kaggle API.

### 2. Image Preprocessing

- Images were resized to **160 × 160 pixels**.
- Images were normalized according to MobileNetV2 preprocessing requirements.
- Image files were checked and converted to RGB JPEG format.

### 3. Data Augmentation

The following augmentation techniques were applied:

- Random horizontal flipping
- Random rotation
- Random zoom

### 4. Transfer Learning

MobileNetV2 pretrained on ImageNet was used as the base model.

The MobileNetV2 base layers were frozen and used as a feature extractor.

The classification head consisted of:

- Global Average Pooling
- Dropout (0.3)
- Dense layer with 6 output classes
- Softmax activation

### 5. Model Training

The model was trained using:

| Parameter | Value |
|---|---|
| Architecture | MobileNetV2 |
| Input Size | 160 × 160 × 3 |
| Batch Size | 32 |
| Epochs | 12 |
| Optimizer | Adam |
| Learning Rate | 0.001 |
| Loss Function | Sparse Categorical Crossentropy |
| Output Classes | 6 |

## Model Architecture

```text
Input Image
   ↓
160 × 160 × 3
   ↓
Data Augmentation
   ├── Random Flip
   ├── Random Rotation
   └── Random Zoom
   ↓
MobileNetV2
(ImageNet Pretrained)
   ↓
Global Average Pooling
   ↓
Dropout (0.3)
   ↓
Dense Layer
   ↓
Softmax
   ↓
6 Landmark Classes
