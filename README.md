# Implied-Volatility-Prediction-Using-Boosting-Approaches-

This project focuses on predicting implied volatility (IV) for cryptocurrency options using a combination of sequential feature engineering and machine learning models.

📌 Project Overview

The objective was to improve IV prediction accuracy by integrating lagged features, rolling statistics, and market microstructure indicators with robust ML models. Building on recent research, the strongest results were achieved with CatBoost, LightGBM, and a weighted ensemble of CatBoost, LightGBM, and ExtraTrees.

Best-performing models: CatBoost and Weighted Ensemble

Evaluation metrics: RMSE (optimized), R², sMAPE, MASE, Pearson Correlation

Key insight: Boosting models handled structured, engineered features more effectively than deep time-series models (e.g., TCN/LSTM) while maintaining low latency for real-time deployment.

⚙️ Features & Engineering

A total of 42 engineered features were created to capture:

Order-book imbalance & spreads (e.g., bid-ask volumes, best spreads, depth ratios)

Momentum & technical indicators (RSI, normalized momentum, rolling volume)

Market microstructure dynamics (absolute volume changes, rolling skew/kurtosis)

Lagged returns (mid-price percentage changes over 10s lags)

The most impactful features included:

Mid-price returns

RSI (10s & 30s)

Normalized momentum

Skewness & kurtosis

📊 Results
Model	R²	sMAPE	MASE	Pearson Corr.
LightGBM	0.3974	44.02%	3.74	0.6646
ExtraTrees	0.3300	45.51%	3.93	–
CatBoost	0.3872	44.14%	3.87	0.6667
Weighted Ensemble (CatBoost + LightGBM + ExtraTrees)	0.3974	44.02%	3.74	0.6655
TCN + CatBoost	0.1511	48.51%	4.37	–

✅ CatBoost offered the best balance of accuracy, interpretability, and efficiency, making it suitable for live trading systems.

🚀 Live Trading Considerations

CatBoost & Weighted Ensemble: Best suited for real-time deployment due to low latency and modest computational cost.

Neural time-series models (TCN/LSTM): Strong temporal modeling capacity, but slower, heavier, and riskier under latency constraints.

Trading signal usage:

If Predicted IV > Market IV → asset may be underpriced → potential buy opportunity.

If Predicted IV < Market IV → asset may be overpriced → potential sell opportunity.

📖 References

Lent, 2023 – Machine Learning vs. Traditional IV Models

Leung et al., 2024 – Nonlinear ML for Crypto Options

Zhibo, 2024 – IV Prediction & Backtesting
