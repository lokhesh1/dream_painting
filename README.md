# 🧠 Multimodal EEG-to-Image Alignment (Dream Decoding PoC)

This repository contains the code for a Proof-of-Concept (PoC) study investigating the feasibility of decoding visual dream imagery directly from EEG signals. 

By framing neural decoding as a **cross-modal representation learning** problem, this project aligns high-dimensional EEG time-series data with corresponding visual stimuli into a shared latent space.

## 🔬 Methodology & Architecture

Instead of training a classifier from scratch, this pipeline leverages domain-specific foundational models to extract robust feature embeddings, projecting them into the same dimensional space to monitor similarity loss.

* **EEG Encoder:** Utilizes **LUNA-base** (a foundational EEG model) to extract temporal and spatial embeddings from raw neural signals.
* **Image Encoder:** Utilizes **ResNet50** to extract visual feature embeddings from the corresponding imagery.
* **Cross-Modal Alignment:** Both the EEG and Image embeddings are passed through respective projection heads to map them into a shared latent dimension. The system optimizes a contrastive/projection loss to align the neural representations with their visual counterparts.

### Pipeline Overview
`EEG Signal` ➔ `LUNA-base` ➔ `EEG Embedding` ➔ `Projection Head` ➔ **[ Shared Latent Space ]**
`Visual Stimuli` ➔ `ResNet50` ➔ `Image Embedding` ➔ `Projection Head` ➔ **[ Shared Latent Space ]**

## 📊 Dataset
This project utilizes the **Dream2Image** dataset. 
*(Note: Briefly mention any preprocessing steps here, e.g., bandpass filtering, epoching, or artifact removal applied to the EEG data before passing it to LUNA-base).*

## 🚀 Getting Started

### Prerequisites
* Python 3.8+
* PyTorch
* MNE-Python (for EEG processing)
* standard data science libraries (`numpy`, `pandas`, `scikit-learn`)

### Installation
1. Clone the repository:
   ```bash
   git clone [https://github.com/yourusername/eeg-dream-decoding.git](https://github.com/yourusername/eeg-dream-decoding.git)
   cd eeg-dream-decoding
