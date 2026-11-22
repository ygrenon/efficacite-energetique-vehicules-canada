# Efficacité énergétique des véhicules au Canada (2015–2024)

**Projet en science des données - SCI 1402**  
**Université TÉLUQ**  

## 1. Présentation du projet

Ce projet porte sur l'analyse de l'efficacité énergétique des véhicules automobiles au Canada, à partir des données officielles de Ressources naturelles Canada (RNCan) couvrant les années modèles 2015 à 2024.

L'objectif est d'étudier les relations entre les caractéristiques techniques des véhicules et leur consommation de carburant, puis de développer un modèle prédictif permettant d'estimer leur consommation combinée, exprimée en litres par 100 kilomètres (L/100 km).

Le projet combine l'exploration statistique, la préparation des données, l'apprentissage automatique et l'évaluation chronologique des performances prédictives.

## 2. Source et description des données

**Source principale :** Ressources naturelles Canada (RNCan) - Cotes de consommation de carburant.

Le jeu de données utilisé comprend :

  - **10 060 observations**
  - **15 variables**
  - **10 années modèles : 2015 à 2024**

Les observations correspondent à des configurations de véhicules et non à des volumes de ventes.

Les variables étudiées comprennent notamment l'année modèle, la marque, le modèle, la catégorie de véhicule, la cylindrée, le nombre de cylindres, la transmission, le type de carburant, la consommation de carburant et les émissions de CO₂.

## 3. Objectifs

Les principaux objectifs du projet sont :

  1. Explorer et préparer les données de consommation de carburant.
  2. Étudier les relations entre les caractéristiques techniques et la consommation combinée.
  3. Développer et comparer plusieurs modèles prédictifs.
  4. Évaluer la capacité de généralisation du modèle retenu à des années plus récentes.
  5. Analyser les erreurs de prédiction et les limites du modèle.
  6. Produire des tableaux et des figures permettant de communiquer les résultats.

## 4. Méthodologie

### Préparation et exploration

Les données sont importées, inspectées et préparées à l'aide de Python et de la bibliothèque pandas.

Les principales opérations comprennent la vérification des valeurs manquantes, des doublons et des incohérences, ainsi que la normalisation des catégories de véhicules.

Des analyses descriptives et des visualisations permettent ensuite d'examiner les distributions et les relations entre les variables.

### Modélisation prédictive

La variable cible est la consommation combinée de carburant (L/100 km).

Six variables explicatives sont retenues :

  - Année modèle
  - Cylindrée
  - Nombre de cylindres
  - Catégorie de véhicule
  - Transmission
  - Type de carburant

Trois approches sont comparées :

  - Modèle naïf de référence (*Dummy Regressor*)
  - Régression linéaire
  - Forêt aléatoire (*Random Forest Regressor*)

Le **modèle Forêt aléatoire (Random Forest)** est retenu pour les analyses approfondies.

### Validation chronologique

Les données des années 2015 à 2022 sont utilisées pour l'entraînement, tandis que les observations de 2023 et 2024 servent à l'évaluation finale.

Une validation chronologique progressive est également réalisée afin d'examiner la stabilité des performances dans le temps.

Les principaux indicateurs utilisés sont :

  - MAE : Erreur absolue moyenne
  - RMSE : Racine de l'erreur quadratique moyenne
  - R² : Coefficient de détermination

## 5. Principaux résultats

Sur le jeu de test 2023–2024, le modèle Random Forest obtient les performances suivantes :

| Indicateur | Résultat |
|---|---:|
| MAE | 0,610 L/100 km |
| RMSE | 0,910 L/100 km |
| R² | 0,897 |

La comparaison des modèles montre une réduction de la MAE d'environ 36,4 % par rapport à la régression linéaire et de 72,6 % par rapport au modèle naïf.

L'évaluation annuelle révèle toutefois une diminution de la précision en 2024 :

| Année | MAE (L/100 km) |
|---|---:|
| 2023 | 0,553 |
| 2024 | 0,676 |

Les analyses complémentaires indiquent que cette augmentation de l'erreur provient principalement d'une hausse des erreurs à l'intérieur des catégories de véhicules, plutôt que d'une modification de leur répartition.

L'analyse de l'importance des variables par permutation montre également que la cylindrée joue un rôle prépondérant dans la précision du modèle.

## 6. Organisation du dépôt

Le projet est organisé en trois notebooks :

  - **[Notebook 01 - Importation, exploration et modélisation initiale](notebooks/01_importation_inspection.ipynb)**  
  Importation, inspection, préparation et exploration des données, analyse des corrélations et construction des premiers modèles prédictifs.

  - **[Notebook 02 - Modélisation et validation approfondie](notebooks/02_modelisation_validation.ipynb)**  
  Analyse des résidus, étude des erreurs de prédiction et validation chronologique des performances du modèle.

  - **[Notebook 03 - Analyses complémentaires et finalisation](notebooks/03_analyses_complementaires.ipynb)**  
  Décomposition des variations de performance, analyses complémentaires, consolidation des résultats et production des fichiers définitifs.

Les dossiers complémentaires contiennent :

  - **[figures/](figures/)** : Cinq graphiques définitifs produits par la manipulation M029.

  - **[resultats/](resultats/)** : Quatre tableaux CSV produits par la manipulation M030.

## 7. Environnement technique

Les analyses sont réalisées en Python dans Google Colab.

Les principales bibliothèques utilisées sont :

  - pandas
  - NumPy
  - Matplotlib
  - scikit-learn

Les notebooks contiennent les cellules de code et les explications nécessaires pour suivre les différentes étapes du projet.

## 8. Reproduction des analyses

Les trois notebooks sont conçus pour être exécutés indépendamment dans Google Colab.

Pour reproduire les analyses :

  1. Télécharger le notebook souhaité depuis ce dépôt GitHub.
  2. Ouvrir le fichier `.ipynb` dans Google Colab.
  3. Exécuter les cellules dans l'ordre, à partir du début du notebook.

Les données officielles de Ressources naturelles Canada (RNCan), couvrant les années modèles 2015 à 2024, sont téléchargées automatiquement lors de l'initialisation si le fichier CSV est absent de l'environnement d'exécution.

Le fichier source est enregistré dans le répertoire `/content/data/raw/` et lu avec l'encodage `cp1252`.

Les dépendances Python sont documentées dans le fichier `requirements.txt` à la racine du dépôt.

Le troisième notebook permet notamment de reconstruire le modèle prédictif et de générer les tableaux CSV et les figures définitives du projet.

La reproduction des résultats suppose que la source officielle RNCan demeure accessible et que le fichier téléchargé correspond à celui utilisé lors du développement. Des différences de versions des bibliothèques pourraient également influencer certains résultats.

## 9. Limites du projet

Les observations correspondent aux configurations de véhicules présentes dans les données de RNCan. Elles ne permettent donc pas de déduire directement la consommation moyenne du parc automobile canadien ni celle des véhicules effectivement vendus.

Les résultats prédictifs dépendent des variables explicatives, du jeu de données et du protocole de validation.

Les relations statistiques observées ne constituent pas des démonstrations de causalité.

## 10. Références

**Ressources naturelles Canada (RNCan).** Cotes de consommation de carburant des véhicules, années modèles 2015 à 2024. Gouvernement du Canada.

**Université TÉLUQ.** SCI 1402 - Projet en science des données.

---

*Projet réalisé dans le cadre du cours SCI 1402 - Projet en science des données, Université TÉLUQ.*
