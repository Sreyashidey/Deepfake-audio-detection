# RawNet2-Inspired Audio Spoof Detection

This repository contains the partial implementation of an audio spoof detection model inspired by the RawNet2 architecture. The model takes raw waveform audio as input and attempts to classify it as **genuine** or **spoofed** using a combination of convolutional and recurrent neural network layers.

> **Note:** The full training process was not completed due to time and hardware constraints. However, the core architecture and pipeline are implemented, with detailed explanations provided.

---

##  Model Overview

The model architecture includes:

- **1D Convolutional layers** for raw audio feature extraction  
- **Residual Blocks** to enable deeper representation learning  
- **GRU (Gated Recurrent Units)** for capturing temporal dependencies  
- **Fully Connected Layer** for binary classification (spoof/genuine)  

This design follows principles from [RawNet2](https://arxiv.org/abs/2006.03214), enabling end-to-end learning directly from raw waveform inputs.

---

##  Current Status

-  Core model architecture implemented  
-  Code is modular and documented  
-  Data loading and preprocessing prepared  
-  **Training not fully completed** due to very long training time per epoch (~38 seconds per sample)  
-  Detailed explanation of model structure and training pipeline included in [`model_description.md`](model_description.md)

---

##  Dependencies

- Python 3.7+
- PyTorch
- NumPy
- Librosa
- Scikit-learn
- Pandas
- tqdm
All dependencies are listed in requirements.txt.
---
##  Dataset 
Due to licensing and file size constraints, the dataset is not included in this repository.
Link - https://www.kaggle.com/datasets/awsaf49/asvpoof-2019-dataset

