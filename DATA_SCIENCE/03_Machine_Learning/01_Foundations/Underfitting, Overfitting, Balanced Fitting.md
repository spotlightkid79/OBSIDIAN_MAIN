# ⚖️ Model Fit: Underfitting, Overfitting, and Balanced

When training a model, we aim for a balance between the model's complexity and its ability to generalize to new, unseen data.

## 1. Underfitting (High Bias)

The model is **too simple** to capture the underlying pattern of the data. It performs poorly on both the training set and the test set.

- **Cause:** Using a linear model for non-linear data, or insufficient training time.
- **Analogy:** Trying to describe a complex painting using only two colors.
- **Result:** High training error, high test error.
---
## 2. Overfitting (High Variance)

The model is **too complex** and starts "memorizing" the noise and outliers in the training data rather than the actual pattern.

- **Cause:** Model is too powerful for the amount of data (e.g., using a high-degree polynomial for a simple trend).    
- **Analogy:** Memorizing the answers to a practice exam instead of learning the logic behind the questions.
- **Result:** Very low training error, but very high test error.
---
## 3. Balanced Fitting (The "Sweet Spot")

The model captures the general trend and ignores the noise. It generalizes well to new data.

- **Result:** Low training error and low test error (close to each other).
### 🛠️ How to Fix Them

| Problem          | Symptom          | Solution                                                             |
| ---------------- | ---------------- | -------------------------------------------------------------------- |
| **Underfitting** | High Train Error | Increase model complexity, add features, or train longer.            |
| **Overfitting**  | High Test Error  | Reduce complexity, use **Regularization** (L1/L2), or get more data. |

## 🔗 Related
- [[Bias_Variance_Tradeoff]]
- [[Regularization]]
- [[Cross_Validation]]
- [[Classification Model Evaluation]]