---
title: "Lesson 1 - What is AI and Machine Learning?"
subtitle: "READ ME FIRST (theory). Then open the practice notebook."
geometry: margin=2cm
fontsize: 12pt
toc: true
---

# Lesson 1 - What is AI and Machine Learning?

This is the **theory**. Read it slowly. There is almost no code in this lesson - it is about the **ideas and words** you must know. Then open `practice.ipynb`.

# Key words in this lesson
| Word | Simple meaning |
| --- | --- |
| AI | making computers do smart things |
| ML | a computer that learns from data |
| DL | ML that uses big "neural networks" |
| label | the correct answer we already know |
| feature | one piece of input information (a column) |
| model | the thing that learns the pattern and predicts |

---

# 1. AI, ML, DL - three circles
- **AI (Artificial Intelligence)** = the big idea: make a computer act smart.
- **ML (Machine Learning)** = a part of AI: the computer learns a pattern from data, instead of us writing every rule.
- **DL (Deep Learning)** = a part of ML: it uses big "neural networks" for hard things like images and speech.

Picture three circles: AI is the biggest, ML is inside AI, DL is inside ML.

**Why it matters:** people mix these words. Now you know AI is the biggest and DL is the smallest.

---

# 2. What does "learn from data" mean?
Old way: a human writes every rule ("if word = 'free' then spam").
ML way: we show the computer many examples **with the answers**, and it finds the pattern by itself.

- **Feature** = an input column (for example: tenure, monthly charge).
- **Label** = the answer we already know (for example: churned = Yes/No).

**Why:** real life has too many rules to write by hand. Learning from examples scales.

---

# 3. The 3 types of Machine Learning
| Type | Do we have labels? | Goal | Example |
| --- | --- | --- | --- |
| **Supervised** | Yes (answers given) | Learn from answers, predict new ones | Past loans labeled "paid"/"not paid" -> predict new loans |
| **Unsupervised** | No | Find groups or structure | Group 1 million customers into similar types |
| **Reinforcement** | No, but there are rewards | Learn by trying + reward/penalty | A program learns a game by getting points |

**Common mistake:** thinking everything is supervised. If there are **no labels**, it is unsupervised.

---

# 4. Two kinds of supervised tasks
- **Regression** = predict a **number** (price, sales, temperature).
- **Classification** = predict a **category** (spam / not spam, churn Yes / No).

**Quick test:** "How much?" -> regression. "Which group?" -> classification.

**Common mistake:** calling churn (Yes/No) a regression. It is a **category**, so it is classification.

---

# 5. The ML workflow (the steps we follow)
1. **Understand the problem** - what do we want, and why?
2. **Get the data.**
3. **Clean and prepare** the data (Modules 2-3).
4. **Train a model** (Module 4).
5. **Check how good it is** (Module 4).
6. **Use it** on new data.

**Why:** if you skip step 1, you can build a perfect model for the **wrong** problem.

---

# 6. A model is never 100% sure
A model gives a **probability**, not a certain answer. A weather model says "80% rain", not "it will rain for sure". The future has uncertainty.

**Why:** this is normal and fine. We measure how often the model is right, and try to improve it.

---

# 7. Fairness and bias (short but important)
If the data is unfair, the model is unfair.
Example: a model trained mostly on data from men may work badly for women. This is called **bias**.

**Why:** we must check who the data represents, so the model is fair to everyone.

---

# Quick summary
- AI > ML > DL (size).
- ML learns from data: **features** (inputs) + **labels** (answers).
- 3 types: **supervised** (labels), **unsupervised** (no labels), **reinforcement** (rewards).
- Supervised tasks: **regression** (number) or **classification** (category).
- Always understand the problem first. Models give probabilities. Watch for bias.

# Now do this
1. Open `practice.ipynb`.
2. Do the scenario exercises (decide the ML type).
3. Run the small Python warm-up so you are ready for Lesson 2.
