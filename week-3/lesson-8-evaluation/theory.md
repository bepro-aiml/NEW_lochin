---
title: "Lesson 8 - Check How Good the Model Is"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 8 - Check How Good the Model Is

Training is not enough. We must measure the model. The theory, then `practice.ipynb`.

# Key words
| Word | Simple meaning |
| --- | --- |
| accuracy | how many predictions are correct overall |
| precision | of our "Yes" guesses, how many were right |
| recall | of all real "Yes", how many we caught |
| confusion matrix | a table of correct vs wrong, per class |
| overfitting | great on train, bad on test |
| underfitting | bad on train and test |

---

# 1. Always test on unseen data
We check the model on the **test** set (data it never saw). This gives an honest score.

---

# 2. Accuracy
Accuracy = correct predictions / all predictions.
```python
from sklearn.metrics import accuracy_score
accuracy_score(y_test, y_pred)
```

---

# 3. Accuracy can lie (very important)
If 95% of customers do NOT churn, a lazy model that always says "no churn" gets 95% accuracy - but catches ZERO churners. So accuracy alone is not enough when one class is rare.

**This is why we also use precision and recall.**

---

# 4. Precision and Recall
- **Precision** = of all the cases we predicted "Yes", how many were really Yes.
- **Recall** = of all the real "Yes" cases, how many we actually caught.

Example (catching churners):
- High precision = when we say "will churn", we are usually right.
- High recall = we catch most of the real churners.

**F1** combines precision and recall into one number.

---

# 5. Confusion matrix
A small table showing correct and wrong predictions for each class:
```
[[true No,  wrong No ],
 [wrong Yes, true Yes]]
```
It shows exactly where the model makes mistakes.

---

# 6. Overfitting vs underfitting
- **Overfitting** = 99% on train, 60% on test. The model memorized; it fails on new data.
- **Underfitting** = 60% on train AND 60% on test. The model is too simple.
- **Good** = high on both, and close to each other.

---

# Quick summary
- Test on **unseen** data for an honest score.
- **Accuracy** can lie when one class is rare - also use **precision** and **recall**.
- **Confusion matrix** shows where mistakes happen.
- **Overfitting** = good train, bad test. **Underfitting** = bad on both.

# Now do this
Open `practice.ipynb`, measure the model, and do the assignment.
