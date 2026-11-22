# Données du projet SCI 1402

## Source des données

Le projet utilise les données officielles de consommation de carburant des véhicules publiées par **Ressources naturelles Canada (RNCan)**.

**Période étudiée :** Années modèles 2015 à 2024.

**Jeu de données :** Cotes de consommation de carburant des véhicules.

**Source officielle :** [Ressources naturelles Canada — Cotes de consommation de carburant](https://ressources-naturelles.canada.ca/energie/efficacite-energetique/transports-energie-efficacite/vehicules-personnels).

## Fichier utilisé

Nom du fichier :

`am2015-2024-cotes-de-consommation-de-carburant.csv`

Caractéristiques du jeu de données :

  - 10 060 observations
  - 15 variables
  - Encodage : `cp1252`
  - Période : 2015 à 2024

Chaque observation correspond à une configuration de véhicule et non à un volume de ventes.

## Utilisation des données

Le fichier CSV constitue la source principale des analyses effectuées dans les trois notebooks du projet.

Pour reproduire les analyses, il faut disposer du fichier CSV correspondant à la période étudiée et le rendre accessible à l'environnement Google Colab.

Les notebooks contiennent le code nécessaire pour importer et traiter ces données.

## Reproductibilité

Les résultats ont été obtenus à partir de la version du jeu de données utilisée pendant la réalisation du projet.

L'utilisation d'une version différente ou actualisée des données pourrait entraîner des différences dans les résultats.
