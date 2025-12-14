# 🍽️ Explainable Food Recognition (Food-101)

This project builds a **food image classification model** using deep learning and explains its predictions with **Grad-CAM**.

The focus is **not only accuracy**, but also **understanding why the model makes correct or incorrect predictions**.

---

## 📌 Project Overview

- Dataset: **Food-101**
- Model: **ResNet34 (ImageNet pretrained)**
- Method: **Transfer Learning + Grad-CAM**
- Goal:  
  - Classify food images  
  - Visualize where the model is looking  
  - Analyze why misclassifications happen  

---

## 📂 Dataset

**Food-101**
- 101 food categories  
- 1,000 images per class  
- Balanced dataset  
- Many visually similar dishes (e.g., seafood, desserts, breakfast foods)

---

## 🧠 Model Architecture

- Backbone: **ResNet34 pretrained on ImageNet**
- Final fully connected layer replaced with **101 output classes**

---

## 🔁 Training Strategy

The model is trained in **two stages**:

### Stage 1 – Train Classifier Head
- Freeze the ResNet34 backbone
- Train only the final fully connected (FC) layer
- Purpose: adapt ImageNet features to Food-101

### Stage 2 – Fine-tuning
- Unfreeze the last ResNet block (`layer4`)
- Fine-tune `layer4 + FC` with a smaller learning rate
- Purpose: improve food-specific feature representation

---

## 📊 Evaluation

The model is evaluated using:
- **Accuracy**
- **Macro F1-score**

Stage 2 shows clear improvement over Stage 1 and more balanced performance across classes.

---

## 🔍 Explainability with Grad-CAM

Grad-CAM is used to:
- Visualize **class-specific attention**
- Show which image regions influence predictions
- Explain both **correct predictions** and **errors**

Grad-CAM is applied to the **last convolutional layer** of ResNet34.

---

## ❌ Misclassification Analysis

For misclassified samples, Grad-CAM reveals that:
- The model focuses on **visually dominant or shared ingredients**
- Visually similar dishes cause confusion
- Errors are **systematic**, not random

Examples:
- Seafood dishes confused due to similar textures
- Breakfast dishes confused due to similar crispy bases

---

## ⚠️ Limitations

- Single-label classification
- No ingredient-level supervision
- Grad-CAM provides coarse explanations

---

## 🚀 Possible Improvements

- Multi-label classification
- Ingredient or part-based detection
- Higher input resolution
- Stronger data augmentation

---

## ✅ Summary

This project demonstrates how **Explainable AI techniques** such as Grad-CAM can be used to better understand deep learning models for food recognition, beyond simply reporting accuracy.
