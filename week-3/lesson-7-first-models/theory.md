---
title: "Lesson 7 - Your First Models"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 7 - Your First Models

Now we add a model. The theory, then `practice.ipynb`.

# Key words
| Word | Simple meaning |
| --- | --- |
| model | the thing that learns the pattern and predicts |
| Linear Regression | predicts a number |
| Logistic Regression | predicts a category (Yes/No) with a probability |
| fit | train the model on data |
| predict | get answers for new data |

---

# 1. What is a model?
A model learns the pattern between the **features** (inputs) and the **label** (answer). After training, it can answer for new data it has not seen.

---

# 2. Linear Regression - predict a number
Linear Regression draws the best straight-line formula to predict a **number** (price, sales).

**Use it when:** the answer is a number.

---

# 3. Logistic Regression - predict Yes/No
Logistic Regression gives a **probability** between 0 and 1, so we can answer a **category** like churn Yes/No. If probability > 0.5 -> Yes.

**Use it when:** the answer is a category (especially two categories).

**Common mistake:** using Linear Regression for Yes/No. Use Logistic for categories.

---

# 4. Two steps: fit then predict
```python
model.fit(X_train, y_train)     # STEP 1: learn from training data
y_pred = model.predict(X_test)  # STEP 2: answer for new data
```

**Common mistake:** calling `predict` before `fit`. The model must be trained first, or it gives an error.

---

# 5. Put the model at the end of the Pipeline
We add the model as the last step of the Pipeline from Lesson 6. Now ONE object does everything: fill -> scale -> encode -> predict.

```python
from sklearn.linear_model import LogisticRegression
model = Pipeline([
    ("preprocessor", preprocessor),
    ("clf", LogisticRegression(max_iter=1000)),
])
model.fit(X_train, y_train)
```

---

# Quick summary
- A **model** learns features -> label.
- **Linear Regression** predicts a number. **Logistic Regression** predicts a category.
- Always **fit** (train) before **predict**.
- Put the model as the last step of the Pipeline = one object does everything.

# Now do this
Open `practice.ipynb`, train a Logistic Regression model, and do the assignment.
