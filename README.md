# food101recognition
Explainable Food Recognition (Food-101)

This project builds a food image classification model using ResNet34 and explains its predictions using Grad-CAM.

The goal is not only to classify food images, but also to understand why the model makes correct or incorrect predictions.

What This Project Does

Trains a food classifier on the Food-101 dataset

Uses transfer learning with a pretrained ResNet34

Applies Grad-CAM to visualize model attention

Analyzes misclassified samples to understand model errors

Dataset

Food-101

101 food categories

1,000 images per class

Balanced dataset

Many visually similar classes (e.g. seafood, desserts)

Model

Backbone: ResNet34 pretrained on ImageNet

Final fully connected layer replaced for 101 food classes

Training Strategy

The model is trained in two stages:

Stage 1 – Train Classifier Head

Freeze the ResNet34 backbone

Train only the final fully connected (FC) layer

Purpose: adapt ImageNet features to Food-101

Stage 2 – Fine-tuning

Unfreeze the last ResNet block (layer4)

Fine-tune layer4 + FC with a smaller learning rate

Purpose: improve high-level food feature representation

Evaluation

The model is evaluated using:

Accuracy

Macro F1-score

Stage 2 improves performance significantly compared to Stage 1 and shows more balanced results across classes.

Explainability with Grad-CAM

Grad-CAM is used to:

Visualize which image regions influence predictions

Explain why predictions are correct

Analyze why misclassifications happen

Grad-CAM is applied to the last convolutional layer of ResNet34.

Misclassification Analysis

For misclassified samples, Grad-CAM shows that:

The model often focuses on shared or visually dominant ingredients

Visually similar dishes can confuse the model

Errors are systematic, not random

Example patterns:

Seafood dishes confused due to similar textures

Breakfast dishes confused due to similar crispy bases

What This Project Shows

Accuracy alone is not enough to understand model behavior

Grad-CAM provides useful visual explanations

The model relies heavily on visually salient regions

Explainability helps identify model limitations

Limitations

Single-label classification

No ingredient-level supervision

Grad-CAM provides coarse (not pixel-perfect) explanations

Possible Improvements

Multi-label classification

Ingredient or part-based detection

Higher input resolution

Stronger data augmentation

Summary

This project demonstrates how Explainable AI techniques like Grad-CAM can be used to better understand deep learning models for food recognition, beyond just reporting accuracy.
