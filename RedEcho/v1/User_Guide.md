# RedEcho v1 – User Guide

This document explains how to use RedEcho v1, a machine learning model built to classify dangerous or extremist political rhetoric.

---

## 🛠 Prerequisites

Before starting, make sure you have:

- Google Colab or Jupyter Notebook access
- Python 3.8+
- The following files from [`RedEcho/v1`](./):
  - `RedEcho_model_v1.pkl`
  - `RedEcho_vectorizer_v1.pkl`

---

## ✅ Step-by-Step Instructions

### 1. Set Up Your Environment

```python
!pip install pandas scikit-learn joblib scipy
```

---

### 2. Load the Model and Vectorizer

```python
import pandas as pd
import joblib
from scipy.sparse import hstack
from sklearn.feature_extraction.text import TfidfVectorizer

model = joblib.load("RedEcho_model_v1.pkl")
vectorizer = joblib.load("RedEcho_vectorizer_v1.pkl")
```

---

### 3. Prepare Your Input CSV

Make a file with one column called `Matched Text`, like so:

```csv
Matched Text
they're coming for your rights, we must act fast!
join us for gardening workshop this Sunday
traitors will hang if justice is to be served
```

Then read it in:

```python
df = pd.read_csv("your_input_file.csv")
```

---

### 4. Apply Feature Engineering

```python
df['Has Exclamation'] = df['Matched Text'].str.contains("!", regex=False)
df['Has All-Caps Word'] = df['Matched Text'].apply(lambda x: any(w.isupper() and len(w) > 1 for w in x.split()))
df['Has They/Us Pronouns'] = df['Matched Text'].str.contains(r'\b(they|us|them)\b', case=False, regex=True)
```

---

### 5. Vectorize and Combine Features

```python
X_text = vectorizer.transform(df['Matched Text'])
X_features = df[['Has Exclamation', 'Has All-Caps Word', 'Has They/Us Pronouns']].astype(int)
X_input = hstack([X_text, X_features])
```

---

### 6. Make Predictions

```python
df['Prediction'] = model.predict(X_input)
df[['Matched Text', 'Prediction']]
```

---

### 7. Export Your Results

```python
df.to_csv("RedEcho_classified_output.csv", index=False)
```

---

## 📌 Output Definitions

| Label      | Meaning |
|------------|---------|
| `dangerous` | Suggests violent, extremist, or coded incitement language |
| `benign`    | Neutral, civil, or non-threatening discourse |

---

© 2025 The Greeley Gadfly • For non-commercial, public-interest use only.
