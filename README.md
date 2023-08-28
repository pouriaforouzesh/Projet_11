
# Implémentez un modèle de scoring
Vous êtes Data Scientist au sein d'une société financière, nommée  **"Prêt à dépenser"**, qui propose des crédits à la consommation pour des personnes ayant peu ou pas du tout d'historique de prêt.

[![Logo entreprise ](https://user.oc-static.com/upload/2019/02/25/15510866018677_logo%20projet%20fintech.png)](https://user.oc-static.com/upload/2019/02/25/15510866018677_logo%20projet%20fintech.png)

L’entreprise souhaite  **mettre en œuvre un outil de “scoring crédit” pour calculer la probabilité** qu’un client rembourse son crédit, puis classifie la demande en crédit accordé ou refusé. Elle souhaite donc développer un  **algorithme de classification**  en s’appuyant sur des sources de données variées (données comportementales, données provenant d'autres institutions financières, etc.).

De plus, les chargés de relation client ont fait remonter le fait que les clients sont de plus en plus demandeurs de  **transparence**  vis-à-vis des décisions d’octroi de crédit. Cette demande de transparence des clients va tout à fait dans le sens des valeurs que l’entreprise veut incarner.

**Prêt à dépenser** décide donc de  **développer un dashboard interactif**  pour que les chargés de relation client puissent à la fois expliquer de façon la plus transparente possible les décisions d’octroi de crédit, mais également permettre à leurs clients de disposer de leurs informations personnelles et de les explorer facilement.

#### **Les données**

Voici  [les données](https://www.kaggle.com/c/home-credit-default-risk/data)  dont vous aurez besoin pour réaliser le dashboard. Pour plus de simplicité, vous pouvez les télécharger à  [cette adresse](https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/Parcours_data_scientist/Projet+-+Impl%C3%A9menter+un+mod%C3%A8le+de+scoring/Projet+Mise+en+prod+-+home-credit-default-risk.zip).

Vous aurez sûrement besoin de joindre les différentes tables entre elles.

#### **Votre mission**

1.  Construire un modèle de scoring qui donnera une prédiction sur la probabilité de faillite d'un client de façon automatique.
2.  Construire un dashboard interactif à destination des gestionnaires de la relation client permettant d'interpréter les prédictions faites par le modèle, et d’améliorer la connaissance client des chargés de relation client.
3.  Mettre en production le modèle de scoring de prédiction à l’aide d’une API, ainsi que le dashboard interactif qui appelle l’API pour les prédictions.

**Michaël**, votre manager, vous incite à sélectionner un ou des kernels Kaggle pour vous faciliter l’analyse exploratoire, la préparation des données et le feature engineering nécessaires à l’élaboration du modèle de scoring. Si vous le faites, vous devez analyser ce ou ces kernels et le ou les adapterpour vous assurer qu’ils répond(ent) aux besoins de votre mission.

C’est optionnel, mais nous vous encourageons à le faire afin de vous permettre de vous focaliser sur l’élaboration du modèle, son optimisation et sa compréhension.

#### **Spécifications du dashboard**

Michaël vous a fourni des spécifications pour le dashboard interactif. Celui-ci devra contenir au minimum les fonctionnalités suivantes :

-   Permettre de visualiser le score et l’interprétation de ce score pour chaque client de façon intelligible pour une personne non experte en data science.
-   Permettre de visualiser des informations descriptives relatives à un client (via un système de filtre).
-   Permettre de comparer les informations descriptives relatives à un client à l’ensemble des clients ou à un groupe de clients similaires.

#### **Spécifications techniques**

Michaël vous propose d’utiliser Dash ou Bokeh ou Streamlit pour réaliser le Dahboard interactif.

Michaël souhaite également, afin de pouvoir faire évoluer régulièrement le modèle, tester la mise en oeuvre d’une démarche de type MLOps d’automatisation et d’industrialisation de la gestion du cycle de vie du modèle. Il vous envoie  [la liste d’outils à utiliser](https://s3.eu-west-1.amazonaws.com/course.oc-static.com/projects/Data_Scientist_P7/Outils+Open+Source+MLOps.pdf)  pour créer une plateforme MLOps qui s’appuie sur des outils Open Source.

Michaël vous demande également de tester l’utilisation de la librairie  **evidently**  pour détecter dans le futur du  **Data Drift** en production. Pour cela vous prendrez comme hypothèse que le dataset “application_train” représente les datas pour la modélisation et le dataset “application_test” représente les datas de nouveaux clients une fois le modèle en production.

L’analyse à l’aide d’**evidently**  vous permettra de  **détecter éventuellement du Data Drift sur les principales features**, entre les datas d’entraînement et les datas de production, au travers du tableau HTML d’analyse que vous aurez réalisé.

**Le déploiement de l'application dashboard et de l’API**  seront réalisées sur une plateforme Cloud, de préférence une solution gratuite, par exemple Azure webapp (ASP F1 gratuit), PythonAnywhere, Heroku avec le package “student” de Github ou tout autre solution.

D’autre part Michaël attend que vous mettiez en oeuvre une démarche d’élaboration des modèles avec  **Cross-Validation, via GridsearchCV ou équivalent**.

Il vous donne un dernier conseil : si vous obtenez des scores supérieurs au 1er du challenge Kaggle (AUC > 0.82), posez-vous la question si vous n’avez pas de l’overfitting dans votre modèle.

Michaël attend également de votre part  **une note technique**, présentant toute votre démarche d’élaboration du modèle jusqu’à l’analyse du Data Drift, afin de partager vos réalisations avec vos collègues.

#### **Spécifications contextuelles**

Michaël vous fait part de sa vigilance dans l’élaboration du modèle, concernant deux points spécifiques au contexte métier :

-   Le déséquilibre entre le nombre de bons et de moins bons clients doit être pris en compte pour élaborer un modèle pertinent, à l’aide d’au moins une méthode au choix
-   Le déséquilibre du coût métier entre un faux négatif (FN - mauvais client prédit bon client : donc crédit accordé et perte en capital) et un faux positif (FP - bon client prédit mauvais : donc refus crédit et manque à gagner en marge)

-   Vous pourrez supposer, par exemple, que le coût d’un FN est dix fois supérieur au coût d’un FP
-   Vous créerez un score “métier” (minimisation du coût d’erreur de prédiction des FN et FP) pour comparer les modèles, afin de choisir le meilleur modèle et ses meilleurs hyperparamètres. Attention cette minimisation du coût métier doit passer par l’optimisation du seuil qui détermine, à partir d’une probabilité, la classe 0 ou 1 (un “predict” suppose un seuil à 0.5 qui n’est pas forcément l’optimum)
-   En parallèle, maintenez pour comparaison et contrôle des mesures plus techniques, telles que l’AUC et l’accuracy

### Livrables

-   L’application de  **dashboard**  interactif répondant aux spécifications ci-dessus et  **l’API de prédiction**  du score, déployées chacunes sur le cloud.
-   Un  **dossier,** géré via un outil de versioning de code contenant :

-   Le notebook ou code de la modélisation (du prétraitement à la prédiction), intégrant via MLFlow le tracking d’expérimentations et le stockage centralisé des modèles
-   Le code générant le dashboard
-   Le code permettant de déployer le modèle sous forme d'API
-   Pour les applications dashboard et API, un fichier introductif permettant de comprendre l'objectif du projet et le découpage des dossiers, et un fichier listant les packages utilisés seront présents dans les dossiers
-   Le tableau HTML d’analyse de data drift réalisé à partir d’**evidently**

-   Une  **note méthodologique**  décrivant :

-   La méthodologie d'entraînement du modèle (2 pages maximum)
-   Le traitement du déséquilibre des classes (1 page maximum)
-   La fonction coût métier, l'algorithme d'optimisation et la métrique d'évaluation (1 page maximum)
-   Un tableau de synthèse des résultats (1 page maximum)
-   L’interprétabilité globale et locale du modèle (1 page maximum)
-   Les limites et les améliorations possibles (1 page maximum)
-   L’analyse du Data Drift (1 page maximum)

-   Un  **support de présentation**  pour la soutenance, détaillant le travail réalisé (Powerpoint ou équivalent, 30slides maximum).

-   Des copies écran des commits, du dossier Github (+ lien vers ce dossier) et de l’exécution des tests unitaires, qui sont les preuves qu’un  **pipeline de déploiement continu**  a permis de déployer l’API, doivent être formalisés dans ce support de présentation.
#   P r o j e t _ 1 1  
 