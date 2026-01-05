🌱 Plant Disease Image Classification using EfficientNet
📌 Project Overview

This project implements an industry-style deep learning pipeline for plant disease classification using leaf images.
The focus is on handling class imbalance, memory-efficient data augmentation, and robust CNN training on limited hardware.

The model is trained using EfficientNet with a two-stage training strategy and evaluated on unseen real-world images, achieving strong generalization performance.

🎯 Objectives

Build a production-oriented image classification pipeline

Handle severe class imbalance effectively

Perform disk-based data augmentation (RAM-efficient)

Train and fine-tune a transfer learning CNN

Evaluate real-world performance, not just validation accuracy

🗂️ Dataset Description

Image dataset of plant leaf diseases

Multiple disease classes with high imbalance

Dataset split into:

Training set

Validation set

Unlabeled test images (real-world scenario)

⚠️ Problem: Class Imbalance

Some disease classes had very few samples, which can:

Bias the model toward majority classes

Reduce recall for rare diseases (critical in agriculture)

✔️ Solution Implemented

Identified low, medium, and high frequency classes

Applied class-wise augmentation strategy

Augmented only minority classes

Avoided over-augmentation to prevent distribution shift

🔄 Data Augmentation Strategy (Disk-Based)

Why disk-based augmentation?

System constraint: 8GB RAM, Intel i3

On-the-fly augmentation caused memory pressure

Approach:

Generate augmented images once

Save them directly to disk

Merge with original dataset

Keep original images untouched

Augmentation intensity:
Class Type	Augmentation
Low count	Heavy
Medium count	Moderate
High count	None

✔️ Ensures balance
✔️ Stable training
✔️ RAM-efficient

Notebook: Data_Aug.ipynb

🧠 Model Architecture

Backbone: EfficientNet (Transfer Learning)

Input size: As required by EfficientNet variant

Loss: Categorical Crossentropy

Optimizer: Adam

Metrics: Accuracy, per-class performance

🏗️ Training Strategy (Two-Stage)
Stage 1: Feature Extraction

Backbone frozen

Train classifier head

Faster convergence

Stage 2: Fine-Tuning

Unfreeze top layers of backbone

Low learning rate

Improve class-specific features

Notebook: code.ipynb

📊 Evaluation

Validation accuracy during training

Manual evaluation on 100 unseen real-world test images

Achieved ~89% real-world accuracy

✔️ Strong generalization
✔️ Good minority class recognition

🧪 Key Learnings

Disk-based augmentation is highly effective on low-end systems

Over-augmentation can hurt real-world performance

Class-wise strategies outperform uniform augmentation

Validation accuracy alone is not enough — real-world testing matters

🛠️ Tech Stack

Python

TensorFlow / Keras

NumPy

OpenCV / PIL

Matplotlib

🚀 Future Improvements

Convert model to TensorFlow Lite for mobile deployment

Add Grad-CAM for explainability

Deploy as mobile app / web app

Collect more real-world samples for rare diseases

📁 Project Structure
├── Data_Aug.ipynb        # Disk-based class-wise augmentation
├── code.ipynb            # Model training & evaluation
├── dataset/
│   ├── train/
│   ├── val/
│   └── test/
├── saved_model/
└── README.md

👨‍💻 Author

Ramakrishna Reddy | Challa Anjanikumar Reddy | Sai Vardhan
Aspiring Machine Learning Engineer | Healthcare & Computer Vision AI