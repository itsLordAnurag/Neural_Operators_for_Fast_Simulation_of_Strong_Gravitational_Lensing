# Neural Operators for Fast Simulation of Strong Gravitational Lensing

## Project Overview

This repository contains my submission for the GSoC 2025 project under ML4SCI. The project focuses on classifying strong gravitational lensing images into distinct categories (no substructure, subhalos, and vortices) using deep learning. It specifically explores the performance differences between standard Convolutional Neural Networks (CNNs) and advanced continuous-space models like Fourier Neural Operators (FNOs).

## Repository Structure

* `/common_test_1/`: Contains the implementation for the multi-class image classification task using a standard CNN architecture (ResNet18).
* `/specific_test_4/`: Contains the implementation of the Neural Operator-based classifier and the comparative analysis.
  * `specific test IVneural operators.ipynb`: FNO implementation and spectral convolution layers.
  * `cnn_vs_fno.ipynb`: Comparative analysis and evaluation scripts aligning the preprocessing steps to directly evaluate the CNN vs. FNO.

## Project Tasks

### Common Test I: Multi-Class Classification

Classification of strong gravitational lensing images into three distinct classes: 
1. No substructure
2. Subhalo substructure
3. Vortex substructure

The baseline model is built using PyTorch. While the original dataset utilizes min-max normalization, custom preprocessing and physics-aware data augmentation strategies (like 360-degree rotations and horizontal/vertical flips) are implemented to improve feature extraction and model robustness. 
* **Evaluation Metrics:** ROC curve (Receiver Operating Characteristic curve) and AUC score (Area Under the ROC Curve).

### Specific Test IV: Neural Operators

This task replaces the standard convolutional feature extractor with a **Fourier Neural Operator (FNO)** architecture. 
1. **Model Architecture:** The model utilizes neural operator layers that operate in continuous function space via spectral convolutions (using Fast Fourier Transforms), truncating high-frequency modes to focus on global structural signals.
   <h2>FNO Architecture</h2>

    <p align="center">
      <img src="Specific_Test%20IV%20_Neural_Operators/fno_architecture.jpg" width="700"/>
    </p>
3. **Strategy & Comparison:** The implementation explores how FNOs naturally capture global spatial features and continuous macro-structures of gravitational lenses, in contrast to the localized, discrete pixel patches processed by standard CNNs. 
4. **Evaluation:** The FNO model is evaluated on the exact same strong lensing validation subset and directly compared against the CNN baseline from Common Test I.
* **Evaluation Metrics:** ROC curve, AUC score, and a comparative analysis of both approaches.

## Links

* [ML4SCI GSoC 2025 Project Description](https://ml4sci.org/gsoc/2026/proposal_DEEPLENSE3.html)
* [Dataset](https://drive.google.com/file/d/1ZEyNMEO43u3qhJAwJeBZxFBEYc_pVYZQ/view)
* [Paper 1](https://arxiv.org/abs/2010.08895)
* [Paper 2](https://arxiv.org/abs/2108.08481)
