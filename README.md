# 🖼️ CIFAR-10 Image Classification using CNN & Transfer Learning

## 📌 Project Overview

This project focuses on **image classification using deep learning** with the CIFAR-10 dataset.

Two different approaches were implemented and compared:

1. **Custom Convolutional Neural Network (CNN)** built from scratch
2. **Transfer Learning using MobileNetV2** pretrained on ImageNet

The objective was to understand how a CNN learns image features from scratch and how a pretrained deep learning model can be adapted to a new image classification problem.

---

## 🎯 Objectives

* Build a CNN model for multi-class image classification.
* Apply transfer learning using MobileNetV2.
* Compare the performance of a custom CNN with a pretrained model.
* Evaluate models using accuracy, loss, precision, recall and F1-score.
* Analyze model predictions using a confusion matrix.
* Understand practical challenges involved in image classification.

---

## 📊 Dataset

The **CIFAR-10** dataset was used for this project.

It contains **60,000 color images** belonging to 10 different classes.

| Class | Description |
| ----- | ----------- |
| ✈️    | Airplane    |
| 🚗    | Automobile  |
| 🐦    | Bird        |
| 🐱    | Cat         |
| 🦌    | Deer        |
| 🐶    | Dog         |
| 🐸    | Frog        |
| 🐴    | Horse       |
| 🚢    | Ship        |
| 🚚    | Truck       |

The dataset contains:

* **50,000 training images**
* **10,000 test images**
* Image size: **32 × 32 × 3**
* Number of classes: **10**

---

## 🧹 Data Preprocessing

The following preprocessing steps were performed:

* Loaded the CIFAR-10 dataset using TensorFlow/Keras.
* Normalized pixel values for the custom CNN.
* Resized images to **96 × 96 × 3** for MobileNetV2.
* Applied MobileNetV2-specific preprocessing for transfer learning.
* Used a validation split during training.

---

# 🧠 Model 1 — Custom CNN

A CNN architecture was developed from scratch using convolutional and pooling layers.

### Architecture

```text
Input Image (32 × 32 × 3)
        ↓
Conv2D (32 filters)
        ↓
MaxPooling2D
        ↓
Conv2D (64 filters)
        ↓
MaxPooling2D
        ↓
Conv2D (128 filters)
        ↓
MaxPooling2D
        ↓
Flatten
        ↓
Dense (128, ReLU)
        ↓
Dropout (0.5)
        ↓
Dense (10, Softmax)
```

The model was trained using:

* **Optimizer:** Adam
* **Loss:** Sparse Categorical Crossentropy
* **Metric:** Accuracy

---

# 🚀 Model 2 — MobileNetV2 Transfer Learning

For the second approach, **MobileNetV2 pretrained on ImageNet** was used as the feature extractor.

The original ImageNet classification head was removed using:

```python
include_top=False
```

The MobileNetV2 base model was followed by custom classification layers.

### Architecture

```text
Input Image (96 × 96 × 3)
        ↓
MobileNetV2
(Pretrained on ImageNet)
        ↓
GlobalAveragePooling2D
        ↓
Dense (128, ReLU)
        ↓
Dropout (0.3)
        ↓
Dense (10, Softmax)
```

Initially, the pretrained base model was frozen so that the newly added classification layers could be trained.

---

## 📈 Model Evaluation

Both models were evaluated using:

* Test Accuracy
* Training Accuracy
* Validation Accuracy
* Training Loss
* Validation Loss
* Precision
* Recall
* F1-score
* Confusion Matrix

### Performance Comparison

| Model       | Test Accuracy |
| ----------- | ------------: |
| Custom CNN  |       **XX%** |
| MobileNetV2 |       **XX%** |

> Replace `XX%` with the final accuracy values from your notebook.

---

## 📊 Confusion Matrix

A confusion matrix was generated to analyze the classification performance for each CIFAR-10 class.

It helps identify:

* Correct predictions
* Misclassified images
* Classes that are difficult to distinguish
* Class-wise model performance

The classification report provides **precision, recall and F1-score** for each class.

---

## 🔍 CNN vs Transfer Learning

| Feature                  | Custom CNN              | MobileNetV2                |
| ------------------------ | ----------------------- | -------------------------- |
| Feature learning         | From scratch            | Pretrained                 |
| Training data            | CIFAR-10                | ImageNet + CIFAR-10        |
| Training time            | Higher                  | Lower when frozen          |
| Feature extraction       | Learned during training | Already learned            |
| Customization            | High                    | Moderate                   |
| Computational efficiency | Depends on architecture | Designed to be lightweight |
| Transfer learning        | ❌                       | ✅                          |

The custom CNN provides a good understanding of how convolutional networks learn visual features, while MobileNetV2 demonstrates the benefits of reusing features learned from a large-scale dataset.

---

## ⚙️ Challenges Faced

During implementation, several challenges were encountered:

* CIFAR-10 images are originally **32 × 32**, while MobileNetV2 was configured for **96 × 96** input images.
* Images had to be resized before being passed to MobileNetV2.
* MobileNetV2-specific preprocessing was required.
* The original ImageNet classification head had to be removed.
* The output layer needed to be modified for CIFAR-10's 10 classes.
* Predictions for the complete test dataset were required for generating the confusion matrix and classification report.
* Training time and computational resources had to be considered.

---

## 🌍 Real-World Applications

Image classification models can be used in many real-world applications, including:

* 🚗 Autonomous vehicles
* 🏥 Medical image classification
* ♻️ Automated waste classification
* 🌱 Agricultural disease detection
* 🛍️ Retail product recognition
* 🔐 Security and surveillance
* 📱 Mobile image recognition applications

Lightweight architectures such as MobileNetV2 are particularly useful for applications where computational resources are limited.

---

## 🔮 Future Improvements

Possible improvements include:

* Data augmentation
* Fine-tuning MobileNetV2
* Hyperparameter tuning
* Learning-rate scheduling
* Early stopping
* Batch normalization
* Experimenting with different pretrained architectures
* Improving class-wise performance
* Model deployment using Flask or Streamlit
* Converting the model to TensorFlow Lite for mobile deployment

---

## 🛠️ Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* CNN
* Transfer Learning
* MobileNetV2
* Image Classification

---

## 📂 Project Structure

```text
CIFAR10-Image-Classification/
│
├── CIFAR10_CNN_MobileNetV2.ipynb
├── README.md
└── requirements.txt
```

---

## ▶️ How to Run

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
```

### 2. Install dependencies

```bash
pip install tensorflow numpy matplotlib seaborn scikit-learn
```

### 3. Run the notebook

Open:

```text
CIFAR10_CNN_MobileNetV2.ipynb
```

and execute the cells sequentially.

---

## 💡 Key Learning Outcomes

Through this project, I gained practical experience in:

* Building CNN architectures from scratch
* Working with image datasets
* Image preprocessing and normalization
* Transfer learning
* Using pretrained MobileNetV2
* Model evaluation
* Confusion matrix analysis
* Classification reports
* Preventing overfitting using dropout
* Comparing deep learning approaches
* Understanding the practical challenges of computer vision projects

---

## 👩‍💻 Author

**Apeetha S.**

Aspiring Data Scientist | Machine Learning & Deep Learning Enthusiast

### 🔗 Connect with me

* LinkedIn: [Add your LinkedIn profile]
* GitHub: [Add your GitHub profile]

---

⭐ If you found this project useful, feel free to explore the repository and connect with me!
