# RSNA Knee Abnormality Detection

Exploratory and preprocessing notebook for the [RSNA Knee Abnormality Detection](https://www.kaggle.com/competitions/rsna-knee-abnormality-detection) Kaggle competition, hosted by the Radiological Society of North America (RSNA).

## Project Objective

Build a machine learning system that predicts twelve clinically important knee abnormalities from multimodal knee MRI studies (DICOM imaging + free-text radiology reports).

## Target Abnormalities (12 labels)

1. ACL (anterior cruciate ligament injury)
2. MCL (medial collateral ligament injury)
3. Medial Meniscus tear
4. Lateral Meniscus tear
5. Medial OA (osteoarthritis)
6. Lateral OA (osteoarthritis)
7. PF OA (patellofemoral osteoarthritis)
8. Effusion
9. Synovitis
10. Baker's cyst
11. Contusion
12. Fracture

## Evaluation Metric

Macro-averaged AUC-ROC across all twelve target labels.

## Notebook Contents

This notebook (`rsna-knee-abnormality-detection-ammu (1).ipynb`) walks through the early stages of the pipeline:

- **Environment check** — verifying Python, PyTorch, and GPU/CUDA availability on Kaggle.
- **Dataset discovery** — exploring the competition file structure (`train.csv`, `train_series.csv`, DICOM folders).
- **Training data inspection** — examining study-level labels and metadata.
- **MRI series metadata inspection** — reviewing `Anatomical_Plane`, `Fluid_Sensitive`, and `Fat_Suppression` fields.
- **DICOM visualization** — loading and displaying raw knee MRI slices with `pydicom`.
- **Preprocessing pipeline**:
  - Pixel intensity normalization (0–1 range)
  - Resizing to a standardized 224×224 spatial resolution
  - Intensity distribution analysis (histograms)
  - Percentile-based contrast enhancement
  - Threshold-based image segmentation to isolate the anatomical region
- **Feature extraction** — computing quantitative intensity features (mean, median, standard deviation, min, max) from the segmented MRI region.
- **Feature dataset construction and validation** — building, saving, and verifying a structured feature dataset for downstream modeling.

## Planned Development Strategy

```
Environment → Dataset → DICOM → Preprocessing → Validation → Baseline Model →
Evaluation → Model Improvement → Pseudo-Labels → DINO/DINOv3 → Fusion →
Ensemble → Test Inference → Submission
```

## Dataset

The competition dataset is provided by RSNA on Kaggle and is **not included in this repository**, in compliance with the competition's Data Security rules (no redistribution of Competition Data outside registered participants). To reproduce this notebook, join the competition on Kaggle and attach the dataset directly inside a Kaggle Notebook environment.

## Requirements

- Python 3
- `pandas`, `numpy`
- `pydicom`
- `torch`
- `matplotlib`
- Kaggle Notebook environment (GPU recommended)

## Status

Work in progress — currently at the preprocessing and feature-extraction stage. Baseline model training, multimodal (image + text) fusion, and final submission generation are upcoming steps.

## License

Code in this repository is shared under an OSI-approved open-source license, in line with the competition's Public Code Sharing rules (Section 3.6.b of the Official Competition Rules). Competition data itself remains subject to RSNA's MIRA license and is not part of this repository.

## Author

Prepared by the repository owner for participation in the RSNA Knee Abnormality Detection Kaggle competition (2026).
