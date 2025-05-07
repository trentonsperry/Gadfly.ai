RedEcho v1 - Official Release

This model was trained on a curated dataset of 75 labeled statements, combining:
- Direct violent or extremist language
- Coded and suggestive political rhetoric
- Benign but politically adjacent content

Features:
- TF-IDF vectorization
- Presence of ALL-CAPS words
- Use of "they/us/them" pronouns
- Exclamation detection
- Logistic Regression model with balanced class weighting

Contents:
- RedEcho_model_v1.pkl (LogisticRegression model)
- RedEcho_vectorizer_v1.pkl (TF-IDF vectorizer)
- LICENSE (non-commercial attribution license)
