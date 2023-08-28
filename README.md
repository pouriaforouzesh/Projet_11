
# Projet de Scoring Crédit pour "Prêt à dépenser"


## Contexte

"Prêt à dépenser" est une société financière spécialisée dans l'offre de crédits à la consommation pour des personnes ayant peu ou pas d'historique de prêt. Dans une démarche de transparence et d'amélioration de l'expérience client, l'entreprise cherche à développer un outil de scoring crédit basé sur des données variées et un dashboard interactif pour expliquer les décisions d’octroi de crédit.

## Objectifs

1. **Modèle de scoring** : Prédire la probabilité de remboursement d'un client.
2. **Dashboard interactif** : Aider les chargés de relation client à interpréter les prédictions et améliorer la connaissance client.
3. **Mise en production** : Déployer le modèle et le dashboard via une API.

## Données

Les données utilisées pour ce projet peuvent être téléchargées à [cette adresse]([URL_DE_TELECHARGEMENT](https://www.kaggle.com/c/home-credit-default-risk/data)). L'ensemble contient plusieurs tables qui nécessiteront un travail d'assemblage.

## Fonctionnalités du Dashboard

- Visualisation intelligible du score et interprétation pour chaque client.
- Informations descriptives sur un client.
- Comparaison d'un client avec l'ensemble des clients ou un groupe similaire.

## Spécifications Techniques

- **Dashboard**: Dash, Bokeh ou Streamlit.
- **MLOps**: Automatisation et industrialisation de la gestion du cycle de vie du modèle.
- **Détection de Data Drift**: Utilisation de la librairie `evidently`.
- **Déploiement Cloud**: Azure webapp (ASP F1 gratuit), PythonAnywhere, Heroku ou équivalent.
- **Elaboration des modèles**: Cross-Validation, GridsearchCV.

## Recommandations

1. Prendre en compte le déséquilibre entre le nombre de bons et de moins bons clients.
2. Minimiser le coût d’erreur de prédiction des FN et FP.
3. Utiliser l'AUC et l'accuracy pour comparaison et contrôle.

## Contribution

Ce projet est supervisé par Michaël, manager chez "Prêt à dépenser".

---

**Note** : Remplacez "URL_DU_LOGO" et "URL_DE_TELECHARGEMENT" par les liens réels pour le logo et les données respectivement.

Ce résumé est un bon point de départ pour un README. Vous pouvez le personnaliser davantage en ajoutant des captures d'écran, des détails sur les dépendances logicielles, des instructions d'installation ou d'exécution, etc. selon les besoins de votre projet.
