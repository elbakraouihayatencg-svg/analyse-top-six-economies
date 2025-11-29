## EL BAKRAOUI Hayat École Nationale de Commerce et de Gestion (ENCG) - 4ème Année
<img src="EL BAKRAOUI Hayat (1).jpg" style="height:164px;margin-right:132px"/>
## appogé d'etudiant:
## Classe:CAC2
  ---
# Rapport d'Analyse Prédictive du PIB (Produit Intérieur Brut)
---
##  Petit descriptif du jeu de donnees

---
Ce jeu de données, a été compilé pour l'analyse des six principales économies mondiales. Il contient 180 entrées et 18 colonnes, couvrant une période allant au moins de 1991 à 2020 . Chaque entrée représente une observation annuelle pour un pays donné parmi ces six économies. Les informations disponibles incluent des indicateurs macroéconomiques et sociaux essentiels tels que le PIB (en dollars courants et en PPA), le PIB par habitant, le taux de croissance du PIB, les importations et exportations de biens et services (% du PIB), la dette publique centrale (% du PIB), les réserves totales, le taux de chômage, l'inflation, les transferts de fonds personnels (% du PIB), la population totale, le taux de croissance démographique, l'espérance de vie à la naissance et le taux de pauvreté (à 1,90 $ par jour en PPA 2011). Ce riche ensemble de données permet une analyse approfondie des tendances économiques et sociales des plus grandes puissances économiques mondiales sur plusieurs décennies.


## Introduction

Ce projet a pour objectif de réaliser une analyse prédictive détaillée du Produit Intérieur Brut (PIB) actuel en dollars américains (`GDP (current US$)`) en utilisant des données historiques sur l'année (`Year`) et le nom du pays (`Country Name`). L'analyse comprendra la préparation des données, l'application de divers modèles de régression (linéaire, polynomiale, Ridge, et arbre de décision), l'évaluation de leurs performances et une comparaison de leurs résultats. Le rapport est rédigé en français.

## Dataset

Le dataset utilisé provient de l'URL suivante : `https://raw.githubusercontent.com/elbakraouihayatencg-svg/analyse-top-six-economies/main/top_six_economies.csv`.

Il contient des données sur les six principales économies mondiales sur plusieurs années, incluant divers indicateurs économiques tels que le PIB, la croissance du PIB, la population, etc.

## Objectifs de l'Analyse

1.  **Préparer les données** pour la modélisation prédictive (sélection des caractéristiques, gestion des valeurs manquantes, encodage des variables catégorielles, division des données).
2.  **Explorer les corrélations** entre les caractéristiques numériques et le PIB.
3.  **Implémenter et évaluer** différents modèles de régression :
    *   Régression Linéaire Simple
    *   Régression Polynomiale
    *   Régression Ridge
    *   Régression par Arbre de Décision
4.  **Justifier la non-pertinence** de la Régression Logistique pour ce problème.
5.  **Comparer les performances** de tous les modèles à l'aide de métriques clés (R², MSE, RMSE).
6.  **Tirer des conclusions** et formuler des recommandations pour des analyses futures.

## Méthodologie

### 1. Préparation des Données

*   Sélection des colonnes pertinentes : 'Year', 'Country Name', et 'GDP (current US$)'.
*   Gestion des valeurs manquantes par suppression des lignes concernées.
*   Encodage `One-Hot` de la variable catégorielle 'Country Name' pour la convertir en format numérique.
*   Division du dataset en ensembles d'entraînement (80%) et de test (20%).

### 2. Analyse de Corrélation

Une matrice de corrélation a été calculée et visualisée pour toutes les caractéristiques numériques du dataset, afin d'identifier les relations et la force de la liaison linéaire avec la variable cible 'GDP (current US$)'.

### 3. Modèles de Régression

#### a. Régression Linéaire Simple

Un modèle de régression linéaire a été entraîné sur les données préparées pour établir une relation linéaire de base entre les prédicteurs et le PIB.

#### b. Régression Polynomiale

Des caractéristiques polynomiales de degré 2 ont été générées pour capturer les relations non linéaires potentielles. Un modèle de régression linéaire a ensuite été entraîné sur ces caractéristiques transformées.

#### c. Régression Ridge

Un modèle de régression Ridge, une forme de régression linéaire régularisée, a été appliqué aux caractéristiques polynomiales pour atténuer le surapprentissage et gérer la multicolinéarité. Un paramètre `alpha` de 1.0 a été utilisé.

#### d. Régression par Arbre de Décision

Un modèle de régression par arbre de décision a été entraîné. Ce modèle est capable de capturer des relations complexes et non linéaires sans nécessiter une transformation explicite des caractéristiques.

### 4. Évaluation des Modèles

Chaque modèle a été évalué à l'aide des métriques suivantes :

*   **R-carré (R²)** : Proportion de la variance de la variable dépendante qui est prévisible à partir des variables indépendantes.
*   **Erreur Quadratique Moyenne (MSE)** : Moyenne des carrés des erreurs (différence entre les prévisions et les valeurs réelles).
*   **Racine Carrée de l'Erreur Quadratique Moyenne (RMSE)** : Racine carrée du MSE, offrant une mesure de l'erreur dans la même unité que la variable cible.

### 5. Non-pertinence de la Régression Logistique

La régression logistique n'est pas adaptée à cette tâche car le 'GDP (current US$)' est une variable cible continue (problème de régression), alors que la régression logistique est conçue pour des problèmes de classification (variable cible catégorielle).

## Résultats et Discussion

Voici un résumé des performances de chaque modèle :

| Modèle                            | R-carré (R²) | MSE                  | RMSE                 |
|:----------------------------------|:-------------|:---------------------|:---------------------|
| Régression Linéaire Simple        | 0.8647       | 4.0912e+24           | 2.0227e+12           |
| Régression Polynomiale (Degré 2)  | 0.9798       | 6.1006e+23           | 7.8107e+11           |
| Régression Ridge (Alpha=1.0)      | 0.8670       | 4.0208e+24           | 2.0052e+12           |
| Régression par Arbre de Décision  | 0.9934       | 2.0100e+23           | 4.4833e+11           |

### Analyse des Modèles

*   **Régression Linéaire Simple** : A servi de baseline. Bien qu'elle explique une part significative de la variance (R² = 0.8647), ses erreurs sont élevées, suggérant une relation non linéaire.
*   **Régression Polynomiale (Degré 2)** : A considérablement amélioré les performances (R² = 0.9798), indiquant que la relation entre les variables est fortement non linéaire. Le PIB ne croît pas de manière linéaire avec le temps et les pays.
*   **Régression Ridge (Alpha=1.0)** : Ses performances sont similaires à celles de la régression linéaire simple, et inférieures à la régression polynomiale non régularisée. Cela suggère que le surapprentissage n'était pas le problème principal avec le degré polynomial choisi, ou que l'alpha n'était pas optimal.
*   **Régression par Arbre de Décision** : Ce modèle a surpassé tous les autres, atteignant un R² impressionnant de 0.9934. Les arbres de décision excellent dans la capture des relations complexes et des interactions entre les caractéristiques, ce qui les rend très efficaces pour ce dataset.

### Modèle le Plus Performant

Le **modèle de Régression par Arbre de Décision** est clairement le plus performant pour la prédiction du PIB dans ce dataset, suivi de près par la Régression Polynomiale (Degré 2).

## Conclusions et Recommandations

1.  **Relation Non Linéaire :** La prédiction du PIB à partir de l'année et du pays nécessite des modèles capables de gérer des relations non linéaires, comme la régression polynomiale ou les arbres de décision. Les modèles linéaires simples sont insuffisants.
2.  **Importance des Caractéristiques :** Les variables 'Year' et 'Country Name' sont des prédicteurs puissants du PIB, surtout lorsque leurs effets non linéaires sont pris en compte.
3.  **Potentiel de Surapprentissage :** Bien que l'Arbre de Décision soit très performant, il est susceptible de surapprendre. Une optimisation des hyperparamètres (par exemple, la profondeur maximale de l'arbre, le nombre minimum d'échantillons par feuille) est cruciale pour assurer sa robustesse sur des données non vues.

### Prochaines Étapes

*   **Optimisation des Hyperparamètres :** Affiner les hyperparamètres du modèle d'Arbre de Décision, potentiellement en utilisant la validation croisée et des techniques comme `GridSearchCV` ou `RandomizedSearchCV`.
*   **Modèles d'Ensemble :** Explorer des modèles plus avancés tels que les Forêts Aléatoires (Random Forests) ou le Gradient Boosting (XGBoost, LightGBM), qui sont souvent plus robustes et précis.
*   **Analyse des Résidus :** Examiner les erreurs de prédiction pour identifier des tendances non capturées par les modèles actuels, ce qui pourrait orienter vers de nouvelles caractéristiques ou transformations.
*   **Intégration de Caractéristiques Supplémentaires :** Inclure d'autres indicateurs économiques ou sociaux pertinents si disponibles pour améliorer la capacité prédictive des modèles.

## Comment Exécuter ce Projet

1.  **Cloner le dépôt GitHub** :
    ```bash
    git clone <URL_DE_VOTRE_DEPOT>
    cd <NOM_DE_VOTRE_DEPOT>
    ```
2.  **Installer les dépendances** :
    ```bash
    pip install pandas scikit-learn matplotlib seaborn numpy
    ```
3.  **Exécuter le notebook** Jupyter (`votre_notebook.ipynb`) pour reproduire l'analyse.

---
