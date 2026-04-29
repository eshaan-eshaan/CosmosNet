# 🌌 CosmosNet — Galaxy Morphology Classification

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB"/>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
</p>

> Automated classification of galaxy morphology using **ResNet-18** and **EfficientNet-B0** on 120,000 Hubble Space Telescope images from the Galaxy Zoo dataset.

***

## 🔭 Overview

Astronomy surveys like Hubble, JWST, and the upcoming LSST produce millions of galaxy images that must be classified by their morphological type — spiral, elliptical, merger, etc. Manual classification is slow and unscalable.

CosmosNet automates this process using deep learning, comparing a **ResNet-18 baseline** against **EfficientNet-B0** for efficiency and accuracy on the Galaxy Zoo Hubble dataset.

***

## 🗂️ Dataset

| Property | Value |
|---|---|
| Dataset | Galaxy Zoo Hubble (GZH) |
| Total Images | ~68,000+ galaxies |
| Image Size | 64×64 to 128×128 pixels |
| Telescope | Hubble ACS (F814W, F606W filters) |
| Label Type | Soft vote fractions (0.0 – 1.0) |
| Source | [data.galaxyzoo.org](https://data.galaxyzoo.org) / [HuggingFace](https://huggingface.co/datasets/mwalmsley/gz-hubble) |

### Morphology Categories
- 🌀 **Spiral** — tight/loose arms, bar presence
- ⚪ **Elliptical** — smooth, rounded structure
- 💥 **Merger / Disturbed** — asymmetric, tidal features
- 🟡 **Lenticular** — disk without spiral arms

***

## 🧠 Models

| Model | Parameters | Type | Purpose |
|---|---|---|---|
| ResNet-18 | 11.1M | Baseline CNN | Standard benchmark |
| EfficientNet-B0 | 5.3M | Efficient CNN | Proposed model |

Both models are trained on the same dataset with identical train/val/test splits for fair comparison.

***

## 🏗️ Architecture

```
Input Galaxy Image (64×64 RGB)
        ↓
  Preprocessing & Normalization
        ↓
  CNN Feature Extraction
  (ResNet-18 / EfficientNet-B0)
        ↓
  Fully Connected Layers
        ↓
  Morphology Prediction (Softmax)
        ↓
  Top-3 Evolutionary Stage Output
```

***

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| Deep Learning | PyTorch + TorchVision |
| Data Pipeline | `galaxy-datasets` library |
| Backend API | FastAPI |
| Frontend | React + Tailwind CSS |
| Training Platform | Google Colab (T4/A100 GPU) |
| Deployment | Render (backend) + Vercel (frontend) |
| Experiment Tracking | Weights & Biases |

***

## 📊 Results

| Model | Accuracy | Params | Inference Time |
|---|---|---|---|
| ResNet-18 (Baseline) | ~% | 11.1M | ~ms |
| EfficientNet-B0 | ~% | 5.3M | ~ms |

> Results will be updated after full training run.

***

## 🚀 Run Locally

### 1. Clone the repository
```bash
git clone https://github.com/eshaan-eshaan/CosmosNet.git
cd CosmosNet
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download dataset
```python
from galaxy_datasets import galaxy_zoo_hubble
dataset = galaxy_zoo_hubble(root='./data', download=True)
```

### 4. Train the model
Open `AstroResNetANN.ipynb` in Google Colab and run all cells.

### 5. Start the API (after training)
```bash
uvicorn backend.main:app --reload
```

***

## 📁 Project Structure

```
CosmosNet/
├── AstroResNetANN.ipynb     ← Main training notebook
├── requirements.txt          ← Python dependencies
├── backend/
│   └── main.py              ← FastAPI inference server
├── frontend/
│   └── src/                 ← React web app
└── README.md
```

***

## 📦 Requirements

```
torch>=2.0.0
torchvision>=0.15.0
fastapi>=0.100.0
uvicorn>=0.23.0
galaxy-datasets>=0.1.0
Pillow>=9.0.0
numpy>=1.24.0
matplotlib>=3.7.0
scikit-learn>=1.3.0
```

***

## 🔬 References

- Willett et al. (2017) — Galaxy Zoo Hubble: morphological classifications for 120,000 galaxies
- Walmsley et al. (2020) — Galaxy Zoo: probabilistic morphology through Bayesian CNNs
- He et al. (2016) — Deep Residual Learning for Image Recognition (ResNet)
- Tan & Le (2019) — EfficientNet: Rethinking Model Scaling for CNNs

***

## 👤 Author

**Eshaan Guliani**  
B.Tech AI/ML Student  
GitHub: [@eshaan-eshaan](https://github.com/eshaan-eshaan)

***

<p align="center">Made with ❤️ for Advanced Neural Networks course</p>
