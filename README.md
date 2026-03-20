# 🎥 Video Tampering Detection

## Overview
This project implements a **video tampering detection system** capable of distinguishing between **authentic (real)** and **manipulated (fake)** videos. With the rise of deepfake technologies and AI-based manipulations, verifying video authenticity has become crucial in fields like cybersecurity, digital forensics, and media verification.

The system leverages **deep learning techniques**, combining **spatial feature extraction** and **temporal analysis** to achieve accurate detection.

---

## Features
- Extract frames from videos for preprocessing
- Apply data augmentation for robust learning
- Use a **CNN + LSTM hybrid model**:
  - Xception for spatial feature extraction
  - LSTM to capture temporal inconsistencies
- Evaluate performance with:
  - Accuracy
  - Precision
  - Recall
  - F1-score
  - Confusion matrix
- Save the best model using ModelCheckpoint
- Reduce learning rate dynamically with ReduceLROnPlateau

---

## Dataset
The system uses a **subset of the FaceForensics++ dataset**, containing:
- **Original (Real) videos**: authentic content
- **Manipulated (Fake) videos**: DeepFakes, FaceSwap, Face2Face, NeuralTextures

> For efficiency, only a balanced subset of videos was used for training and evaluation, while preserving the diversity of manipulation types.

---

## Methodology

### 1. Data Preprocessing
- Extract a fixed number of frames per video
- Resize frames to 128×128 pixels
- Normalize pixel values to [0,1]
- Apply data augmentation (rotation, flip, zoom, brightness)

### 2. Model Architecture
- **Spatial Analysis:** Xception CNN extracts visual inconsistencies per frame
- **Temporal Analysis:** LSTM captures patterns across sequences of frames
- **Output Layer:** Softmax classifier for real/fake prediction

### 3. Training
- Train-validation-test split
- Optimizer: Adam
- Loss: Categorical Crossentropy
- Regularization: Dropout layers, learning rate scheduling

### 4. Evaluation
- Frame-level predictions aggregated to video-level
- Metrics: Accuracy, Precision, Recall, F1-score
- Visualization: Training history, confusion matrix, classification report

---

## Results
- High accuracy in detecting manipulated videos
- Balanced precision and recall, ensuring reliable detection of fakes
- Confusion matrix and F1-score provide insights into performance per class

> Example metrics (subset experiment):
