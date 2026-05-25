---
title: "Lesson 9 - More Models and Tuning"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 9 - More Models and Tuning

There are many models. The theory, then `practice.ipynb`. This lesson is an overview - do not worry about every detail.

# Key words
| Word | Simple meaning |
| --- | --- |
| Decision Tree | asks yes/no questions to decide |
| Random Forest | many trees together |
| KNN | copies the answer of the nearest examples |
| SVM | finds the best border between groups |
| regularization | keeps weights small to avoid overfitting |
| cross-validation | test on several splits for a fair score |
| Grid Search | tries many settings to find the best |

---

# 1. Decision Tree
A tree asks a series of yes/no questions about the features ("tenure < 6? contract = month-to-month?") until it reaches an answer. Easy to understand, but one tree can overfit.

---

# 2. Random Forest
A **forest** is many decision trees together. Each tree votes; the forest takes the majority. It is more stable and overfits less than one tree.

**Why it usually wins:** the mistakes of single trees cancel out.

---

# 3. KNN (K-Nearest Neighbors)
To predict a new point, KNN looks at the **K closest** known examples and copies their answer (the majority).

---

# 4. SVM (Support Vector Machine)
SVM finds the best **border** that separates two groups, with the widest gap.

---

# 5. Regularization (L1 / L2)
Regularization adds a small penalty for large weights, so the model stays simple and does not overfit.
- **L2 (Ridge)** keeps weights small.
- **L1 (Lasso)** can push some weights to exactly 0, removing useless features.

---

# 6. Cross-validation
Instead of one train/test split, we try several different splits and average the scores. The result is more trustworthy.

---

# 7. Grid Search - find the best settings
Models have **hyperparameters** (settings), like how deep a tree is. **Grid Search** tries many combinations and keeps the best one. No more guessing by hand.

---

# Quick summary
- **Decision Tree** = yes/no questions. **Random Forest** = many trees, stronger.
- **KNN** = copy the nearest neighbors. **SVM** = best border.
- **Regularization** stops overfitting (L1 can drop features).
- **Cross-validation** = fairer score. **Grid Search** = find the best settings.

# Now do this
Open `practice.ipynb`, train a Random Forest, compare it, and do the assignment.
