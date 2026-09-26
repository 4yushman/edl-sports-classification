# Sports Image Classification

Fine-tuned YOLOv11-nano (classification) on a 100-class sports dataset.

## Two Runs (Comparison)

| Run | Hardware | Classes | Train imgs | Top-1 Acc | Notes |
|---|---|---|---|---|---|
| **Local CPU** (main) | i3, 8 GB RAM | 10 (subset) | 400 | 47% | Lab PC constraint |
| **Kaggle GPU** (bonus) | T4, 16 GB | 100 (full) | 13,493 | 91.4% | See kaggle/ folder |

## Main Submission: Local CPU (this folder)

- test.ipynb — main notebook (renamed from Q1_Sports_Finetune_Clean.ipynb)
- sports_predictions.csv — predictions on 100 unseen test images
- best_sports_model.pt — fine-tuned weights

### Why only 47%?

Trained on 10 of 100 classes (400 images) due to:
- i3 CPU + 8 GB RAM (no GPU)
- Time constraint (deadline 5 PM)
- Full 100-class training on CPU would take ~19 hours

## Bonus: Kaggle GPU (kaggle/ folder)

Upgraded to Kaggle free T4 GPU for full training:
- All 100 classes, 13,493 images
- 10 epochs in ~10 minutes
- Top-1: 91.4% | Top-5: 99.2%
- See kaggle/README.md for full details

## Dataset

- 100 sports, 13,493 train / 500 valid / 500 test images
- Folder: train/, valid/, test/ + sports.csv
- Source: Kaggle "100 Sports Image Classification" by gpiosenka

## Model

- Base: yolo11n-cls.pt (pretrained on ImageNet, 1000 classes)
- Adapted head: 1000 → 100 classes (auto-detected from folders)
- Local CPU run: 10 epochs, batch 8, imgsz 224
- Kaggle GPU run: 10 epochs, batch 32, imgsz 224, T4 GPU

## Files Structure

    .
    ├── README.md                       (this file)
    ├── requirements.txt                (dependencies)
    ├── test.ipynb                      (main submission notebook - CPU run)
    ├── best_sports_model.pt            (fine-tuned weights - CPU run)
    ├── sports_predictions.csv          (predictions - CPU run, 100 test imgs)
    ├── yolo11n-cls.pt                  (pre-trained base model)
    └── kaggle/                         (bonus GPU run)
        ├── README.md
        ├── kaggle-sports.ipynb         (full Kaggle notebook)
        └── results/
            ├── best_sports_model.pt
            ├── sports_predictions.csv
            └── confusion_matrix_normalized.png

## How to run

### Main submission (CPU)

    pip install -r requirements.txt
    jupyter notebook test.ipynb

### Bonus GPU run (Kaggle)

1. Open kaggle/kaggle-sports.ipynb on Kaggle
2. Add dataset: search "sports classification" by gpiosenka
3. Settings → Accelerator → GPU T4 x2
4. Run all cells
