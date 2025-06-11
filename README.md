# 📡 EDFA Power Profile Prediction using Deep Neural Networks

This project explores the use of deep learning models to predict the output power profile of an Erbium-Doped Fiber Amplifier (EDFA) based on its input spectrum across 84 WDM channels. The goal is to estimate the complex transfer function of the EDFA and assess how input sampling strategies affect prediction accuracy and model complexity.

---

## 📁 Dataset

- **Source**: TUD, December 2020  
- **Samples**: 16,497 input-output power profiles  
- **Channels**: 84 (WDM)  
- **Gain Settings**: Input power ∈ [−9, 9] dBm  
- **Target**: Predict full output power profile given sampled input profile  

---

## 🚀 Objectives

- Build a **MIMO regression model** using a deep neural network  
- Compare performance across different input sampling rates:
  - Every 1st, 2nd, 5th, 10th, ... channel  
- Evaluate **accuracy vs. model complexity** trade-offs  
- Apply **XAI techniques** to understand feature importance  

---

## 🛠️ Tools & Libraries

- `Python` (3.9+)  
- `TensorFlow` / `Keras`  
- `NumPy`, `pandas`, `matplotlib`
- `scikit-learn` (metrics & preprocessing)  
- `SHAP` (for Explainable AI)

---

## 📊 Model Architecture

- Fully connected sequential neural network  
- Tunable depth and width  
- Output layer: 84 nodes (regression for each output channel)  
- Loss: Mean Squared Error (MSE)  
- Optimizer: Adam
- Hyperparameters Optimization over:
  - Activation functions = ['relu', 'tanh', 'sigmoid', 'linear']
  - Neurons = [16, 32, 64, 128]
  - Layers = [1, 2, 3]


---

## 📈 Results Summary

| Sampling | Input Dim | RMSE (↓) | Best H-Pars | Notes |
|----------|-----------|----------|--------------|-------|
| Every 1st channel | 84 | 0.042 | relu - 128 - 2 | Best accuracy |
| Every 5th channel | 17 | 0.048 | relu - 128 - 2 | Good trade-off |
| Every 10th channel | 9 | 0.078 | relu - 128 - 3 | Lower accuracy, fast |

---

## 🧠 Explainable AI (XAI)

Applied **SHAP** to estimate feature importance across different input sampling strategies.  
Insights:
- Central wavelength channels contributed most to accurate predictions.
- Redundant edge channels can be skipped in lightweight models.


---

## 👨‍💻 Author

**Alberto Ceresoli**  
MSc Telecommunication Engineering – Politecnico di Milano  
[LinkedIn](https://www.linkedin.com/in/alberto-ceresoli-1a9508266) 

---

## 📜 License

This project is for academic and research purposes only. Please contact the author before reuse in commercial contexts.
