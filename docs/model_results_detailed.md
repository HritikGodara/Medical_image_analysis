# 🧪 Model Evaluation Results (Detailed)

**Project:** Medical Image Analysis  
**Generated on:** 2026-03-27 15:59:08

---

# 🫁 Chest X-Ray (Pneumonia)

## Overall Metrics
- Accuracy: 0.8766
- Precision: 0.8724
- Recall: 0.8620
- F1-Score: 0.8666

## Classification Report
| Class       | Precision | Recall | F1-Score | Support |
|------------|----------|--------|----------|---------|
| NORMAL     | 0.86     | 0.80   | 0.83     | 234     |
| PNEUMONIA  | 0.89     | 0.92   | 0.90     | 390     |

## Confusion Matrix
| Actual \ Predicted | NORMAL | PNEUMONIA |
|--------------------|--------|-----------|
| NORMAL             | 188    | 46        |
| PNEUMONIA          | 31     | 359       |

---

# 🦠 COVID-19 Radiography

## Overall Metrics
- Accuracy: 0.7330
- Precision: 0.7596
- Recall: 0.6571
- F1-Score: 0.6864

## Classification Report
| Class            | Precision | Recall | F1-Score | Support |
|------------------|----------|--------|----------|---------|
| COVID            | 0.72     | 0.34   | 0.47     | 723     |
| Lung_Opacity     | 0.70     | 0.74   | 0.72     | 1202    |
| Normal           | 0.74     | 0.87   | 0.80     | 2038    |
| Viral Pneumonia  | 0.87     | 0.67   | 0.76     | 269     |

## Confusion Matrix
| Actual \ Predicted | COVID | Lung_Opacity | Normal | Viral Pneumonia |
|--------------------|-------|--------------|--------|-----------------|
| COVID              | 248   | 168          | 307    | 0               |
| Lung_Opacity       | 41    | 891          | 270    | 0               |
| Normal             | 54    | 175          | 1783   | 26              |
| Viral Pneumonia    | 0     | 32           | 57     | 180             |

---

# 🧠 Brain Tumor MRI

## Overall Metrics
- Accuracy: 0.6931
- Precision: 0.7042
- Recall: 0.6931
- F1-Score: 0.6635

## Classification Report
| Class       | Precision | Recall | F1-Score | Support |
|------------|----------|--------|----------|---------|
| glioma     | 0.78     | 0.40   | 0.53     | 400     |
| meningioma | 0.66     | 0.41   | 0.51     | 400     |
| notumor    | 0.74     | 0.97   | 0.84     | 400     |
| pituitary  | 0.64     | 0.98   | 0.77     | 400     |

## Confusion Matrix
| Actual \ Predicted | glioma | meningioma | notumor | pituitary |
|--------------------|--------|------------|---------|-----------|
| glioma             | 161    | 82         | 63      | 94        |
| meningioma         | 37     | 166        | 77      | 120       |
| notumor            | 4      | 0          | 390     | 6         |
| pituitary          | 4      | 4          | 0       | 392       |

---

# 📊 Final Summary

| Model         | Accuracy | Precision | Recall | F1-Score |
|--------------|----------|----------|--------|----------|
| Chest X-Ray  | 0.8766   | 0.8724   | 0.8620 | 0.8666   |
| COVID-19     | 0.7330   | 0.7596   | 0.6571 | 0.6864   |
| Brain Tumor  | 0.6931   | 0.7042   | 0.6931 | 0.6635   |

---

# 📌 Key Observations

- Chest X-Ray model shows strong and balanced performance.
- COVID-19 model struggles with detecting COVID cases (low recall).
- Brain Tumor model performs well for some classes but poorly for others.
