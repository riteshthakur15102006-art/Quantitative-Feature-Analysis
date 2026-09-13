# Quantitative Feature Analysis on High-Frequency Time Series

## Overview
This repository contains a statistical exploratory data analysis (EDA) pipeline designed for high-frequency (1-second interval) algorithmic trading data. The objective is to evaluate 437 masked, multi-scale features for stationarity, collinearity, and predictive distribution before feeding them into a zero-lookahead vectorized backtesting engine.

## Statistical Methodologies Applied
* **Stationarity Testing:** Applied Augmented Dickey-Fuller (ADF) tests to identify mean-reverting vs. persistent regimes. Short-lookback features heavily rejected the unit root hypothesis ($p < 0.001$), while longer horizons exhibited increasing persistence.
* **Feature Orthogonality:** Computed Pearson correlation matrices to identify severe multi-horizon collinearity ($r > 0.85$), proving the necessity of PCA or hierarchical clustering prior to alpha weighting.
* **Target Labeling & Leptokurtosis:** Modeled 5-observation forward log returns ($r_{t, t+5} = \ln(P_{t+5} / P_t)$). The empirical distribution exhibited an excess kurtosis of $+2.30$, confirming fat-tailed market microstructure that standard Gaussian models would underestimate.

## Technologies Used
* `pandas` & `numpy` for vectorized time-series manipulation
* `statsmodels.tsa.stattools` for unit root testing
* `seaborn` & `matplotlib` for correlation heatmaps and distribution benchmarking
