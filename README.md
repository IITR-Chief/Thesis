# Thesis: Neural Network based Calibration of the Stochastic Volatility Inspired (SVI) Model

This repository contains the implementation of a quantitative framework for modeling and calibrating the **Implied Volatility (IV) Smile** using the **Stochastic Volatility Inspired (SVI)** parameterization. This project was developed as part of a thesis focused on financial derivatives and risk management.

## 📌 Project Overview

The calibration of the volatility surface is essential for option pricing, hedging, and identifying market inefficiencies. This project provides a complete pipeline from raw market data acquisition to the generation of smooth, arbitrage-free volatility smiles.

### Key Features:
* **Real-time Data Integration:** Uses `yfinance` to fetch live options chains.
* **Data Transformation:** Converts market strikes and premiums into Log-Moneyness and Total Variance space.
* **SVI Parameterization:** Implements the Raw SVI model to capture the characteristic "smile" or "skew" of equity options.
* **Grid Interpolation:** Maps discrete market data onto a continuous log-moneyness grid for standardized analysis.

## 🛠️ Technical Stack

* **Language:** Python 3.x
* **Libraries:** * `numpy` & `pandas`: Numerical operations and data structures.
    * `yfinance`: Market data API.
    * `matplotlib`: Technical visualization of volatility surfaces.
    * `scipy`: Optimization for model calibration.

## 📉 Methodology

### 1. The SVI Model
The model fits the total variance $w(k)$ as a function of log-moneyness $k$:
$$w(k) = a + b \left( \rho(k - m) + \sqrt{(k - m)^2 + \sigma^2} \right)$$
Where:
* **a**: General level of variance.
* **b**: Slope of the asymptotes (volatility of volatility).
* **ρ**: Orientation/Skew of the smile.
* **m**: Horizontal displacement (location of the minimum).
* **σ**: Curvature at the vertex.

### 2. Workflow
1.  **Extraction:** Pulling Call/Put data for specific maturities.
2.  **Cleaning:** Filtering out low-liquidity options and calculating Mid-Prices.
3.  **Mapping:** Projecting data into $(k, w)$ space.
4.  **Calibration:** Minimizing the sum of squared errors between market variance and SVI predicted variance.

## 🚀 Getting Started

### Prerequisites
```bash
pip install numpy pandas matplotlib yfinance scipy
