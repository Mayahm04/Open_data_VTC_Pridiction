# Open Data Analysis and Predictive Modeling

Ce dépôt contient un notebook Jupyter (`Open_data.ipynb`) développé sous Google Colab pour analyser et modéliser des données de trajets (train.csv, test.csv). L'objectif est de prédire le tarif (`trip_fee`) à l'aide de différentes méthodes de machine learning, réaliser des segmentations clients, calculer des KPI pour les conducteurs et visualiser des données géographiques.

## Table des matières

* [Fonctionnalités](#fonctionnalités)
* [Structure du projet](#structure-du-projet)
* [Prérequis](#prérequis)
* [Installation](#installation)
* [Données](#données)
* [Utilisation](#utilisation)
* [Exploration des données (EDA)](#exploration-des-données-eda)
* [Feature Engineering](#feature-engineering)
* [Modèles de prédiction](#modèles-de-prédiction)
* [Évaluation des modèles](#évaluation-des-modèles)
* [Génération de la soumission](#génération-de-la-soumission)
* [Segmentation Clients](#segmentation-clients)
* [KPI Conducteurs](#kpi-conducteurs)
* [Visualisation Géographique](#visualisation-géographique)
* [Licence](#licence)

## Fonctionnalités

* **Exploration des données** : statistiques descriptives, détection et suppression d’outliers, carte de corrélation.
* **Feature engineering** : conversion des dates, calcul de la durée, extraction du jour de la semaine et de l’heure.
* **Modélisation** : Linear Regression, XGBoost (avec GridSearchCV), SVR, Ridge, Bayesian Ridge, Random Forest.
* **Segmentation** : diagrammes circulaires, histogrammes et bar charts pour répartir les villes et horaires.
* **KPI Conducteurs** : taux d’acceptation, distance et durée moyennes, note moyenne, score global combiné.
* **Cartographie** : heatmap et markers via Folium pour visualiser les trajets et motifs d’annulation.

## Structure du projet

```
├── data/
│   ├── train.csv
│   ├── test.csv
│   └── sample_submission.csv
├── Open_data.ipynb       # Notebook principal
└── README.md            # Ce fichier
```

## Prérequis

* Python 3.8+
* Librairies Python :

  * pandas
  * numpy
  * matplotlib
  * seaborn
  * scikit-learn
  * xgboost
  * folium
  * plotly (optionnel)

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost folium plotly
```

## Données

Placez `train.csv`, `test.csv` et `sample_submission.csv` dans le dossier `data/`. Les fichiers contiennent :

* **train.csv** : données d’entraînement avec `trip_fee` à prédire.
* **test.csv** : données de test (sans `trip_fee`).
* **sample\_submission.csv** : format attendu pour la soumission.

## Utilisation

1. Ouvrir `Open_data.ipynb` dans Google Colab ou Jupyter.
2. Adapter les chemins vers les fichiers dans la cellule de chargement.
3. Exécuter les cellules dans l’ordre pour :

   * Charger et nettoyer les données
   * Réaliser l’EDA et le feature engineering
   * Entraîner les modèles
   * Évaluer les performances (RMSE)
   * Générer et exporter la soumission (`.csv`)
   * Effectuer segmentation, calcul de KPI et visualisations géographiques

## Exploration des données (EDA)

* Chargement du DataFrame et affichage des premières lignes.
* Bilan des valeurs manquantes.
* Boxplots et détection d’outliers (IQR).
* Heatmap de la matrice de corrélation.

## Feature Engineering

* Conversion des colonnes dates (`accepted_date`, `trip_finished_date`).
* Calcul de la durée de trajet, extraction du jour de la semaine et de l’heure.
* Encodage des variables catégorielles (`pickup_city`, `destination_city`, etc.).
* Winsorization pour la variable `trip_distance`.

## Modèles de prédiction

1. **Linear Regression**
2. **XGBoost** (avec recherche d’hyperparamètres via GridSearchCV)
3. **Support Vector Regression (SVR)**
4. **Ridge et Lasso Regression**
5. **Bayesian Ridge**
6. **Random Forest Regressor**

Les modèles sont évalués en RMSE sur un split train/test (test\_size=0.33).

## Évaluation des modèles

Affichage de la **Root Mean Squared Error (RMSE)** pour chaque modèle.

## Génération de la soumission

* Prédiction sur `test.csv`.
* Création du fichier `submission.csv` conformément à `sample_submission.csv`.

## Segmentation Clients

* Diagramme circulaire des villes de prise en charge.
* Histogramme des heures de demande.
* Bar chart des jours de la semaine.
* Analyse des notes des clients.

## KPI Conducteurs

* Taux d’acceptation (`accepted_date` vs `id`).
* Distance et durée moyennes des trajets terminés.
* Note moyenne des conducteurs.
* Normalisation des KPI et calcul d’un **score combiné**.
* Classement des conducteurs selon le score global.

## Visualisation Géographique

* Heatmap des zones de prise en charge.
* Markers Folium pour les motifs d’annulation (passagers et conducteurs).

## Licence

Ce projet est distribué sous la licence MIT. Vous êtes libre d’utiliser, modifier et redistribuer le code.
