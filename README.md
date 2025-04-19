# SVM Hyperparameter Optimization Project 🚀



## Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset-)
- [Methodology](#methodology-)
- [Results](#results-)
  - [Optimized Parameters Table](#optimized-parameters-table)
  - [Convergence Graph Analysis](#convergence-graph-analysis)

---

## Project Overview
This project demonstrates automated hyperparameter tuning for **Support Vector Machines (SVM)** on the UCI PenDigits dataset. By systematically optimizing kernel, regularization (`C`), and kernel coefficient (`gamma`) across 10 data splits, we achieve **99.7% accuracy** while identifying robust parameter configurations.

---

## Dataset 📊
**Pen-Based Recognition of Handwritten Digits**
- **Samples**: 10,992  
- **Features**: 16 (x/y coordinates of pen strokes)  
- **Classes**: 10 (digits 0-9)  
- **Split**: 70% training / 30% testing (stratified)  
- **Preprocessing**: Standardized using `StandardScaler`

---

## Methodology ⚙️
### Optimization Pipeline
1. **Stratified Sampling**  
   - 10 unique 70-30 splits (`random_state=0` to `9`)  
   - Preserves class distribution  

2. **Hyperparameter Search**  
   - **Algorithm**: `RandomizedSearchCV` with 30 iterations  
   - **Parameters**:  
     - `kernel`: `['linear', 'rbf']`  
     - `C`: Log-uniform distribution (0.1 to 100)  
     - `gamma`: Log-uniform distribution (0.0001 to 0.1)  
   - **Validation**: 3-fold cross-validation  

3. **Evaluation**  
   - Final testing on held-out 30% data  

---

## Results 📈
### Optimized Parameters Table
| Sample | Accuracy | Kernel |    C   |  Gamma  |
|--------|----------|--------|--------|---------|
| S1     | 0.9967   | rbf    | 5.76   | 0.0787  |
| S2     | 0.9948   | rbf    | 81.05  | 0.0212  |
| S3     | 0.9955   | rbf    | 5.76   | 0.0787  |
| S4     | 0.9970   | rbf    | 5.76   | 0.0787  |
| S5     | 0.9961   | rbf    | 5.76   | 0.0787  |
| S6     | 0.9948   | rbf    | 5.76   | 0.0787  |
| S7     | 0.9970   | rbf    | 5.76   | 0.0787  |
| S8     | 0.9948   | rbf    | 5.76   | 0.0787  |
| S9     | 0.9970   | rbf    | 5.76   | 0.0787  |
| S10    | 0.9964   | rbf    | 5.76   | 0.0787  |





**Key Observations**:
- 🏆 **Peak Accuracy**: **99.70%** achieved in 3/10 samples  
- 🔄 **Parameter Consistency**:  
  - RBF kernel outperformed linear in all cases  
  - Optimal `C ≈ 5.76` and `gamma ≈ 0.0787`  
- ⚡ **Efficiency**: Best parameters found within 15 iterations  

### Convergence Graph Analysis
![Convergence Graph](download.png)
- **Rapid Learning**: 99% accuracy reached by iteration 5  
- **Stabilization**: Marginal gains (<0.2%) after iteration 15  
- **Robustness**: Small variance between iterations  

---





