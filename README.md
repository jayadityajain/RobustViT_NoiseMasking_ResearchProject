# 🩺 Robust Vision Transformer for Skin Lesion Classification

Vision Transformer (ViT-Small) model for 7-class skin lesion classification on the HAM10000 dataset, with systematic robustness evaluation under real-world image corruptions.

---

## Overview

This project evaluates the robustness of a partially fine-tuned ViT-Small model under distribution shifts such as noise, blur, compression, and illumination changes.

Unlike many medical imaging models that collapse under corruption, this implementation demonstrates controlled degradation and strong structural stability.

---

## Model Details

- Architecture: ViT-Small / 16  
- Patch Size: 16×16  
- Embedding Dimension: 384  
- 12 Transformer Layers, 6 Attention Heads  
- ImageNet Pretrained  
- Partial Fine-Tuning  

Input: 224×224 RGB dermatoscopic images  
Dataset: HAM10000 (7 classes)

---

## Results

### Experiment A – Fine-Tuned ViT

| Condition      | Accuracy | Retention vs Clean |
|---------------|----------|-------------------|
| Clean         | 76.89%   | 100% |
| Gaussian      | 74.50%   | 96.9% |
| Salt & Pepper | 70.32%   | 91.5% |
| Blur          | 77.62%   | 101.0% |
| JPEG          | 75.96%   | 98.8% |
| Brightness    | 75.63%   | 98.4% |

### Experiment B – Clean-Trained ViT (No Noise Training)

| Condition       | Accuracy | Retention vs Clean |
|----------------|----------|-------------------|
| Clean          | 86.45%   | 100% |
| Gaussian Noise | 71.12%   | 82.3% |
| Salt & Pepper  | 71.38%   | 82.6% |
| Blur           | 85.19%   | 98.5% |
| JPEG           | 83.07%   | 96.1% |
| Brightness     | 85.13%   | 98.5% |

Key Observations:
- Near-complete retention under blur and brightness shifts (~98–99%)
- Strong resistance to JPEG compression
- Controlled degradation under severe Gaussian noise
- No catastrophic performance collapse

---

## Installation

```bash
git clone https://github.com/your-username/skin-lesion-vit.git
cd skin-lesion-vit
pip install -r requirements.txt

## Author

Jay Aditya Jain  
B.Tech – Computer Science Engineering  
GitHub: https://github.com/jayadityajain  
LinkedIn: https://www.linkedin.com/in/jay-aditya-jain/