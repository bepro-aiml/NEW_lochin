---
title: "Lesson 4 - Cleaning the Data"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 4 - Cleaning the Data

Real data is dirty. The model needs clean data. The theory first, then `practice.ipynb`.

# Key words
| Word | Simple meaning |
| --- | --- |
| missing value (NaN) | an empty cell |
| dtype | the type of a column (number or text) |
| median | the middle value of a column |
| mode | the most common value |
| outlier | a strange value, very far from the rest |

---

# 1. Why clean the data?
"Bad data in, bad model out." A model cannot learn from text where it expects numbers, or from empty cells. We fix these first.

---

# 2. A column that looks numeric but is text
Sometimes a column like `TotalCharges` looks like numbers but pandas reads it as **text** (`object`). Reason: a few cells are blank spaces, not numbers. One bad cell makes the whole column text.

Fix it:
```python
df["TotalCharges"] = pd.to_numeric(df["TotalCharges"], errors="coerce")
```
- `to_numeric` turns text into numbers.
- `errors="coerce"` = if a cell is not a number, make it **NaN** (instead of crashing).

**Common mistake:** doing math on the column before fixing the type -> error.

---

# 3. Find missing values
```python
df.isna().sum().sort_values(ascending=False)
```
This shows how many empty cells are in each column.

---

# 4. Fill missing numbers - median
Fill empty number cells with the **median** (the middle value):
```python
m = df["TotalCharges"].median()
df["TotalCharges"] = df["TotalCharges"].fillna(m)
```
**Why median, not mean?** A few very big values pull the mean up. The median is not moved by a few outliers, so it is safer.

---

# 5. Fill missing text - mode
For a text column, fill with the **mode** (the most common value):
```python
top = df["Contract"].mode()[0]
df["Contract"] = df["Contract"].fillna(top)
```

---

# 6. Duplicates
Two identical rows can confuse the model.
```python
df.duplicated().sum()     # how many duplicate rows
df = df.drop_duplicates()  # remove them
```

---

# 7. Unrealistic values (outliers)
Check that numbers make sense. A tenure of 999 months or a negative charge is wrong. Use `.describe()` to see the min and max, then decide to remove or cap them.

**Why:** crazy values pull the model in the wrong direction.

---

# Quick summary
- Fix wrong **types** first (`to_numeric(..., errors="coerce")`).
- Find missing with `df.isna().sum()`.
- Fill numbers with **median**, text with **mode**.
- Remove **duplicates**. Check for **unrealistic** values with `.describe()`.

# Now do this
Open `practice.ipynb`, clean the real Telco data, and do the assignment.
