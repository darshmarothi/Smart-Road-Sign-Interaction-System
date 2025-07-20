
# Smart Road Sign Interaction System

## Background

Traffic sign recognition is a vital component of modern intelligent transportation systems. Whether for **autonomous vehicles** or **driver assistance applications**, accurate detection and classification of road signs is essential for road safety and situational awareness.

This project presents a real-time road sign recognition system using **Computer Vision** and a **Convolutional Neural Network (CNN)** trained on the **German Traffic Sign Recognition Benchmark (GTSRB)**. It classifies various types of road signs with high accuracy and provides instant predictions via a **Gradio-based UI**.

The primary aim is to offer a **baseline system** for traffic sign classification that can be further optimized with more advanced techniques in future iterations.

---

## Theory

### Why CNN?

Convolutional Neural Networks (CNNs) are especially suitable for image classification tasks. Their ability to detect spatial hierarchies of features makes them ideal for identifying patterns in road signs such as edges, curves, or colors. A lightweight CNN architecture was chosen here to handle **32x32 grayscale images**, reducing complexity while maintaining performance.

### Dataset

This system is trained on the **GTSRB (German Traffic Sign Recognition Benchmark)**, which contains over 50,000 images of traffic signs across 43 categories. For this project, we narrowed the scope to 6 essential traffic signs for real-time inference.

### Preprocessing Techniques

To enhance image clarity and uniformity before model training:
- **Grayscale Conversion**
- **Histogram Equalization**
- **Gaussian Blurring**

These steps improve contrast and reduce noise, aiding the model in recognizing features across varied lighting and road conditions.

---

## Code Structure

```
smart-road-sign-interaction/
├── SmartRoadSignRecognition.ipynb   # Jupyter Notebook with model training and testing
├── requirements.txt                 # Python dependencies
├── accuracy_report.txt              # Accuracy & loss metrics summary
├── results/                         # Screenshots of test predictions
└── README.md                        # Project documentation
```

---

## Training & Model

The notebook uses a **simple CNN architecture** with the following setup:

- Input: 32x32 grayscale image
- 2 Conv2D layers with ReLU activation
- MaxPooling layers
- Flatten + Dense layers
- Softmax output for 6 classes

Training configuration:
- **Optimizer**: Adam
- **Loss Function**: Categorical Crossentropy
- **Epochs**: 40+
- **Validation Accuracy**: 99.63%
- **Validation Loss**: 0.0032

---

## Overall System Architecture
![Overall System Architecture]("C:\Users\Work\OneDrive\Pictures\Screenshots\Screenshot 2025-07-20 134945.png")

## Testing & Results

The trained model was tested using unseen data and deployed using **Gradio** for real-time sign detection.

| Metric              | Value       |
|---------------------|-------------|
| Validation Accuracy | 99.63%      |
| Validation Loss     | 0.0032      |
| Epochs Trained      | 40          |

### Sample Outputs

- `Turn Left Ahead` → ✅ Detected
- `Speed Limit (30km/h)` → ✅ Detected
- `No Entry` → ✅ Detected

> View screenshots in the `/results/` folder.

---

## Manual Setup (Optional)

### Prerequisites
- Python 3.8+
- pip
- Jupyter or VS Code
- (Optional) Git

### 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/smart-road-sign-interaction.git
cd smart-road-sign-interaction
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Train the Model

Open the notebook and train the model. Minimum 40 epochs recommended:
```bash
jupyter notebook SmartRoadSignRecognition.ipynb
```

### 4. Launch the Gradio UI

If you’ve saved the trained model:
```bash
python gradio_app/interface.py
```

---

## Evaluation

The current model demonstrates strong performance across limited classes, but real-world deployments may require:

- More diverse training data
- Detection of occluded/blurred signs
- Deployment on edge devices for real-time processing

Further optimizations may include:
- Transfer learning using MobileNet or ResNet
- Sign detection via object detection frameworks (YOLO, SSD)

---

## References

- [German Traffic Sign Recognition Benchmark (GTSRB)](https://benchmark.ini.rub.de/?section=gtsrb&subsection=news)
- TensorFlow & Keras Documentation
- Gradio for UI Deployment
