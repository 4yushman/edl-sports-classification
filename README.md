# EDL Lab - Q1: Sports Image Classification

Fine-tuned YOLOv11-nano (classification) on a 100-class sports dataset.

## Dataset
- 100 sports, 13,493 train / 500 valid / 500 test images
- Folder: train/, valid/, test/ + sports.csv
- Used a small subset: 10 classes × 40 images (CPU-friendly)

## Model
- Base: yolo11n-cls.pt (pretrained on ImageNet, 1000 classes)
- Adapted head: 1000 → 100 classes (auto-detected from folders)
- Epochs: 10, Batch: 8, Image size: 224

## Files
- `test.ipynb` — main notebook
- `sports_predictions.csv` — predictions on 100 unseen test images
- `best_sports_model.pt` — fine-tuned weights

## Results
- Test images: 100
- Accuracy: 47%
- Average confidence: 79.51%

## How to run
pip install ultralytics
jupyter notebook test.ipynb

## Limitations
- Trained on 10 of 100 classes (400 images) due to CPU-only 8GB machine
- Full training requires GPU and longer time
- 47% test accuracy reflects small subset; full-data training expected to reach 85%+