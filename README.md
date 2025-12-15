# NetVisionPioneers

A **semi-supervised network intrusion detection research project** built on the **UNSW-NB15 dataset**, focused on **reproducing a state-of-the-art research paper** and then **systematically improving upon it** using deep learning, attention mechanisms, and ensemble models.

This repository demonstrates:
* Exact reproduction of a published semi-supervised IDS paper
* Multiple architectural variants (GRU, GCN, Self-Attention)
* Training with **as little as 0.5%–10% labeled data**
* Final models that **surpass the original paper’s reported F1-score**

---

## 📌 Project Objectives
1. **Faithfully reproduce** a published IDS model on UNSW-NB15
2. Validate reported results under low-label regimes
3. Propose architectural enhancements
4. Achieve **higher F1-score with the same or fewer labels**

---

## 📂 Dataset
* **UNSW-NB15** (official release)
* Includes:
  * Flow-level CSV features
  * Raw PCAP files (optional)

The code automatically downloads:
* `UNSW_NB15_training-set.csv`
* `UNSW_NB15_testing-set.csv`
* Feature metadata

---

## 🧠 Methodology Overview

### 1️⃣ Paper Reproduction Model
This model closely follows the referenced paper’s design:

**Components:**
* GRU-based sequence autoencoder
* Graph Convolution Network (GCN) branch
* Feature reconstruction loss
* Focal loss for class imbalance
* Semi-supervised learning via label masking

**Training setup:**
* 0.5% – 20% labeled data
* Reconstruction + supervised loss

**Result:**
* Achieves **~97.5–98.1% F1-score** with **10% labeled data**
* Matches the paper’s reported Table-5 results

---

### 2️⃣ Enhanced Model (Author Contribution)
A novel architecture designed to improve performance:

**Key ideas:**
* Treat selected flow statistics as a **short temporal sequence**
* Apply **Multi-Head Self-Attention**
* Fuse with an MLP branch
* Add **learnable label propagation**

**Result:**
* **~99.15% F1-score** using only **10% labeled data**
* Outperforms the base paper

---

### 3️⃣ Final Ensemble (State-of-the-Art)
A powerful semi-supervised ensemble:

**Models used:**
* LightGBM (tree-based)
* CatBoost (categorical residuals)
* Deep Neural Network

**Strategy:**
* Train only on **10% labeled samples**
* Soft-voting with optimized weights

**Result:**
* Best overall performance
* Clearly surpasses all baseline models

---

## ⚙️ Installation
```bash
pip install torch torch-geometric scikit-learn pandas numpy tqdm
pip install lightgbm catboost 
```
## (Optional GPU support)
```bash
pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cu118
```
## ▶️ How to Run

Open the notebook or Python script
Run cells sequentially
The script will:
Download datasets
Preprocess features
Train multiple models
Print evaluation metrics


No manual dataset setup required.

### 📊 Evaluation Metrics

Accuracy
Precision
Recall
F1-score (primary metric)

Evaluation is performed on the official UNSW-NB15 test split.

### 🏆 Key Results Summary
Model,Labeled Data,F1-Score
Paper Reproduction,10%,~0.978
Attention Model (Ours),10%,~0.991
Ensemble Model,10%,Highest

### 🧪 Reproducibility

Fixed random seeds
Identical preprocessing pipeline
Matches reported results before improvements


### 📚 Research & Academic Use
This project is suitable for:

Research paper reproduction
Final Year Projects (FYP)
IDS benchmarking
Semi-supervised learning studies

You are free to:

Extend architectures
Add PCAP-based features
Explore online/streaming IDS


### ⚠️ Disclaimer
This code is intended for research and educational purposes only.
It is not production-hardened for live network defense systems.

## 👤 Authors
Umaima Hashmi  📧 umaimahashmi65@gmail.com

Mueez Rizwan (Corresponding Author)  📧 mueez7364@gmail.com

Nooran Ishtiaq  📧 nooranishtiaq@gmail.com



📄 Citation
If you use this work, please cite our paper:
```@article{hashmi2025semi,
  title={Semi-Supervised Encrypted Malicious Traffic Detection: Reproduction and Enhancement on the UNSW-NB15 Dataset},
  author={Hashmi, Umaima and Rizwan, Mueez and Ishtiaq, Nooran},
  journal={Submitted to IEEE ICIT 2025},
  year={2025}
}
```
Base paper:
```@article{liu2024semi,
  title={Semi-Supervised Encrypted Malicious Traffic Detection Based on Multimodal Traffic Characteristics},
  author={Liu, Ming and Yang, Qichao and Wang, Wenqing and Liu, Shengli},
  journal={Sensors},
  volume={24},
  number={20},
  pages={6507},
  year={2024},
  publisher={MDPI}
}
```
