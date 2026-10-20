# Mushroom Classification: Edible or Poisonous?

A beginner machine learning project that predicts whether a mushroom is **edible or poisonous** from features you can see or smell, such as its cap colour, odour and gill size. I trained and compared two models, a **Decision Tree** and **K-Nearest Neighbours (KNN)**.

## Why it is useful

Many poisonous mushrooms look very similar to edible ones. A quick, reliable check based on simple observations could help foragers avoid dangerous mistakes.

## Dataset

- **Source:** [UCI Machine Learning Repository: Mushroom dataset](https://archive.ics.uci.edu/dataset/73/mushroom)
- **Size:** 8,124 mushrooms, 22 features, 1 target column (`e` = edible, `p` = poisonous)
- **Balance:** 4,208 edible and 3,916 poisonous, roughly an even split
- All features are letters (categories), for example odour `n` = none and `f` = foul.

## What I did

1. **Loaded the data** with pandas and added column names.
2. **Checked for missing values.** The `stalk-root` column had 2,480 of them (about 30%), so I removed that column.
3. **Prepared features and target.** Split the table into clues (X) and answers (y), then used **one-hot encoding** to turn the letters into 0/1 columns.
4. **Split the data** into 80% for training (6,499 mushrooms) and 20% for testing (1,625 mushrooms).
5. **Trained two models:** a Decision Tree and KNN with k = 5.
6. **Evaluated** both with accuracy and a confusion matrix.

## Results

| Model | Accuracy | Mistakes (out of 1,625 test mushrooms) |
| --- | --- | --- |
| Decision Tree | 100% | 0 |
| KNN (k = 5) | 100% | 0 |

Both confusion matrices show 843 edible and 782 poisonous mushrooms classified correctly, with **no poisonous mushroom wrongly called edible**.

The Decision Tree's most important features were:

| Feature | Meaning | Importance |
| --- | --- | --- |
| `odor_n` | no smell | 62% |
| `bruises_t` | the mushroom bruises | 17% |
| `odor_p` | pungent smell | 9% |
| `odor_f` | foul smell | 6% |
| `spore-print-color_r` | green spore print | 3% |

## Conclusion

Both models tie at 100% accuracy, but I would choose the **Decision Tree** because it can explain its decisions. It shows that **smell is the most important clue**, making up about 78% of its decisions. KNN cannot explain itself in this way, and it is slower because it compares each new mushroom with every training mushroom.

**What I learned:**
- Real data can hide missing values in unexpected forms, like `?`.
- Models need numbers, so categories must be encoded first.
- Testing on unseen data is what proves a model has really learned.
- For safety problems, the confusion matrix matters more than accuracy alone, because some mistakes are far more dangerous than others.

## How to run it

**Option 1: Google Colab (easiest, nothing to install)**
1. Go to [colab.research.google.com](https://colab.research.google.com).
2. Click **File → Upload notebook** and choose `mushroom_classification.ipynb`.
3. Click **Runtime → Run all**.

**Option 2: On your own computer**
1. Install Python 3, then run:
   ```
   pip install pandas scikit-learn matplotlib jupyter
   ```
2. Open the notebook:
   ```
   jupyter notebook mushroom_classification.ipynb
   ```
3. Run the cells from top to bottom.

The notebook downloads the dataset automatically from the UCI website, so an internet connection is needed.

## Built with

Python · pandas · scikit-learn · matplotlib · Google Colab

---

Made by Manya Agarwal, CSE Core, VIT Vellore.
