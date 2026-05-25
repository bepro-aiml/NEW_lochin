---
title: "Lesson 5 - Scale and Encode"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 5 - Scale and Encode (and the most important rule)

The model only understands **numbers on a similar scale**. The theory, then `practice.ipynb`.

# Key words
| Word | Simple meaning |
| --- | --- |
| scale | make numbers a similar size |
| StandardScaler | makes mean = 0 and spread = 1 |
| encode | turn text categories into numbers |
| OneHotEncoder | makes a 0/1 column for each category |
| fit | LEARN from the training data |
| transform | APPLY what was learned |
| leakage | the model secretly sees test data - bad |

---

# 1. The most important rule: split first
Split the data into **train** (80%) and **test** (20%) **before** you prepare it.
The model learns from train. We keep test hidden to check it honestly.

```python
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42)
```

**Why:** if we prepare using the test data too, the model gets secret help. That is **leakage**.

---

# 2. Scale numbers - StandardScaler
Some columns are big (TotalCharges = 8000), some small (tenure = 5). The model thinks the big numbers matter more. We fix this: make every column mean 0 and spread 1.

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
scaler.fit(X_train[num_cols])              # LEARN from train
train_scaled = scaler.transform(X_train[num_cols])   # APPLY
test_scaled  = scaler.transform(X_test[num_cols])    # APPLY (same numbers)
```

**Why:** so big and small columns are treated fairly.

---

# 3. fit vs transform (remember this!)
- **fit** = LEARN (the mean, the median, the categories) from the **training** data.
- **transform** = APPLY what was learned to change the data.
- We **fit on train only**, then **transform** both train and test.

**Common mistake:** calling `fit` on the test data. That is leakage.

---

# 4. Encode text - OneHotEncoder
The model cannot read words. We turn each category into 0/1 columns.

```python
from sklearn.preprocessing import OneHotEncoder
enc = OneHotEncoder(handle_unknown="ignore", sparse_output=False)
```

Example: `Contract = "Two year"` becomes `[0, 0, 1]`.

`handle_unknown="ignore"` = if a NEW category appears later, do not crash.

---

# 5. What is leakage, simply?
Leakage = the model sees information it should not see while learning. The test score looks great, but in real life the model fails. Splitting first and fitting on train only prevents it.

---

# Quick summary
- **Split first** (train/test). Never let the model see test data while learning.
- **StandardScaler** makes numbers a fair size.
- **OneHotEncoder** turns text into 0/1 columns; use `handle_unknown="ignore"`.
- **fit = learn (train only), transform = apply (train and test).**
- Fitting on test data = **leakage** = bad.

# Now do this
Open `practice.ipynb`, split + scale + encode the real data, and do the assignment.
