# BrainSync: EEG Processing & AI Pipeline

## Overview  
The BrainSync AI model pipeline is designed to process, analyze, and interpret EEG signals. It follows a structured deep learning approach and integrates machine learning techniques for brain signal decoding.

The pipeline includes:
- Feature extraction from EEG signals using time-domain, frequency-domain, and graph-based methods.  
- Deep learning models such as CNNs, RNNs, and Transformers for EEG classification.  
- Real-time AI inference and potential hardware deployment on embedded systems.

This document outlines the pipeline architecture from raw EEG data to model predictions.

---

## Pipeline Overview  

The AI pipeline follows a modular and structured approach:

1. Raw EEG Data Collection  
2. Preprocessing and Artifact Removal  
3. Feature Extraction  
4. Model Training  
5. Real-Time Inference  

Each stage is described below.

---

## Raw EEG Data Collection  
- The dataset used is BCI Competition IV - Dataset 2a in `.gdf` format.  
- EEG is recorded from 22 electrodes placed on the scalp.  
- The dataset contains four motor imagery tasks: left hand, right hand, both feet, and tongue.  
- Event markers are used to label motor imagery tasks.  

---

## Preprocessing and Artifact Removal  
EEG signals require preprocessing before being used in machine learning models.  

The preprocessing steps include:
- Bandpass filtering (0.5 - 100 Hz) to remove unwanted frequencies.  
- Notch filtering (50 Hz) to remove power-line noise.  
- Independent Component Analysis (ICA) for artifact removal (eye/muscle movement).  
- Epoch extraction (segmenting continuous EEG into fixed time windows).  
- Normalization using z-score standardization.  

These steps enhance signal quality and improve model performance.

---

## Feature Extraction  
EEG signals are transformed into numerical features that are used for machine learning models.  

The extracted features include:

| Feature Type | Description |
|-------------|-------------|
| Time-Domain Features | Raw EEG signals segmented into time windows. |
| Frequency-Domain Features | Power Spectral Density (PSD), Fourier and Wavelet transforms. |
| Graph-Based Features | EEG signals represented as spatial graphs for Graph Neural Networks. |
| Deep Representations | Learned embeddings from self-supervised models. |

These features allow models to identify patterns in brain signals.

---

## Deep Learning Model Training  
Once features are extracted, a deep learning model is trained to classify EEG signals.

### Baseline Model (CNN-RNN Hybrid)  
- A convolutional neural network (CNN) is used to extract spatial EEG features.  
- A recurrent neural network (RNN) with LSTM/GRU layers is used to capture temporal dependencies in EEG sequences.  

### Advanced Model (Transformers + Graph Neural Networks)  
- Graph Neural Networks (GNNs) treat EEG signals as a structured graph for improved spatial decoding.  
- Transformers use self-attention mechanisms to capture long-range dependencies in EEG signals.  
- Self-Supervised Learning (SSL) techniques are applied to learn EEG representations without labels.  

Training parameters:
- Loss Function: Contrastive Learning + Cross-Entropy Loss.  
- Optimizer: AdamW with Cosine Annealing.  
- Batch Size: 64.  
- Learning Rate: 0.001.  
- Training Framework: PyTorch and PyTorch Lightning.  

---

## Real-Time Inference  
The trained model is deployed for real-time EEG decoding.

- The model performs EEG classification with latency below 100ms.  
- AI inference is optimized for edge deployment on embedded hardware.  
- The system is designed to integrate with brain-controlled applications.  

This ensures that BrainSync is structured for real-time applications rather than offline research models.

---

