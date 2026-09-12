	 
## ⚖️ Model Comparison Table

| Model               | Task Type          | Best Used For...                        | Key Weakness                              |
| ------------------- | ------------------ | --------------------------------------- | ----------------------------------------- |
| **Simple Linear**   | Regression         | One feature vs. One target.             | Too simple for real-world data.           |
| **Multiple Linear** | Regression         | Predicting value based on many factors. | Sensitive to outliers/correlation.        |
| **Polynomial**      | Regression         | Capturing non-linear, curved trends.    | Can overfit wildly at high degrees.       |
| **Logistic**        | **Classification** | Binary outcomes (Yes/No).               | Assumes linear decision boundary.         |
| **Ridge**           | Regression         | Many features with small effects.       | Doesn't eliminate features.               |
| **Lasso**           | Regression         | Sparse data (many useless features).    | Can struggle with highly correlated data. |


| Task Type          | Evaluation Tool      | What it measures                              |
| ------------------ | -------------------- | --------------------------------------------- |
| **Regression**     | **RMSE / R²**        | How far away the predicted number was.        |
| **Classification** | **Confusion Matrix** | How many times the label was right vs. wrong. |

## 📝 Analyst Summary

- If you are predicting **"How much?"** (Price, Temperature) → Use **Linear/Ridge/Lasso**.
- If you are predicting **"Which one?"** (Survived, Spam, Fraud) → Use **Logistic**.
- Like **Titanic project**, Logistic is the baseline because you are predicting a category (1 or 0), and you've already handled the outliers using **Binning**, which makes the model more robust without needing complex regularization.