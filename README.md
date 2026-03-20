# Green & Fast

`Green & Fast` est un projet d'école mené dans le cadre d'un projet de `Scrum Data Agile`.

L'objectif est d'améliorer les délais de livraison de plats à domicile, avec une contrainte métier forte : réduire le nombre de livraisons au-delà de 30 minutes, car ces retards entraînent un remboursement des frais de livraison. En parallèle, le projet vise à tendre vers une émission carbone de `0 g` en favorisant les solutions de livraison les moins émettrices.

Un des axes principaux du projet consiste à mieux comprendre quels facteurs influencent le temps de livraison, en particulier le type de véhicule, la distance, le contexte temporel et les conditions opérationnelles. L'idée est d'aider à choisir le mode de livraison le plus pertinent pour livrer plus vite tout en réduisant l'impact carbone.

## Contenu du dépôt

- `train.csv` : données d'entraînement avec la cible
- `test.csv` : données d'inférence sans la cible
- `Sample_Submission.csv` : modèle de soumission attendu
- `food-delivery-mvp-regression.ipynb` : notebook principal du MVP local
- `requirements.txt` : dépendances du projet
- `Note de Cadrage _ Projet _Green & Fast 2026_.pdf` : cadrage du projet

## Objectifs du MVP

Ce MVP a pour rôle de poser une base simple, lisible et défendable pour le projet. Il permet de :

- nettoyer les données
- créer des variables explicatives utiles
- analyser les délais de livraison selon le type de véhicule
- intégrer une lecture métier autour du seuil des `30 minutes`
- ajouter une dimension environnementale avec la distance estimée et les émissions de CO2
- comparer plusieurs modèles de régression
- générer un fichier de prédiction pour le jeu de test

## Logique métier

Le notebook s'appuie sur deux priorités :

- diminuer les livraisons de plus de `30 minutes`
- tendre vers une logistique à très faible émission carbone

Dans cette logique, le projet cherche à identifier les situations dans lesquelles :

- un véhicule rapide permet d'éviter un dépassement critique de délai
- un véhicule peu ou non émetteur peut être privilégié sans dégrader le service
- la distance, l'heure, le trafic ou le contexte de livraison augmentent le risque de retard

## Variables enrichies dans le projet

Le projet intègre notamment :

- une `distance_km` estimée à partir des coordonnées GPS
- une variable `co2_emission_g_km` selon le type de véhicule
- une lecture des livraisons `<= 30 min` et `> 30 min`
- des variables temporelles comme l'heure, le jour de la semaine ou le temps de préparation

## Modèles testés

Le MVP compare actuellement :

- `DummyRegressor`
- `LinearRegression`
- `RandomForestRegressor`

Les métriques de suivi sont :

- `MAE`
- `RMSE`
- `R2`

## Exécution

1. Installer les dépendances avec `pip install -r requirements.txt`.
2. Ouvrir `food-delivery-mvp-regression.ipynb`.
3. Exécuter les cellules de haut en bas.
4. Consulter les analyses, les graphiques et les métriques.
5. Récupérer le fichier de sortie généré pour la soumission.

## Positionnement du projet

Ce dépôt ne cherche pas encore à produire une solution industrielle complète. Il constitue une base pédagogique et analytique pour :

- comprendre le problème métier
- tester rapidement des hypothèses
- soutenir une démarche itérative en mode agile
- préparer les prochaines évolutions du projet
