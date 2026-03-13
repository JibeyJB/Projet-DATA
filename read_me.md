# Prédiction du taux zéro-coupon US à 1 an par Machine Learning
GITHUB
https://github.com/JibeyJB/Projet-DATA/edit/main/
COLLAB: https://colab.research.google.com/github/JibeyJB/Projet-DATA/blob/main/scripts.ipynb

## Description

Projet de Machine Learning & Finance visant à prédire le taux zéro-coupon souverain américain à 1 an (ZC_1Y) à l'aide de méthodes de machine learning, en alternative aux modèles paramétriques traditionnels (Hull-White, Nelson-Siegel).

L'approche est purement data-driven : un ensemble de variables macroéconomiques, financières et internationales est utilisé pour entraîner et comparer plusieurs modèles prédictifs.

## Contexte financier

La courbe des taux zéro-coupon est un indicateur fondamental qui synthétise les anticipations du marché en matière de croissance, d'inflation et de politique monétaire. Les modèles paramétriques classiques (Hull-White 1/2 facteurs) sont coûteux à calibrer et sensibles aux hypothèses mathématiques. Ce projet explore une approche alternative par machine learning.

## Données

* **Sources** : API FRED (Federal Reserve Economic Data) et Yahoo Finance (`yfinance`)
* **Période** : 2003–2022 (~4 700 observations en jours ouvrés)
* **Pipeline** : collecte automatisée, alignement temporel en jours ouvrés, forward-fill des valeurs manquantes, test ADF de stationnarité, différenciation des variables non stationnaires, découpage en périodes normale (2017–2020) et stress Covid (2020–2022)

**Variables explicatives :**

| Catégorie | Variables |
|---|---|
| Politique monétaire | Fed Funds Rate, Spread 10Y-2Y |
| Anticipations d'inflation | Breakevens 5Y, 10Y |
| Risque et stress | VIX, Spread BAA, TED Spread |
| Activité économique | CPI, GDP |
| International | Taux UK, Japon, Chine |
| Marché | S&P 500, Or |

## Modèles et résultats

Trois modèles sont comparés sur des données stationnaires (variables différenciées), évalués sur une période normale (2017–2020) et une période de stress Covid (2020–2022) :

| Modèle | Approche | RMSE Normal | R² Normal | RMSE Stress | R² Stress |
|---|---|---|---|---|---|
| OLS (diff) | Régression linéaire sans contrainte | 0.017 | 0.12 | 0.028 | -0.80 |
| ARIMA | Série temporelle univariée | 0.017 | -0.004 | 0.021 | -0.008 |
| **LASSO** | **Régression régularisée L1** | **0.015** | **0.26** | **0.019** | **0.17** |

Le Lasso est le seul modèle à conserver un R² positif en période de stress.

**Métriques business (stratégie directionnelle sur le Lasso) :**

| Métrique | Période normale | Période stress |
|---|---|---|
| Directional Accuracy | 69% | 61% |
| PnL cumulé | 5.18 pt | 2.60 pt |
| Sharpe ratio | 6.81 | 4.02 |

PnL positif sur toutes les périodes. Sharpe à relativiser (sans coûts de transaction).

## Structure du répertoire

```
Projet-DATA/
├── Projet_DATA.ipynb          # Notebook principal (pipeline complet)
├── README.md                  # Ce fichier
└── Cahier des charges.docx    # Spécifications du projet
```

## Exécution

Le notebook est conçu pour Google Colab :

1. Ouvrir le notebook dans Colab
2. Configurer la clé API FRED dans les secrets Colab (`FRED_API_KEY`)
   * Créer un compte gratuit sur [FRED](https://fred.stlouisfed.org/) pour obtenir une clé API
3. Exécuter les cellules séquentiellement

## Encadrement

Projet réalisé sous la supervision de **Sitraka Matthieu Forler**.

## Équipe

| Membre | GitHub | LinkedIn |
|---|---|---|
| Jean-Baptiste Attié | [@JibeyJB](https://github.com/JibeyJB) | [LinkedIn](https://linkedin.com) |
| Yahya Kali | | |
| Vincent Karakoseian | | [LinkedIn](https://linkedin.com) |
