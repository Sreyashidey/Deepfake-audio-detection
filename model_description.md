#  Model Description

##  Overview

This project implements a **RawNet2-inspired deep learning model** for **audio classification** using **raw waveform inputs**. The architecture is designed to process 1D audio signals directly, utilizing residual CNN blocks and a GRU-based recurrent layer to capture both spatial and temporal audio features.

---

##  Architecture

### 1. Convolutional Front-End
- A 1D convolution layer extracts low-level features from the raw audio.
- Followed by Batch Normalization for stabilizing training.

### 2. Residual Blocks (ResBlocks)
- Two stacked ResBlocks.
- Each contains:
  - Two Conv1D layers
  - Batch Normalization
  - ReLU activations
  - Skip connection for residual learning
- Helps in mitigating vanishing gradients and enhances feature propagation.

### 3. Gated Recurrent Unit (GRU)
- A single-layer **bidirectional GRU** captures long-term temporal dependencies in the extracted features.
- GRU processes the sequence and outputs the final hidden state.

### 4. Fully Connected Classifier
- A linear layer maps the final GRU output to class logits.
- Output is passed to `CrossEntropyLoss` for training.

---

## ⚙️Model Flow

```
Input waveform 
    → Conv1D 
    → BatchNorm 
    → ResBlock 1 
    → ResBlock 2 
    → GRU 
    → FC 
    → Output (logits)
```

- GRU input size is matched with the final output size of the ResBlock stack.
- Output size is 2 for binary classification.

---

## Novelty

- **Raw waveform input** – eliminates the need for handcrafted features like MFCCs or spectrograms.
- **CNN-GRU hybrid** – combines the spatial strength of CNNs with the temporal capabilities of RNNs.
- **Lightweight RawNet2 adaptation** – reduced complexity while retaining key architectural principles.

---

## Current Implementation Status

- Model code, training loop, and architecture setup are implemented successfully.
- **Full training not completed** due to large training time requirements.
    - Example: Only ~6% completed after 2 hours (`38.46s/iteration`, >3000 iterations/epoch).
- Suggestions for future work:
  - Use of checkpointing
  - Mixed-precision training
  - Learning rate warm-up
  - More powerful GPU or cloud compute

---

##  Dataset

- Dataset consists of raw audio tensors and corresponding labels.
- DataLoader is set up to shuffle and batch the dataset efficiently.
- Please refer to the notebook for preprocessing and loading steps.

---
