# Iris-Income-Analysis
1. Description du projet

Ce projet utilise les données publiques de l’Insee issues de la base Filosofi IRIS 2021 pour analyser les revenus disponibles à l’échelle infracommunale.
L’objectif est de :

charger et nettoyer les données,

explorer les variables principales,

effectuer des estimations statistiques (moyennes, proportions, différences de moyennes),

étudier les propriétés asymptotiques des estimateurs,

mettre en place des modèles simples (régression linéaire).

2. Source des données

Les données proviennent de la page Insee :
https://www.insee.fr/fr/statistiques/8229323

Le fichier utilisé est :
Base IRIS sur les revenus disponibles (CSV, 892 Ko).

Il contient notamment : niveau de vie médian, déciles, taux de pauvreté, composantes du revenu, et identifiants géographiques.

3. Contenu du dataset

Chaque ligne correspond à un IRIS (unité statistique de 1 800 à 5 000 habitants).
Les principales variables sont :

médiane du niveau de vie,

taux de pauvreté,

déciles du revenu,

part des pensions, allocations chômage, prestations sociales, impôts.

Les noms exacts dépendent du dictionnaire fourni par l’Insee.

4. Points méthodologiques importants (Insee)

L’Insee donne plusieurs avertissements concernant l’usage de ces données :

Le périmètre a changé : depuis 2020, seules les communes de 5 000 habitants ou plus sont incluses (contre 10 000 avant 2019). Les comparaisons temporelles doivent donc être faites avec prudence.

Les indicateurs sont soumis au secret statistique et certains peuvent être masqués.

Les indicateurs ne sont pas sommables : ils ne peuvent pas être additionnés pour reconstituer des totaux.

Plusieurs dispositifs exceptionnels de 2020 et 2021 ne sont pas pris en compte (prime exceptionnelle, aides Covid, indemnité inflation, etc.). Cela peut entraîner une légère sous-estimation des revenus réels.

L’enquête ERFS intègre ces dispositifs, ce qui peut créer des divergences entre ERFS et Filosofi.

Une nouvelle méthode de géoréférencement a été introduite en 2019, ce qui affecte les comparaisons annuelles à l’échelle locale.

Ces données conviennent bien à une analyse statistique transversale pour l’année 2021, mais pas à l’analyse des évolutions d’une année sur l’autre.