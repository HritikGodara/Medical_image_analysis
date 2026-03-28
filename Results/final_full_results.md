# 📊 Complete Model Evaluation Report

## 🫁 Chest X-Ray (Pneumonia)

### Overall Metrics
- Accuracy: 0.9087
- Precision: 0.9076
- Recall: 0.8962
- F1-Score: 0.9012

### Classification Report
| Class | Precision | Recall | F1 | Support |
|------|----------|--------|----|--------|
| NORMAL | 0.90 | 0.85 | 0.87 | 234 |
| PNEUMONIA | 0.91 | 0.95 | 0.93 | 390 |

### Confusion Matrix
| Actual \ Pred | NORMAL | PNEUMONIA |
|--------------|--------|-----------|
| NORMAL | 198 | 36 |
| PNEUMONIA | 21 | 369 |

---

## 🦠 COVID-19

### Overall Metrics
- Accuracy: 0.8707
- Precision: 0.8384
- Recall: 0.8926
- F1-Score: 0.8613

### Classification Report
| Class | Precision | Recall | F1 | Support |
|------|----------|--------|----|--------|
| COVID | 0.80 | 0.88 | 0.83 | 723 |
| Lung_Opacity | 0.88 | 0.84 | 0.86 | 1202 |
| Normal | 0.92 | 0.87 | 0.89 | 2038 |
| Viral Pneumonia | 0.76 | 0.98 | 0.86 | 269 |

### Confusion Matrix
| Actual \ Pred | COVID | L.O | Normal | Viral |
|--------------|------|-----|--------|-------|
| COVID | 635 | 34 | 48 | 6 |
| Lung Opacity | 84 | 1007 | 111 | 0 |
| Normal | 78 | 105 | 1779 | 76 |
| Viral Pneumonia | 1 | 0 | 4 | 264 |

---

## 🧠 Brain Tumor

### Overall Metrics
- Accuracy: 0.8888
- Precision: 0.8923
- Recall: 0.8888
- F1-Score: 0.8856

### Classification Report
| Class | Precision | Recall | F1 | Support |
|------|----------|--------|----|--------|
| glioma | 0.94 | 0.74 | 0.83 | 400 |
| meningioma | 0.86 | 0.81 | 0.84 | 400 |
| notumor | 0.92 | 1.00 | 0.96 | 400 |
| pituitary | 0.85 | 1.00 | 0.92 | 400 |

### Confusion Matrix
| Actual \ Pred | glioma | meningioma | notumor | pituitary |
|--------------|--------|------------|---------|-----------|
| glioma | 298 | 53 | 27 | 22 |
| meningioma | 17 | 326 | 8 | 49 |
| notumor | 0 | 1 | 399 | 0 |
| pituitary | 1 | 0 | 0 | 399 |

---

## 📌 Final Summary

| Model | Accuracy | F1 Score |
|------|----------|----------|
| Chest X-Ray | 0.9087 | 0.9012 |
| COVID-19 | 0.8707 | 0.8613 |
| Brain Tumor | 0.8888 | 0.8856 |
