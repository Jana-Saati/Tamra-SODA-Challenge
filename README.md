# Tamra 🌴 SODA Challenge: Saudi Dates Image Classification

Deep learning models that classify 13 varieties of Saudi dates from images.
Built for the **SODA Challenge** (CCWin Challenges Series 1) on Kaggle, hosted by
the College of Computing at Umm Al-Qura University.
Course project for DS2313 (Data Analysis 1), 2026.

## 🏆 Result
- **Macro F1-Score: 0.838**
- **Rank 8** out of 46 teams on the private leaderboard

## 🎯 Objective
Automatically identify Saudi date varieties using computer vision, which can
help sort and label dates in the agricultural industry.

## 📂 Dataset
- 13 balanced classes (about 140–141 images each)
- 2,613 images: 1,829 for training and 784 for testing
- JPG and PNG formats, no corrupt files found
- Source: SODA Challenge on Kaggle (the data is not included in this repository)

## 🔧 Approach
1. **Preprocessing:** labels converted to strings, image extensions fixed,
   class weights, stratified 85/15 train/validation split
2. **Transfer Learning:** frozen backbone, trained only the final layers for 20 epochs
3. **Fine-Tuning:** unfroze all layers with a very low learning rate (1e-5) for 15 epochs
4. **Data Augmentation:** rotation, flip, zoom, brightness, shear, MixUp and CutMix
5. **Test Time Augmentation (TTA):** averaged predictions over several augmented
   versions of each test image
6. **Evaluation:** Macro F1-Score with K-Fold cross validation

## 📈 Model progress

| Model | Technique | Macro F1 |
|---|---|---|
| MobileNetV2 | Baseline | 0.411 |
| EfficientNetB3 | Transfer Learning | 0.692 |
| EfficientNetB3 | + 5x TTA | 0.786 |
| EfficientNetB3 | Fine-Tuning | 0.789 |
| **EVA02** | **MixUp + CutMix (PyTorch)** | **0.838** |

## 💡 Key takeaways
- Transfer learning and fine-tuning were very effective for image classification.
- Data augmentation (especially MixUp and CutMix) was essential to avoid overfitting.
- TTA gave a small but consistent improvement.

## 🔮 Future work
Ensembling several models, using larger backbones such as EfficientNetV2L,
higher image resolution, and longer training.

## 🛠️ Tools
Python, TensorFlow/Keras, PyTorch, Scikit-learn, Pandas, NumPy, Kaggle

## 📁 Files
- `jana-saati.ipynb`: project code
- `Tamra-Project.pdf`: project report
- `SODA Challenge
📢 Official announcement by UQU College of Computing- https://x.com/uqu_cc/status/2049025774116544880?s=46&t=2nnnu3k-uezeJSUcUaXvYw
