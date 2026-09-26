# Kaggle GPU Run

This folder contains the Kaggle notebook + artifacts from the GPU run.

## Why Kaggle?
- Lab PC: i3, 8 GB RAM, no GPU → too slow for full 100-class training
- Kaggle: free T4 GPU → full training in ~10 min vs 19 hours CPU

## Results (Kaggle T4)
- Top-1 accuracy: 91.4%
- Top-5 accuracy: 99.2%
- Training: 10 epochs, ~10 min on T4 GPU
- Full dataset: 100 classes, 13,493 train images

## Contents
- `kaggle-sports.ipynb` — Kaggle notebook (cells 1-12)
- `results/` — training artifacts:
  - `best_sports_model.pt` — fine-tuned model
  - `sports_predictions.csv` — 100 test image predictions
  - `confusion_matrix_normalized.png` — model performance