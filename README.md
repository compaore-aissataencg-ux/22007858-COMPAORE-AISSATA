# 22007858-COMPAORE-AISSATA
# Rapport d’Analyse

## Étude Statistique et Prédictive des Risques Cardiaques

---

## Sommaire

1. Objectifs de l’Étude
2. Introduction et Problématique
3. Thématiques Abordées
4. Préparation et Qualité des Données
5. Analyse des Résultats : Facteurs de Risque Dominants
6. Analyse des Signaux de Protection
7. Performance Globale du Modèle et Recommandations
8.  Conclusion et Limites de l’Étude et Perspectives

---

## 1. Objectif de l’Étude

Ce projet s’inscrit dans une démarche d’analyse statistique appliquée à la santé, visant à exploiter des données cliniques afin de soutenir la prise de décision médicale. L’objectif principal est de transformer un jeu de données médicales brutes en un outil analytique interprétable et pertinent pour l’évaluation du risque cardiovasculaire.

---

## 2. Introduction et Problématique

Les maladies cardiovasculaires représentent l’une des principales causes de mortalité dans le monde. Leur détection précoce constitue un enjeu majeur de santé publique, nécessitant des outils d’aide au diagnostic fiables et interprétables.

Dans ce contexte, ce projet repose sur l’analyse du jeu de données **Heart Disease** issu du référentiel de l’UCI Machine Learning Repository. Ce dataset regroupe des informations cliniques, biologiques et diagnostiques collectées auprès de patients ayant subi des examens cardiaques approfondis.

La problématique centrale est la suivante :

> Comment exploiter efficacement des données cliniques hétérogènes afin de prédire le risque de maladie cardiaque tout en conservant une interprétation médicale claire des résultats ?

L’originalité de cette étude réside dans le choix d’un modèle explicatif (régression logistique) permettant non seulement la prédiction, mais également l’analyse fine de l’influence de chaque variable grâce aux Odds Ratios.

---

## 3. Thématiques Abordées

L’analyse couvre plusieurs dimensions complémentaires de la santé cardiovasculaire :

### 3.1 Facteurs démographiques

L’âge et le sexe sont étudiés comme variables structurelles influençant la prédisposition aux pathologies cardiaques. Ces facteurs permettent d’identifier des profils à risque sur le long terme.

### 3.2 Signes cliniques et biologiques

Les symptômes déclarés, tels que les types de douleurs thoraciques, ainsi que les mesures physiologiques (pression artérielle, cholestérol), sont analysés afin d’évaluer leur valeur informative dans la détection de la maladie.

### 3.3 Examens diagnostiques avancés

Une attention particulière est portée aux résultats d’examens techniques, notamment la fluoroscopie des vaisseaux coronaires, qui fournit une information directe sur l’état du système cardiovasculaire.

---

## 4. Préparation et Qualité des Données

Avant toute modélisation, un travail approfondi de préparation des données a été réalisé afin de garantir la robustesse des résultats.

### 4.1 Traitement des données manquantes


### 4.2 Encodage des variables catégorielles

Les variables qualitatives ont été transformées à l’aide de la méthode du **One-Hot Encoding**, permettant de représenter chaque modalité sous forme de variable binaire. Cette approche améliore la capacité du modèle à capter les effets spécifiques de chaque catégorie.

### 4.3 Standardisation des variables numériques

Les variables quantitatives ont été normalisées afin de rendre les coefficients du modèle comparables et d’éviter qu’une variable à grande échelle ne domine artificiellement les autres.

---

## 5. Analyse des Résultats : Facteurs de Risque Dominants

L’interprétation des résultats repose sur l’analyse des **Odds Ratios (OR)** issus de la régression logistique. Un Odds Ratio supérieur à 1 indique une augmentation du risque, tandis qu’un OR inférieur à 1 suggère un effet protecteur.

### 5.1 Rôle central de l’imagerie médicale (variable `ca`)

La variable représentant le nombre de vaisseaux coronaires colorés lors de la fluoroscopie apparaît comme le facteur le plus déterminant du modèle.

* **Deux vaisseaux atteints (`ca_2.0`)**
  L’Odds Ratio de **18,57** indique une augmentation extrêmement élevée du risque. Les patients présentant cette caractéristique ont une probabilité de maladie multipliée par plus de 18 par rapport au profil de référence.

* **Un ou trois vaisseaux atteints (`ca_1.0`, `ca_3.0`)**
  Les Odds Ratios compris entre **7,93** et **8,05** confirment le rôle critique de cette variable, soulignant l’importance des examens d’imagerie dans le diagnostic.

### 5.2 Influence du sexe

* **Profil masculin (`sex_Male`)**
  Avec un Odds Ratio de **5,80**, le sexe masculin apparaît comme un facteur de risque majeur. À caractéristiques cliniques équivalentes, les hommes présentent une probabilité de maladie cardiaque nettement supérieure à celle des femmes.

---

## 6. Analyse des Signaux de Protection

Certaines variables présentent des Odds Ratios significativement inférieurs à 1, traduisant un effet protecteur apparent.

### 6.1 Douleur thoracique typique

* **Angine typique (`cp_typical angina`)**
  Un Odds Ratio de **0,15** suggère une réduction du risque de l’ordre de 85 %. Ce résultat, contre-intuitif à première vue, met en évidence la différence entre symptômes perçus et gravité réelle de la pathologie.

### 6.2 Interprétation clinique

Les douleurs thoraciques typiques sont souvent rapidement prises en charge et peuvent correspondre à des causes moins sévères, tandis que les pathologies les plus graves peuvent évoluer de manière plus silencieuse, détectées principalement par des examens techniques.

---

## 7. Performance Globale du Modèle et Recommandations

Le modèle présente une performance satisfaisante, caractérisée par une bonne capacité de détection des patients réellement atteints. La sensibilité élevée permet de limiter les faux négatifs, ce qui est essentiel dans un contexte médical.

### Recommandations principales :

1. **Prioriser les examens d’imagerie**
   La fluoroscopie des vaisseaux coronaires doit être considérée comme un examen clé dans l’évaluation du risque.

2. **Renforcer la vigilance chez les hommes**
   Le sexe masculin constitue un facteur de risque structurel nécessitant une surveillance accrue.

3. **Utiliser le modèle comme outil de tri**
   Le modèle peut servir de filtre décisionnel pour orienter les patients vers des examens cardiologiques approfondis.

---

## 8. Limites de l’Étude et Perspectives

Cette étude repose sur un dataset de taille limitée, ce qui peut affecter la généralisation des résultats. De futures améliorations pourraient inclure :

* l’intégration de jeux de données plus récents ou plus volumineux,
* la comparaison avec d’autres modèles (arbres de décision, forêts aléatoires),
* l’ajout d’une validation croisée approfondie.
