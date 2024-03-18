---
title: Description et prévision d'une série temporelle
publishDate: 2024-03-01 00:00:00
img: /portfolio/assets/time_series.png
img_alt: time series illustration
description: ""
tags:
  - Série temporelle
  - Prévision
  - R
  

---
<div style="text-align: justify"> 

### Contexte et objectifs du projet
L'Institut National de la Statistique et des Études Économiques (INSEE) met à disposition du grand public une multitude de séries chronologiques portant sur diverses thématiques. Pour ce projet, mon intérêt s'est porté sur la série représentant le nombre de mariages mensuels enregistrés entre personnes de sexe différent en France métropolitaine, couvrant la période allant de janvier 1946 à décembre 2020. L'objectif principal de cette étude est de développer un modèle de prédiction afin d'estimer le nombre de mariages mensuels pour la période s'étendant de janvier 2021 à décembre 2025.

### Démarche et résolution du problème 
Pour aborder ce projet, j'ai utilisé le langage R en me basant sur l'interface RStudio.

##### Préparation des données
Pour la préparation des données, j'ai dans un premier temps sélectionné les colonnes pertinentes puis j'ai ajusté le format de la date et converti les valeurs en entier. Enfin, j'ai créé un objet de type zoo pour la manipulation des séries chronologiques. Cette étape de préparation des données a permis de garantir la cohérence et la qualité des données pour les analyses ultérieures.

##### Analyse exploratoire
Pour l'analyse exploratoire des données sur le nombre de mariages mensuels, j'ai réalisé plusieurs visualisations à l'aide du package ggplot2. Dans un premier temps, j'ai décidé de représenter le nombre de mariages mensuels de 1946 à 2020 avec une courbe de régression lissée.  
<br>

![nombre de mariages mensuels de 1946 à 2020](/portfolio/assets/mariage_1946.png)

<br>

La tendance du phénomène semble décroissante, ce qui se confirme grâce à la courbe de régression lissée. En effet, celle-ci débute aux alentours de 35 000 mariages mensuels en 1946 et se termine approximativement à 25 000 mariages en 2020. On note également la présence d’une fluctuation périodique (saisonnalité). Au vu du nombre élevé de données, j'ai décidé de m'intéresser par la suite aux mariages entre le 1 janvier 2000 et le 1 décembre 2020.

<br>

![nombre de mariages mensuels de 2000 à 2020](/portfolio/assets/mariage_2000.PNG)

<br>

Ici aussi, j'ai pu constater une diminution générale du nombre de mariages. On remarque aussi que la fluctuation périodique est plus forte au début des années 2000. On note également une baisse significative du nombre de mariages pour la fin de l'année 2019 et le début de l'année 2020. Cela peut s’expliquer par le confinement alors mis en place dans tout le pays. J'ai ensuite décidé de m'intéresser à la saisonnalité en modélisant un diagramme en boîte portant sur la distribution mensuels du nombre de mariages entre le 1 janvier 2000 et le 1 décembre 2020.

<br>

![distribution mensuels du nombre de mariages de 2000 à 2020](/portfolio/assets/boxplot_mariage.png)

<br>

On remarque ici un duo de tête, juin et juillet, qui sont les seules mois à avoir une moyenne du nombre de mariages supérieure à 40 000. Les mois d'août, de septembre et de mai possèdent également des moyennes élevées comparé aux autres mois (entre 35 000 et 25 000). Durant l’automne et l’hiver, le nombre moyen de mariages diminue drastiquement. Cette fluctuation périodique peut être expliquée par celle du temps (météo), en effet les mois les plus prisés pour se marier sont ceux où il fait le plus beau/chaud.

##### Modélisation
Pour cette phase du projet, j'ai commencé par ajuster le modèle de régression linéaire pour examiner la relation entre la date et le nombre de mariages. Le modèle de régression linéaire a montré une forte relation entre la date et le nombre de mariages, avec un coefficient de détermination (R-carré) de 0.983, ce qui suggère que le modèle explique bien la variation des données.

<br>

Pour finir cette partie, j'ai décidé de calculer et de visualiser les coefficients saisonniers afin de pouvoir ajuster mon modèle et prendre en compte les variations saisonnières lors de ma prévision.

<br>

![coefficient saisonnier](/portfolio/assets/coefficient_saisonnier.png)

### Résultats
À partir des étapes de modélisation précédentes, j'ai donc pu réaliser une prévision du nombre de mariages mensuels en France métropolitaine jusqu'en décembre 2025. 

<br>

![Prévision](/portfolio/assets/time_series.png)

</div>