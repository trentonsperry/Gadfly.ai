# Gadfly.ai

**Gadfly.ai** is a public-interest machine learning project developed by *The Greeley Gadfly* to detect dangerous, extremist, or escalating rhetoric in public discourse — particularly from political and conspiratorial sources.

## 🔎 Purpose

This project exists to:
- Monitor patterns of rhetorical escalation
- Provide journalists, researchers, and watchdogs with automated analysis tools
- Learn continuously through supervised training and real-world feedback

---

## 🚨 Current Model: RedEcho v1

The first deployed model, **RedEcho**, is a Logistic Regression classifier trained to distinguish between:

- `dangerous`: speech suggesting violence, rebellion, threats, or coded calls to action
- `benign`: neutral or non-threatening political speech

It uses a combination of:
- TF-IDF text features
- Presence of ALL-CAPS words
- Use of pronouns like *they, them, us*
- Exclamation mark detection

➡️ [RedEcho/v1](./RedEcho/v1) includes:
- The trained model and vectorizer
- Summary notes on training data
- License information

---

## 🛡 License

This repository is available for **non-commercial, public-interest use** only.

See the [LICENSE](./RedEcho/v1/LICENSE) file for more details.  
Attribution is required: **© 2025 The Greeley Gadfly**

---

## 🚧 Coming Soon

- RedEcho v2 with expanded rhetorical understanding
- Active learning feedback loop
- Live monitoring dashboards

