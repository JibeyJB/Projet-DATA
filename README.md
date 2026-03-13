# Prediction du taux zero-coupon US a 1 an par Machine Learning

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![ML](https://img.shields.io/badge/ML-Scikit--Learn%20%7C%20Statsmodels%20%7C%20pmdarima-orange)
![Finance](https://img.shields.io/badge/Domaine-Finance%20Quantitative-success)
![Data](https://img.shields.io/badge/APIs-FRED%20%7C%20YFinance-lightgrey)

## Description

Projet de Master 2 (Machine Learning & Finance) visant a predire le **taux zero-coupon souverain americain a 1 an (ZC_1Y)** a l'aide de methodes de machine learning, en alternative aux modeles parametriques traditionnels (Hull-White, Nelson-Siegel).

L'approche est **purement data-driven** : un ensemble de variables macroeconomiques, financieres et internationales est utilise pour entrainer et comparer plusieurs modeles predictifs.

## Contexte financier

La courbe des taux zero-coupon est un indicateur fondamental qui synthetise les anticipations du marche en matiere de croissance, d'inflation et de politique monetaire. Les modeles parametriques classiques (Hull-White 1/2 facteurs) sont couteux a calibrer et sensibles aux hypotheses mathematiques. Ce projet explore une approche alternative par machine learning.

## Donnees

- **Sources** : API FRED (Federal Reserve Economic Data) et Yahoo Finance (`yfinance`)
- **Periode** : 2000 - 2022 (~4 700 observations en jours ouvres)
- **Pipeline** : collecte automatisee, alignement temporel en jours ouvres, forward-fill des valeurs manquantes, decoupage chronologique train/test

**Variables explicatives** :

| Categorie | Variables |
|-----------|-----------|
| Politique monetaire | Fed Funds Rate, Spread 10Y-2Y |
| Anticipations d'inflation | Breakevens 5Y, 10Y |
| Risque et stress | VIX, Spread BAA, TED Spread |
| Activite economique | CPI, GDP |
| International | Taux UK, Japon, Chine |
| Marche | S&P 500, Or |

## Modeles et resultats

Trois approches sont comparees, evaluees sur des periodes normale (2017-2020) et de stress COVID (2020-2022) :

| Modele | Approche | Resultat cle |
|--------|----------|--------------|
| **OLS (niveaux)** | Regression lineaire sur variables brutes | R² = 0.88 — trompeur (regression fallacieuse due a la non-stationnarite) |
| **ARIMA** | Serie temporelle univariee (lags de ZC_1Y uniquement) | RMSE 10x superieur a l'OLS — confirme l'apport des variables exogenes |
| **LASSO (variations)** | Regression regularisee L1 sur donnees differenciees | Meilleur compromis : selection de features, robustesse au stress COVID |

**Metriques business** (strategie directionnelle) :
- Directional Accuracy > 55% (superieur au hasard)
- PnL simule positif sur toutes les periodes
- Sharpe Ratio dans la fourchette 1-2

## Structure du repertoire

```
Projet-DATA/
├── Projet_DATA.ipynb     # Notebook principal (pipeline complet)
├── README.md             # Ce fichier
└── Cahier des charges.docx  # Specifications du projet
```

## Execution

Le notebook est concu pour **Google Colab** :

1. Ouvrir le notebook dans Colab : [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JibeyJB/Projet-DATA/blob/main/Projet_DATA.ipynb)
2. Configurer la cle API FRED dans les secrets Colab (`FRED_API_KEY`)
   - Creer un compte gratuit sur [FRED](https://fred.stlouisfed.org/) pour obtenir une cle API
3. Executer les cellules sequentiellement

## Encadrement

Projet realise dans le cadre du Master 2 Machine Learning & Finance, sous la supervision de :

**[Sitraka Matthieu Forler](https://www.linkedin.com/in/sitraka-matthieu-forler/)**

## Equipe

| Membre | GitHub | LinkedIn |
|--------|--------|----------|
| Jean-Baptiste Attie | [@JibeyJB](https://github.com/JibeyJB) | [LinkedIn](https://www.linkedin.com/in/jean-baptiste-atti%C3%A9-5273a6254/) |
| Yahya Kali | | |
| Vincent Karakoseian | | [LinkedIn](https://www.linkedin.com/in/vincent-ha%C3%AFk-karakoseian-/) |
