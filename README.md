# 🧠 Brain Tumor Classification using Neural Networks

## 📖 Project Overview
This project focuses on the binary classification of brain MRI images into two categories: **Tumor** and **Healthy (Normal)**. By leveraging advanced image processing techniques and a custom Dense Neural Network (MLP) built with TensorFlow/Keras, the model achieves an impressive validation accuracy of **~94%**. 

The pipeline includes robust image preprocessing steps such as grayscale conversion, resizing, adaptive histogram equalization, median filtering for noise reduction, and Laplacian edge detection to enhance tumor boundaries before feeding the data into the neural network.

---

## 📂 Dataset
The dataset used in this project is the **Brain Tumor Data Set**, which contains MRI images categorized into:
- 🩺 **Tumor**: 2,513 images
- 🧬 **Healthy**: 2,087 images

The dataset contains images of various formats (JPEG, PNG, TIFF) and varying resolutions (e.g., 512x512, 256x256, 300x240).

---

## 🛠️ Data Preprocessing
To ensure the model receives high-quality and uniform input, the following preprocessing steps were applied using `OpenCV`:
1. **Format Conversion & Resizing**: All images are converted to grayscale and resized to a uniform dimension of `(225, 255)`.
2. **Noise Reduction**: Applied a **Median Filter** to remove salt-and-pepper noise common in MRI scans.
3. **Contrast Enhancement**: Used **Adaptive Histogram Equalization (CLAHE)** to enhance the contrast of the brain tissues, making tumor regions more distinct.
4. **Edge Detection**: Applied **Laplacian** edge detection to highlight the sharp boundaries of potential tumors.
5. **Flattening**: The 2D images are flattened into 1D vectors to serve as input for the Dense Neural Network.

---

## 🧠 Model Architecture
The classification model is built using **TensorFlow/Keras** and follows a Dense Neural Network (Multi-Layer Perceptron) architecture. **Dropout** and **Batch Normalization** layers are strategically placed to prevent overfitting and stabilize training.

| Layer Type | Output Shape | Parameters |
| :--- | :---: | :---: |
| **Dense** | (None, 50) | 2,868,800 |
| **Dropout** | (None, 50) | 0 |
| **Dense** | (None, 40) | 2,040 |
| **BatchNormalization** | (None, 40) | 160 |
| **Dense** | (None, 30) | 1,230 |
| **Dropout** | (None, 30) | 0 |
| **Dense** | (None, 10) | 310 |
| **BatchNormalization** | (None, 10) | 40 |
| **Dense (Output)** | (None, 1) | 11 |

- **Total params**: 2,872,591
- **Trainable params**: 2,872,491
- **Non-trainable params**: 100

---

## 🚀 Training & Evaluation
- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Batch Size**: 128
- **Epochs**: 10 (with Early Stopping, `patience=2`)
- **Metrics**: Accuracy

### 📊 Results
The model achieved a **Validation Accuracy of ~93.65%** on the unseen validation data, demonstrating strong capability in distinguishing between healthy brain tissue and tumors based on the preprocessed MRI images.

*(Feel free to add your Accuracy/Loss training graphs here)*
<!-- ![Accuracy Graph](path/to/your/accuracy_plot.png) -->

---

## 📦 Dependencies
To run this project, you will need the following Python libraries. You can install them using `pip`:

```bash
pip install tensorflow keras opencv-python numpy pandas matplotlib glob2
