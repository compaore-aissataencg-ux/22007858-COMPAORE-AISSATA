# 22007858-COMPAORE-AISSATA
# Rapport d’Analyse

## Étude Statistique et Prédictive des Risques Cardiaques

---

## Sommaire

1. Objectifs de l’Étude
2. Introduction et Problématique
3.  Analyse Exploratoire des Données (EDA)
4.  Prétraitement et Ingénierie des Caractéristiques
5. Approches de Modélisation
6. Évaluation des Performances
7. Conclusion

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

3. Analyse Exploratoire des Données (EDA)
Avant la modélisation, une analyse approfondie a été menée sur le jeu de données UCI Heart Disease pour comprendre la structure et la qualité des informations cliniques.

Nettoyage rigoureux : Initialement composé de 920 entrées, le dataset présentait de nombreuses valeurs manquantes sur des variables clés. Les colonnes comme id, dataset, fbs (glycémie à jeun) et restecg ont été écartées car elles n'apportaient pas de valeur prédictive fiable ou étaient trop incomplètes. Après suppression des lignes contenant des valeurs nulles, nous avons travaillé sur un échantillon robuste de 299 patients.

Analyse de corrélation : La matrice de corrélation a révélé que des facteurs tels que le type de douleur thoracique (cp), l'âge et le sexe jouent un rôle déterminant dans la prédiction.

Distribution des classes : L'analyse visuelle montre une répartition des classes (malade vs sain) permettant un entraînement équilibré sans nécessité de rééchantillonnage complexe.

(Graphique : Matrice de corrélation des variables cliniques) (Graphique : Répartition des cas positifs et négatifs)

4. Prétraitement et Ingénierie des Caractéristiques

La préparation des données a été une étape cruciale pour assurer la convergence de l'algorithme personnalisé :

Binarisation de la cible : La variable num (allant de 0 à 4) a été transformée en une variable binaire output (0 pour l'absence de maladie, 1 pour la présence).

Encodage Catégoriel : Les variables qualitatives telles que le sexe, le type de douleur thoracique et la pente du segment ST ont été transformées via le One-Hot Encoding. Cela a permis de passer d'un format textuel à un format matriciel de 17 caractéristiques numériques exploitables par les modèles.

Partitionnement : Les données ont été divisées de manière classique : 80% pour l'entraînement (209 individus) et 20% pour le test (90 individus).

5. Approches de Modélisation
   
Modèle de Référence (Scikit-learn)
Nous avons utilisé l'implémentation LogisticRegression de Scikit-learn comme référence de performance. Ce modèle utilise des optimiseurs avancés et une régularisation par défaut.

Implémentation Personnalisée (From Scratch)
Pour comprendre la mécanique interne du modèle, une classe Python a été développée manuellement. Elle repose sur deux piliers mathématiques :

La Fonction Sigmoïde : Utilisée pour transformer la combinaison linéaire des caractéristiques en une probabilité comprise entre 0 et 1.
La Fonction de Coût (Log-Loss) : Pour mesurer l'erreur du modèle et ajuster les poids via la descente de gradient.

6. Évaluation des Performances
L'évaluation repose sur plusieurs métriques pour garantir que le modèle ne se contente pas de prédire la classe majoritaire.

Précision Globale (Accuracy) : Le modèle Scikit-learn atteint 84,4%, un score élevé qui témoigne de la pertinence des caractéristiques choisies.

Matrice de Confusion : Sur les 90 patients testés, le modèle a correctement identifié 33 cas de maladie (Vrais Positifs) et 43 cas de patients sains (Vrais Négatifs). Seuls 6 patients sains ont été classés à tort comme malades.

Analyse du Rappel (Recall) : Avec un rappel de 0.80 pour la classe "Malade", le modèle est capable de détecter 80% des personnes réellement atteintes, ce qui est crucial dans un contexte médical.

(Graphique : Visualisation de la matrice de confusion)

7. Conclusion
Cette étude démontre que la régression logistique, bien que simple, est extrêmement efficace pour le diagnostic binaire de maladies cardiaques. La comparaison montre que notre implémentation personnalisée converge vers des résultats similaires à ceux des bibliothèques industrielles, validant ainsi la compréhension des mécanismes d'optimisation et de descente de gradient.
Le modèle présente une performance satisfaisante, caractérisée par une bonne capacité de détection des patients réellement atteints. La sensibilité élevée permet de limiter les faux négatifs, ce qui est essentiel dans un contexte médical.


