# Predictive Modeling & Trading Strategy Optimization (Smarket Case Study)

> Built regression and classification models on S&P 500 daily returns and designed trading strategies using threshold optimization and backtesting to evaluate investment performance.

**Author:** Amisha Farhana Shaik  
**Project Type:** Quantitative Finance Case Study | Predictive Modeling | Strategy Backtesting  

---

## Business Problem

Using the Smarket dataset (1,250 daily S&P 500 returns from 2001–2005), the objectives were:

- Calculate cumulative investment returns.
- Predict daily percentage returns using regression.
- Predict market direction using logistic regression.
- Design rule-based trading strategies.
- Optimize threshold-based investment decisions.
- Identify the most effective strategy under uncertainty.

---

## Dataset Overview

Source: Smarket dataset :contentReference[oaicite:2]{index=2}  

Variables:
- Lag1–Lag5: 1–5 day lagged returns
- Volume: trading volume (billions)
- Today: daily percentage return
- Direction: Up/Down (binary classification)
- Year: calendar year

Train/Test Split:
- Training: 2004 and earlier
- Testing: 2005 :contentReference[oaicite:3]{index=3}

---

# 1️⃣ Total Investment Return

Implemented cumulative return calculation:

Initial Investment: $1,000  
Final Value over full dataset: **$959.53**

Interpretation:
The overall market performance during this period produced a net loss :contentReference[oaicite:4]{index=4}.

---

# 2️⃣ Linear Regression Model (Predicting Today’s Return)

Model:
Today ~ Lag1 + Lag2 + Lag3 + Lag4 + Lag5 + Volume

Results:
- R² ≈ 0.002
- MSE ≈ 0.42
- No statistically significant predictors :contentReference[oaicite:5]{index=5}

Interpretation:
Lagged returns and volume have almost no explanatory power for predicting daily returns.

Polynomial regression worsened performance:
- R² ≈ -0.84
- Higher MSE

Conclusion:
Daily returns are largely unpredictable using simple linear models.

---

# 3️⃣ Logistic Regression (Predicting Positive Return)

Target:
PositiveReturn = 1 if Today > 0

Results:
- Accuracy ≈ 48%
- AUC ≈ 0.52 :contentReference[oaicite:6]{index=6}
- Confusion Matrix:
  - True Negatives: 81
  - False Positives: 30
  - False Negatives: 101
  - True Positives: 40

Interpretation:
The model performs close to random guessing.

Threshold = 0.5 selected using predicted probability distribution visualization :contentReference[oaicite:7]{index=7}.

---

# 4️⃣ Trading Strategy Design

## Strategy A: Invest When Return > 0%

Final Value:
$174,605.77 :contentReference[oaicite:8]{index=8}  

(Note: This assumes perfect foresight of daily returns.)

---

## Strategy B: Invest When Return > y%

Tested thresholds:
- -2%
- -1%
- 0%
- 1%
- 2%

Example (Test Data 2005):
- 0% threshold → $1,943.64
- 1% threshold → $1,188.39
- 2% threshold → $1,000.00 :contentReference[oaicite:9]{index=9}

Insight:
Lower thresholds increase participation but also risk.
Higher thresholds reduce trades and reduce gains.

---

# 5️⃣ Threshold Selection

### Logistic Regression Threshold
- Based on **probability of positive return**
- Example: Predict “Up” if probability ≥ 0.5

### Trading Threshold (y)
- Based on **expected return magnitude**
- Example: Invest only if predicted return > 1%

Key Difference :contentReference[oaicite:10]{index=10}:
- Logistic threshold = model confidence
- Trading threshold = expected return size

They measure different quantities.

---

# 6️⃣ Strategy Improvements

Suggested improvements :contentReference[oaicite:11]{index=11}:

- Adaptive thresholds based on volatility
- Moving average / trend-based filters
- Volatility-adjusted y
- Grid search optimization
- Incorporating macroeconomic variables
- Stop-loss implementation
- Diversification

---

# 7️⃣ Best Strategy Recommendation

Final recommendation:

**Dollar-Cost Averaging (DCA) + Stop-Loss + Diversification**

Why:
- Reduces volatility risk
- Avoids market timing dependence
- Limits downside exposure
- Suitable for uncertain predictive environments

This approach balances participation in gains with controlled risk management :contentReference[oaicite:12]{index=12}.

---

## Technical Skills Demonstrated

- Time-series data splitting
- Cumulative return modeling
- OLS regression diagnostics
- Logistic regression classification
- ROC & threshold tuning
- Confusion matrix interpretation
- Backtesting trading strategies
- Threshold optimization
- Strategy simulation
- Risk-adjusted reasoning
- Financial return compounding
- Quantitative decision modeling

---

## Why This Case Study Matters

This project demonstrates:

- Understanding limits of financial predictability
- Distinguishing explanatory vs predictive modeling
- Translating model outputs into investment decisions
- Evaluating classification vs magnitude thresholds
- Designing systematic trading rules
- Connecting statistical modeling to capital allocation

It reflects practical quantitative finance reasoning rather than purely academic modeling.

---

## Applications

Quantitative Finance | Algorithmic Trading | Strategy Backtesting | Financial Modeling | Time Series Analysis | Risk Management | Investment Analytics
