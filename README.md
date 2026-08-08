# MLP-Based Image Compression

## Overview

This project implements a simple **image compression system using a Multilayer Perceptron (MLP) Autoencoder** built entirely from scratch with **NumPy**. Instead of relying on deep learning frameworks such as TensorFlow or PyTorch, the project manually implements forward propagation, backpropagation, weight updates, and momentum-based optimization.

The goal is to learn a compact representation of image blocks while reconstructing the original image with minimal reconstruction error.

---

## Features

* Image preprocessing using OpenCV
* Conversion of grayscale images into non-overlapping **8×8 blocks**
* Automatic dataset construction from image folders
* Lossless reconstruction verification before training
* Custom implementation of a neural network autoencoder
* Mini-batch gradient descent with momentum
* Validation after every training epoch
* Automatic saving of the best-performing model
* Visualization of reconstructed images

---

## Methodology

### 1. Dataset Preparation

The training and testing images are first converted to grayscale and divided into **8×8 non-overlapping blocks**.

Each block is flattened into a **64-dimensional feature vector**, creating the dataset used for training.

```
256 × 256 image
        ↓
8 × 8 blocks
        ↓
1024 blocks per image
        ↓
64-dimensional vectors
```

The generated vectors are stored as CSV files for efficient loading during training.

---

### 2. Data Verification

Before training, the generated CSV files are reconstructed back into images to ensure that the preprocessing stage is completely lossless.

Each reconstructed image is compared pixel-by-pixel with the original image.

---

### 3. Autoencoder Architecture

The project implements a fully connected autoencoder with the following architecture:

```
Input Layer      : 64 neurons
Hidden Layer     : 32 neurons
Output Layer     : 64 neurons
Activation       : ReLU
Loss Function    : Mean Squared Error (MSE)
```

The hidden layer acts as the compressed representation of each image block.

---

### 4. Training

The neural network is implemented manually using NumPy and includes:

* Weight initialization
* Forward propagation
* Backpropagation
* Mini-batch gradient descent
* Momentum optimization
* Validation after each epoch
* Best model checkpointing

The dataset is normalized to the range **[0, 1]** before training and split into:

* **80% Training**
* **20% Validation**

The model with the lowest validation error is automatically saved as:

```
best_weights.pkl
```

---

## Project Structure

```
./
├── data/
│   ├── train
│   └── test
├── notebooks/
│   └── main.ipynb
├── requirements.txt
└── README.md
```

---

## Requirements

Install the required Python packages:

```bash
pip install -r requirements.txt
```

Main dependencies include:

* Python
* NumPy
* Pandas
* OpenCV
* Matplotlib
* scikit-learn
* tqdm

---

## Running the Project

1. Clone the repository.

2. Install the required dependencies.

3. Ensure the dataset is organized as:

```
data/
├── train/
└── test/
```

4. Open:

```
notebooks/main.ipynb
```

5. Run the notebook cells sequentially.

The notebook will:

* Build the training and testing datasets
* Verify dataset reconstruction
* Train the autoencoder
* Save the best model weights
* Display reconstructed images

---

## Learning Objectives

This project demonstrates:

* Image preprocessing techniques
* Block-based image representation
* Neural network implementation from scratch
* Gradient descent optimization
* Momentum-based learning
* Autoencoder-based dimensionality reduction
* Image reconstruction

---

## Technologies

* Python
* NumPy
* OpenCV
* Pandas
* Matplotlib
* scikit-learn
* Jupyter Notebook

---
