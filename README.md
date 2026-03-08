# 📈 US Zero-Coupon Yield Curve Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn%20%7C%20Statsmodels-orange)
![Finance](https://img.shields.io/badge/Domain-Quantitative%20Finance-success)
![Data](https://img.shields.io/badge/Data%20APIs-FRED%20%7C%20YFinance-lightgrey)

## 📌 Project Description
This repository contains a final Machine Learning project aimed at predicting specific points on the US Sovereign Zero-Coupon Yield Curve (targets: ZC_1Y, ZC_5Y, ZC_10Y). The primary objective is to evaluate whether a data-driven Machine Learning approach, leveraging macroeconomic indicators and market variables, can provide a robust and interpretable alternative to traditional parametric interest rate models.

## 🌍 Project Overview & Financial Context
The yield curve is a fundamental economic indicator that synthesizes market expectations regarding future economic growth, inflation, and monetary policy. 

Traditionally, quantitative finance relies on parametric interest rate models (such as the 1-factor or 2-factor Hull-White models) to reconstruct and simulate the yield curve. However, these models are often computationally expensive to calibrate and highly sensitive to their underlying mathematical assumptions.

**This project adopts a purely data-driven approach:**
* **Macro-Financial & Market Features:** The models are trained on a comprehensive set of features, including monetary policy (FEDFUNDS, 10Y-2Y Spread), inflation expectations (T5YIE, T10YIE), market volatility (VIX), credit/liquidity stress (BAA10Y, TEDRATE), real economic activity (CPI, GDP), and international benchmarks.
* **Automated Data Pipeline:** A robust data engineering pipeline was built to fetch live data directly via the **FRED API** and **Yahoo Finance (`yfinance`)**. 
* **Time Series Alignment:** The dataset spans from 2000 to 2022 (approx. 4,700 daily observations). The pipeline handles complex temporal alignments, converting all series to business days, managing missing values via forward-filling (`ffill`), and properly strictly splitting the dataset chronologically (80% train / 20% test) to prevent data leakage.
* **Modeling:** The project explores multiple baseline and advanced models, including OLS Linear Regression and time-series specific approaches like ARIMA (p, d, q), evaluating them on their predictive $R^2$ and RMSE.

## 👨‍🏫 Teaching & Supervision
This project was carried out as part of the Master 2 Machine Learning & Finance curriculum. 

The course and project supervision were conducted by:
**[Sitraka Matthieu FORLER](https://www.linkedin.com/in/sitraka-matthieu-forler/)**

## 👥 Project Team
This quantitative research and modeling project was realized by:
* **[Jean-Baptiste Attié](https://github.com/JibeyJB)** | [LinkedIn](https://www.linkedin.com/in/jean-baptiste-atti%C3%A9-5273a6254/)  
* **[Yahya Kali](#)** *(Add actual link if available)*
* **[Vincent Karakoseian](#)**  | [LinkedIn](https://www.linkedin.com/in/vincent-ha%C3%AFk-karakoseian-/)  
---
*Note: This repository is intended for academic and research purposes. The models and forecasts provided do not constitute financial advice.*
