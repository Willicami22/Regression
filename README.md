### Escuela Colombiana de Ingeniería Julio Garavito  
### William Camilo Hernandez Deaza  
### Transformación Digital y Soluciones Empresariales - TDSE-2  

# Stellar Luminosity Regression
## Linear and Polynomial Models Implemented from First Principles

---

# Introduction

Regression is a technique for modeling and analyzing the relationship between variables, especially when predicting a numerical value from other data. This repository demonstrates the implementation and operation of:

- Linear Regression
- Polynomial Regression

Everything was developed **from first principles**, without using Machine Learning libraries such as scikit-learn, TensorFlow, or similar. The following were implemented manually:

- Hypothesis function
- Cost function (MSE)
- Gradient derivation
- Gradient Descent algorithm
- Cost surface visualization
- Convergence experiments

The modeled problem corresponds to a simplified version of the behavior of **stellar luminosity** as a function of mass and temperature.

---

# Repository Structure

```
/
├── README.md
├── 01_part1_linreg_1feature.ipynb
└── 02_part2_polyreg.ipynb
```

---

# Dataset Used

## Part I (One variable)

- Stellar mass (M)
- Luminosity (L)

```
M = [0.6, 0.8, 1.0, 1.2, 1.4, 1.6, 1.8, 2.0, 2.2, 2.4]
L = [0.15, 0.35, 1.00, 2.30, 4.10, 7.00, 11.2, 17.5, 25.0, 35.0]
```

---

## Part II (Two variables)

- Stellar mass (M)
- Temperature (T)
- Luminosity (L)

```
M = [0.6, 0.8, 1.0, 1.2, 1.4, 1.6, 1.8, 2.0, 2.2, 2.4]
T = [3800, 4400, 5800, 6400, 6900, 7400, 7900, 8300, 8800, 9200]
L = [0.15, 0.35, 1.00, 2.30, 4.10, 7.00, 11.2, 17.5, 25.0, 35.0]
```

---

# 01_part1_linreg_1feature.ipynb

## Linear Regression

Stellar luminosity is modeled as a linear function of mass:

```
 L̂= wM + b
```

Where:
- M: stellar mass
- L̂: predicted luminosity
- w: slope
- b: bias (intercept)

---

## Implementation

### Dataset Visualization

M vs L was plotted to analyze the relationship and evaluate whether the behavior can be linearly approximated. An increasing trend is observed, although not perfectly linear.

---

### Cost Function (MSE)

The Mean Squared Error was implemented:

```
J(w,b) = (1/n) Σ (Lᵢ − L̂ᵢ)²
```

This function measures the average squared error between actual and predicted values. The minimum of this function represents the best parameter combination.

---

### Cost Surface

J(w,b) was evaluated over a grid of values and plotted:

- 3D surface / Contour plot

The surface has a convex shape, which guarantees a single global minimum.

---

### Gradients

Analytical derivatives were computed:

- ∂J/∂w
- ∂J/∂b

And implemented manually.

---

### Gradient Descent

Two versions were implemented:

- Non-vectorized (with explicit loops)
- Vectorized (using NumPy)

Parameters were updated via:

```
w := w − α ∂J/∂w
b := b − α ∂J/∂b
```

Multiple learning rates were tested to analyze stability and convergence.

---

### Convergence

The following was plotted:

- Loss vs Iterations

The following were analyzed:

- Convergence speed
- Stability
- Behavior under different learning rates

---

### Physical Interpretation

The parameter w represents how much luminosity increases when mass increases by one unit. However, in real astrophysics:

```
L ∝ M³ or M⁴
```

Therefore, a linear model is a limited approximation and presents systematic errors for high masses. This motivates the use of polynomial regression.

---

# 02_part2_polyreg.ipynb

## Polynomial Regression with Interactions

Model:

```
L̂ = Xw + b
```

Where the design matrix X contains:

- M
- T
- M²
- M*T

A column of ones is not included (bias is handled separately).

---

## Implementation

### Visualization

L vs M was plotted encoding temperature using color.

---

### Feature Engineering

The matrix X was constructed using NumPy vectorization.

---

### Cost Function and Gradients

Fully vectorized MSE was implemented, including gradients with respect to:

- w
- b

---

### Training

Gradient Descent was applied and plotted:

- Loss vs Iterations

---

### Feature Selection Experiment

Three models were compared:

```
M1: [M, T]
M2: [M, T, M²]
M3: [M, T, M², M*T]
```

For each model, the following was reported:

- Final loss
- Learned parameters
- Predicted vs actual plot

This allowed analyzing the impact of non-linearity and interaction.

---

### Interaction Analysis

For the complete model (M3):

Only the interaction coefficient (w_MT) was varied while keeping other parameters fixed. The following was plotted:

- Cost vs w_MT

This allowed evaluating the real importance of the interaction term in error reduction.

---

### Inference

A prediction was made for:

```
M = 1.3
T = 6600
```

The reasonableness of the obtained value was analyzed with respect to the original data.

---

# AWS SageMaker Execution Evidence

## Execution Process

1. AWS SageMaker Studio was accessed.
2. A Notebook environment was created.
3. Both .ipynb files were uploaded.
4. All cells were executed without errors.
5. Correct visualization of graphs was verified.

---

## Included Evidence

This repository contains screenshots showing:

- Both notebooks open in SageMaker.
- Complete execution of cells.
- Graph rendering.
- Numerical results obtained.

---

## Local vs SageMaker Execution Comparison

- No differences were observed in numerical results.
- The SageMaker environment facilitates reproducibility and execution on cloud infrastructure.
- Cloud execution reinforces the business approach of the course, where models are part of scalable architectural capabilities.

---

# Conclusion

This project demonstrates:

- Complete implementation of regression from first principles.
- Mathematical understanding of cost functions and gradients.
- Application of numerical optimization through Gradient Descent.
- Importance of feature engineering.
- Analysis of interaction between variables.
- Execution in cloud environment (AWS SageMaker).

From a Digital Transformation perspective, this exercise demonstrates how analytical intelligence can be built, validated, and operated as an architectural capability within modern enterprise systems.