### 📈 Optimization (Model Parameter Optimization)

Optimization is an **internal** process where the model adjusts its own internal weights and biases _during_ training to minimize error.

- **Goal:** To minimize a "Loss Function" (the difference between prediction and reality).    
- **Controlled by:** The optimization algorithm (e.g., Gradient Descent).
- **Timing:** Occurs automatically during the training phase.
- **Examples:** The weights (w) and bias (b) in a linear regression equation (y=wx+b).
- **Analogy:** The car’s computer constantly adjusting the fuel injection and timing while the car is actually on the road to ensure peak efficiency.
### ⚖️ Summary Comparison

| Feature    | Hyperparameter Tuning      | Optimization (Parameters)     |
| ---------- | -------------------------- | ----------------------------- |
| **Level**  | Higher-level configuration | Lower-level internal learning |
| **When?**  | Before training            | During training               |
| **Who?**   | Set by the user            | Learned by the model          |
| **Output** | Optimal model settings     | Optimal model weights         |