# Medical Image Analysis using Deep Learning
## AI for Sustainable Healthcare (SDG 3)

---

## Overview

This project uses deep learning and computer vision to detect diseases from medical images — chest X-rays and MRI scans. The goal is to build accurate, explainable models that could hold up in real clinical settings.

It targets UN SDG 3 (Good Health & Well-Being), which in practice means: catch diseases earlier, make diagnosis cheaper, and reach places that don't have specialists.

---

## What It Does

- Trained on 3 separate medical datasets
- Uses DenseNet121 with transfer learning
- Full evaluation suite: accuracy, precision, recall, F1, confusion matrices
- Grad-CAM for explainability — so you can see *where* the model is looking
- Exports models as `.h5` / `.pkl` for deployment

---

## Results

| Model | Accuracy | F1 Score | Notes |
|-------|----------|----------|-------|
| Chest X-Ray (Pneumonia) | 90.8% | 90.1% | Strong recall (~95%) |
| COVID-19 Radiography | 87.0% | 86.1% | Handles multi-class well |
| Brain Tumor MRI | 88.8% | 88.5% | Struggles a bit with glioma |

---

## Model Breakdown

### Chest X-Ray
Pneumonia recall sits around 95%, which matters more than accuracy here — you'd rather flag a healthy patient for review than miss a sick one. Generalizes well across the test set.

### COVID-19
Multi-class classification across several COVID severity categories. Recall improved significantly during training (~88%). Grad-CAM confirms the model focuses on lung regions rather than artifacts.

### Brain Tumor MRI
Near-perfect on *notumor* and *pituitary* classes. Glioma is harder — the visual patterns are less distinct, and the model reflects that. Overall performance is still solid.

---

## Explainability (Grad-CAM)

Grad-CAM generates heatmaps over the input image showing which regions drove the prediction. For X-rays, it highlights lung tissue. For MRIs, it highlights the tumor area.

This matters because a model that gets the right answer for the wrong reason is not actually useful in clinical settings.

---

## Tech Stack

- **Language:** Python 3.10+
- **Framework:** TensorFlow / Keras
- **Model:** DenseNet121 (pretrained on ImageNet)
- **Libraries:** NumPy, Pandas, OpenCV, Matplotlib, Scikit-learn
- **Training platform:** Kaggle (GPU)

---

## Datasets

- Chest X-Ray (Pneumonia)
- COVID-19 Radiography Dataset
- Brain Tumor MRI Dataset

---

## Architecture

```
Input (224×224×3)
↓
DenseNet121 (pretrained on ImageNet)
↓
Global Average Pooling
↓
Dense Layers + Dropout
↓
Softmax Output
```

---

## Evaluation

Each model was evaluated using accuracy, precision, recall, F1 score, confusion matrix, and Grad-CAM visualizations.

---

## Project Structure

```
├── notebooks/
│   └── medical_image_analysis.ipynb
├── models/
│   ├── chest_xray_model.h5
│   ├── covid_model.h5
│   └── brain_tumor_model.h5
├── results/
│   ├── confusion_matrices/
│   └── gradcam_outputs/
└── README.md
```

---

## Known Limitations

- Glioma classification is the weakest link — the model gets confused by overlapping visual features with other tumor types
- Performance will vary on datasets with different scanner hardware or imaging protocols
- No web interface yet; inference requires running the notebook directly

---

## What's Next

- Wrap inference in a Flask or FastAPI endpoint
- Add real-time inference support
- Dig deeper into glioma misclassifications — likely needs targeted augmentation or a dedicated sub-model
- Explore integration with DICOM-based hospital workflows

---

## Author

**Hritik Godara**  
AI/ML Developer

---