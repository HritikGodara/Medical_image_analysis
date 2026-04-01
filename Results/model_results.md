# Medical Image Analysis — Model Results & Evaluation Metrics

**Project:** AI for Sustainable Healthcare  
**Platform:** Kaggle (TensorFlow 2.19.0, Tesla T4 x2 GPU)  
**Architecture:** DenseNet121 + Custom Classification Head  
**Date:** March 2026

---

## Summary

| Model | Accuracy | Precision | Recall | F1 Score | Epochs Run | Best Val Acc |
|---|---|---|---|---|---|---|
| Chest X-Ray (Pneumonia) | 90.87% | 90.76% | 89.62% | 90.12% | 6 (early stop) | 100% |
| COVID-19 Radiography | 87.07% | 83.84% | 89.26% | 86.13% | 29 (early stop) | 87.45% |
| Brain Tumor MRI | 88.88% | 89.23% | 88.88% | 88.56% | 30 (full) | 95.00% |

---

## Chest X-Ray (Pneumonia)

**Dataset:** 5,856 images — 4,273 PNEUMONIA / 1,583 NORMAL  
**Test Set:** 624 images (390 PNEUMONIA, 234 NORMAL)  
**Class Weights:** NORMAL 1.94 / PNEUMONIA 0.67  
**Training:** 6 epochs, early stopped at epoch 6 (patience=5)

### Overall Metrics

| Metric | Score |
|---|---|
| Accuracy | 0.9087 |
| Precision | 0.9076 |
| Recall | 0.8962 |
| F1 Score | 0.9012 |

### Per-Class Classification Report

| Class | Precision | Recall | F1 Score | Support |
|---|---|---|---|---|
| NORMAL | 0.90 | 0.85 | 0.87 | 234 |
| PNEUMONIA | 0.91 | 0.95 | 0.93 | 390 |
| **Macro Avg** | 0.91 | 0.90 | 0.90 | 624 |
| **Weighted Avg** | 0.91 | 0.91 | 0.91 | 624 |

### Training History (Validation Accuracy per Epoch)

| Epoch | Train Acc | Val Acc | LR |
|---|---|---|---|
| 1 | 0.8129 | 0.9375 | 1e-3 |
| 2 | 0.9116 | 0.9375 | 1e-3 |
| 3 | 0.9150 | 0.9375 | 1e-3 |
| 4 | 0.9239 | 0.8750 | 1e-3 |
| **5 ✅ best** | **0.9313** | **1.0000** | **2e-4** |
| 6 | 0.9354 | 0.9375 | 2e-4 |

> Note: Validation set is only 16 samples — val accuracy fluctuates significantly. Test set evaluation (624 samples) is the reliable figure.

---

## COVID-19 Radiography

**Dataset:** 21,165 images — COVID 3,616 / Lung Opacity 6,012 / Normal 10,192 / Viral Pneumonia 1,345  
**Test Set:** 4,232 images (val split used as test)  
**Class Weights:** COVID 1.46 / Lung Opacity 0.88 / Normal 0.52 / Viral Pneumonia 3.93  
**Training:** 29 epochs, early stopped (patience=5 from epoch 24 best)

### Overall Metrics

| Metric | Score |
|---|---|
| Accuracy | 0.8707 |
| Precision | 0.8384 |
| Recall | 0.8926 |
| F1 Score | 0.8613 |

### Per-Class Classification Report

| Class | Precision | Recall | F1 Score | Support |
|---|---|---|---|---|
| COVID | 0.80 | 0.88 | 0.83 | 723 |
| Lung Opacity | 0.88 | 0.84 | 0.86 | 1,202 |
| Normal | 0.92 | 0.87 | 0.89 | 2,038 |
| Viral Pneumonia | 0.76 | 0.98 | 0.86 | 269 |
| **Macro Avg** | 0.84 | 0.89 | 0.86 | 4,232 |
| **Weighted Avg** | 0.88 | 0.87 | 0.87 | 4,232 |

### Training History (Key Epochs)

| Epoch | Train Acc | Val Acc | LR | Note |
|---|---|---|---|---|
| 1 | 0.6192 | 0.6961 | 1e-3 | |
| 2 | 0.7508 | 0.8062 | 1e-3 | |
| 5 | 0.7976 | 0.8448 | 1e-3 | |
| 9 | 0.8316 | 0.8464 | 1e-3 | |
| 13 | 0.8316 | 0.8599 | 2e-4 | LR reduced |
| 16 | 0.8441 | 0.8646 | 2e-4 | |
| 20 | 0.8452 | 0.8696 | 4e-5 | |
| 21 | 0.8500 | 0.8710 | 4e-5 | |
| **24 ✅ best** | **0.8468** | **0.8745** | **4e-5** | |
| 29 | 0.8573 | 0.8674 | 1.6e-6 | Early stopped |

---

## Brain Tumor MRI

**Dataset:** 7,200 images — 1,800 per class (glioma, meningioma, notumor, pituitary)  
**Test Set:** 1,600 images (400 per class)  
**Class Weights:** Equal (1.0 per class — balanced dataset)  
**Training:** 30 epochs (full run, best at epoch 29)

### Overall Metrics

| Metric | Score |
|---|---|
| Accuracy | 0.8888 |
| Precision | 0.8923 |
| Recall | 0.8888 |
| F1 Score | 0.8856 |

### Per-Class Classification Report

| Class | Precision | Recall | F1 Score | Support |
|---|---|---|---|---|
| glioma | 0.94 | 0.74 | 0.83 | 400 |
| meningioma | 0.86 | 0.81 | 0.84 | 400 |
| notumor | 0.92 | 1.00 | 0.96 | 400 |
| pituitary | 0.85 | 1.00 | 0.92 | 400 |
| **Macro Avg** | 0.89 | 0.89 | 0.89 | 1,600 |
| **Weighted Avg** | 0.89 | 0.89 | 0.89 | 1,600 |

### Training History (Key Epochs)

| Epoch | Train Acc | Val Acc | LR | Note |
|---|---|---|---|---|
| 1 | 0.6737 | 0.8560 | 1e-3 | |
| 2 | 0.8310 | 0.8798 | 1e-3 | |
| 4 | 0.8616 | 0.8976 | 1e-3 | |
| 8 | 0.8948 | 0.9083 | 1e-3 | |
| 10 | 0.8858 | 0.9238 | 1e-3 | |
| 17 | 0.9149 | 0.9333 | 2e-4 | LR reduced |
| 21 | 0.9244 | 0.9381 | 2e-4 | |
| 25 | 0.9241 | 0.9393 | 2e-4 | |
| 28 | 0.9319 | 0.9476 | 4e-5 | |
| **29 ✅ best** | **0.9460** | **0.9500** | **4e-5** | |
| 30 | 0.9330 | 0.9321 | 4e-5 | |

---

## Key Observations

**Chest X-Ray** hit 90.87% test accuracy with strong pneumonia recall (95%). The model generalizes well for a binary task. The tiny val set (16 images) made epoch-level val accuracy unreliable — test set numbers are what matter.

**COVID-19** reached 87.07% on a hard 4-class problem. Viral Pneumonia recall is exceptionally high (98%), which is the upweighted minority class behaving as intended. COVID detection improved significantly from the earlier run (88% recall vs. 34% in previous results).

**Brain Tumor MRI** achieved 88.88% test accuracy despite the challenge of separating glioma and meningioma. Glioma recall is the weak spot (74%) — these cases get confused with meningioma most often. The notumor and pituitary classes are near-perfect.

---

## Outputs

| File | Path |
|---|---|
| Brain Tumor model weights | `/kaggle/working/exported_models/brain_tumor_model.h5` |
| Brain Tumor metadata | `/kaggle/working/exported_models/brain_tumor_metadata.pkl` |
| Brain Tumor class labels | `/kaggle/working/exported_models/brain_tumor_classes.json` |
| Chest X-Ray best checkpoint | `/kaggle/working/chest_xray_best.keras` |
| COVID-19 best checkpoint | `/kaggle/working/covid19_best.keras` |
| Brain Tumor best checkpoint | `/kaggle/working/brain_tumor_best.keras` |
