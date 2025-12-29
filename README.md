# Robust Gas Classification using MQ Sensors

This repository implements a robust multiclass gas classification system using MQ-series gas sensors and machine learning. The project focuses not only on achieving high classification performance, but also on validating the **reliability and robustness** of the model through systematic stress testing.

---

## 📌 Project Overview

Gas classification using low-cost MQ sensors is challenging due to:
- Cross-sensitivity between sensors
- Noise in sensor readings
- High correlation among sensor responses

In this project, we demonstrate that despite these challenges, gas classes can be **cleanly separated** under controlled conditions, and we rigorously validate the model using **ROC-AUC analysis and robustness tests**.

---

## 🧪 Sensors Used

- MQ2  
- MQ3  
- MQ5  
- MQ6  
- MQ7  
- MQ8  
- MQ135  

These sensors exhibit strong inter-correlation and overlapping sensitivity, which the model exploits to achieve high separability between gas classes.

---

## 🎯 Gas Classes

- NoGas  
- Perfume  
- Smoke  
- Mixture  

The task is formulated as a **multiclass classification problem**.

---

## 🧠 Model

- Feedforward Neural Network (PyTorch)
- Softmax output for multiclass probability estimation
- Cross-entropy loss

The model outputs calibrated class probabilities, enabling ROC-based evaluation.

---

## 📊 Evaluation Metrics

Primary metric:
- **ROC-AUC (One-vs-Rest)**

Reported scores:
- **Macro ROC-AUC:** ~0.997  
- **Weighted ROC-AUC:** ~0.997  

These indicate excellent class separability on the test dataset.

---

## 🔍 Robustness & Stress Testing

To ensure that high performance is not due to data leakage or overfitting, multiple stress tests were performed.

### 1️⃣ Noise Injection Test

Gaussian noise was added to sensor readings at increasing levels:

| Noise Level | Macro ROC-AUC |
|------------|---------------|
| 0.00 | 0.9972 |
| 0.05 | 0.9954 |
| 0.10 | 0.9871 |
| 0.20 | 0.9718 |

**Observation:**  
Performance degrades smoothly with increasing noise, indicating robust learning rather than memorization.

---

### 2️⃣ Evaluation Integrity Checks

- Probability-based ROC (not hard labels)
- Correct alignment of labels and predictions
- One-vs-Rest multiclass ROC
- Separate train/test evaluation

These checks confirm that the reported ROC-AUC values are valid and trustworthy.

---

## 📌 Key Insights

- MQ sensor signals are highly correlated, leading to redundant but strong discriminative features.
- Gas classes are cleanly separable under controlled conditions.
- The classification task is **intrinsically easy on this dataset**, which explains near-perfect ROC-AUC.
- Robustness tests confirm that performance is not due to leakage or evaluation bugs.

---

## ⚠️ Limitations

- Dataset collected under controlled conditions
- Does not account for sensor drift, humidity, or long-term aging
- Generalization to real-world environments requires further validation

---

## 🚀 Future Work

- Sensor ablation and feature selection
- Time-based and session-based validation
- Calibration analysis (reliability curves)
- Real-world deployment testing

---

## 🛠️ Tech Stack

- Python
- PyTorch
- NumPy
- scikit-learn
- Matplotlib

---

## 👤 Author

**Kumar Mohit**  
Aspiring AI/ML Engineer & Data Scientist  

---

## 📜 License

This project is released for academic and educational purposes.
