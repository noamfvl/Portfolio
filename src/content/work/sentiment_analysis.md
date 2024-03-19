---
title: Analyse des sentiments à partir de sources textuelles
publishDate: 2023-03-02 00:00:00
img: /portfolio/assets/sentiment_analysis.jpg
img_alt: sentiment analysis
description: ""
tags:
  - Opinion Mining
  - Python
  - SQL
---
### Contexte et objectifs du projet

<div style="text-align: justify"> 
L'analyse des sentiments, également connue sous d'opinion mining est est le processus qui consiste à analyser un texte numérique pour déterminer si le ton émotionnel du message est plutôt positif ou négatif. Dans le cadre de ce projet, je dispose de 50 000 critiques de films notés positivement ou négativement. Ce jeu est balancé de manière suivante : 25 000 critiques positives et 25 000 négatives. De plus, 25 000 critiques seront utilisées pour l’apprentissage et 25 000 pour le test. Chaque critique est dotée d’une note comprise entre 1 et 10. Une critique est négative lorsque sa note est inférieure à 4 et est positive lorsqu’elle est supérieure à 7. L'objectif est donc de prédire la catégorie d’une critique (positive ou négative) à partir de son commentaire.
</div>

### Démarche et résolution du problème 
##### Entreposage des données

<div style="text-align: justify"> 
Dans un premier temps, il est nécessaire d'entreposer les 50 000 critiques de film. J'obtiens donc les critiques caractérisées par un ID, un commentaire, une note et une catégorie parmi "positive" ou "négative". De plus chaque mot contenu dans chaque critique va servir de descripteur, chaque descripteur est donc caractérisé par un mot et sa valeur qui est son nombre d’occurences dans chaque critique. J'obtiens aussi des descriptions qui sont des ensembles de descripteurs selon une condition. L’échantillonnage pourra être ammené à changer, je vais donc stocker des commentaires afin d’avoir une trace de l'objectif et des valeurs de chaque échantillonnage. 
</div>

<div style="text-align: justify"> 
J'ai donc choisi de créer 4 tables distinctes, les critiques, les descripteurs, les descriptions et les échantillons. Cela m'a donné le schéma conceptuel suivant :
</div>

![Schéma conceptuel](/portfolio/assets/schema_conceptuel.png)

<div style="text-align: justify"> 
Après analyse de mon schéma conceptuel et de la multiplicité de chaque relation entre nos 4 tables, j'ai obtenu une base relationnelle composée de 7 tables.
</div>

![Schéma relation](/portfolio/assets/schema_relation.png)

<div style="text-align: justify"> 
Afin de charger mes données provenant de différents fichiers texte dans ma base de données, j'ai dans un premier temps effectuer des transformations avec le package Pandas. J'ai notamment supprimé les stopwords. Les stopwords sont des mots courants et fréquents qui n'apportent pas de valeur pour notre analyse. En les supprimant on se concentre sur les mots véritablement informatifs qui vont me permettre de prédire la catégorie de la critique. Une fois les données traitées, je les ai insérées avec le package SQLALchemy.
</div>

##### Apprentissage

<div style="text-align: justify"> 
Afin de réaliser mon apprentissage, j'ai dans un premier temps prélever divers échantillons aléatoires de critiques positives et négatives à partir de ma base de données. Concernant le choix des modèles d’apprentissage, j'ai décidé d’en sélectionner trois
afin de pouvoir les comparer entre eux par la suite. J'ai donc choisi le modèle SVM, Naive Bayes et le modèle KNN.
</div>

### Résultats

<div style="text-align: justify"> 
Les modèles de Naive Bayes et SVM se sont révélés tous deux performants. J'ai pu atteindre près de 85 % de précision avec ces deux modèles sur divers échantillons tirés aléatoirement. En revanche, le modèle K-NN a montré une précision moindre, ne dépassant pas les 60 % de précision pour prédire la catégorie des critiques.
</div>