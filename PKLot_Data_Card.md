# PKLot Dataset Card

## 1. Dataset Overview

- Dataset: PKLot
- Task: Binary parking-space occupancy classification
- Classes: empty, occupied
- Source: PKLot parking-space image dataset
- Input resolution used for modeling: 96 x 96 RGB

## 2. Cleaned Sample Statistics

| Split | Images | Empty | Occupied | Locations | Unique Days |
|---|---:|---:|---:|---|---:|
| Train | 20000 | 10000 | 10000 | PUC | 29 |
| Validation | 4000 | 2000 | 2000 | PUC | 9 |
| Test | 4000 | 2000 | 2000 | UFPR04, UFPR05 | 63 |

## 3. Weather Distribution

| Split | Sunny | Cloudy | Rainy |
|---|---:|---:|---:|
| Train | 9979 | 6032 | 3989 |
| Validation | 3107 | 306 | 587 |
| Test | 2293 | 1460 | 247 |

## 4. Data Preparation

- Cleaned and balanced samples were prepared for each split.
- No missing metadata values were detected.
- No duplicate metadata rows were detected within each split.
- Images were resized to 96 x 96 pixels.
- ImageNet normalization was applied.
- Random horizontal flipping was used for training augmentation.

## 5. Split Strategy and Leakage Prevention

- Training: PUC, 29 days.
- Validation: PUC, 9 different days.
- Test: UFPR04 and UFPR05, 63 days.
- No overlapping image paths across splits.
- No overlapping location-date combinations across splits.
- Training and validation share a site but use disjoint dates.
- Test locations are disjoint from training and validation.
- Content-based duplicate screening was also performed during dataset preparation.

## 6. Label Quality Audit

- Method: Visual review of 100 sampled training images.
- Sampling: 50 empty and 50 occupied images.
- Observed label errors: 0.
- Observed error rate: 0.00%.
- One-sided 95% upper error-rate bound: 2.95%.
- Confidence method: Clopper-Pearson.
- The bound assumes independent samples and reliable visual review.
- No obvious label mismatches were observed.

## 7. Limitations

- Weather distributions differ between splits.
- Images from the same cameras may be correlated.
- Label quality was assessed on a sample, not the full dataset.
- The test set evaluates transfer to different PKLot locations.
- CNRPark+EXT is used separately for external domain-shift evaluation.

## 8. Intended Use

- Research and educational evaluation of parking occupancy classifiers.
- Results should not be interpreted as guaranteed performance across all cameras, lighting conditions, or parking facilities.
