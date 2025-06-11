# Prédiction du Churn Client avec LightGBM

## Objectif du projet

Ce projet vise à prédire la probabilité qu’un client résilie son abonnement (churn) à partir de ses caractéristiques personnelles et de son historique de services. L’objectif est d’aider les équipes marketing à anticiper les départs et à optimiser les actions de fidélisation.

## Jeu de données

Le jeu de données provient d’un cas d’usage inspiré du secteur des télécommunications (dataset public Telco Customer Churn). Il contient 7043 clients avec des variables telles que :
- Données démographiques (âge, statut familial, etc.)
- Informations sur les services utilisés (Internet, sécurité, support, etc.)
- Comportement d’achat (type de contrat, facturation, charges mensuelles)
- État de churn (Oui 1/ Non 0)

## Méthodologie

1. **Exploration des données**
   - Analyse de la répartition du churn : 27 % des clients sont partis.
   - Visualisations pour comprendre les facteurs liés au churn (ex. tenure, contrat, genre).

2. **Prétraitement**
   - Nettoyage des valeurs nulles et doublons.
   - Encodage des variables catégorielles avec `LabelEncoder` et `OneHotEncoding`.

3. **Modélisation**
   - Séparation des données en `X_train`, `X_test`, `y_train`, `y_test`.
   - Entraînement de plusieurs modèles : 
     - Régression Logistique
     - Random Forest
     - XGBoost
     - LightGBM

4. **Optimisation**
   - Tuning d’hyperparamètres pour LightGBM via `GridSearchCV` avec un scoring basé sur le `f1-score`.

## Modèle retenu : LightGBM

Le modèle LightGBM a été retenu pour sa capacité à équilibrer précision et rappel dans la détection des clients à risque de churn.  
**Performances finales :**
- Accuracy : 79.96 %
- F1-score (churn) : 0.57
- Précision (churn) : 0.66
- Rappel (churn) : 0.50

## Cas d’usage simulé

Une fonctionnalité a été ajoutée pour permettre à l’entreprise de tester un fichier Excel avec de nouveaux clients :
- Probabilité de churn en pourcentage
- Prédiction finale (0 ou 1)

Résultat exporté dans un fichier `.xlsx` utilisable par les équipes non techniques.

## Fichiers présents dans le dépôt

- `telco-customer.ipynb` : notebook principal avec exploration, modélisation et prédiction.
- `model_lightgbm.pkl` : modèle entraîné et sauvegardé avec `joblib`.
- `resultats_clients_predits.xlsx` : fichier avec les prédictions pour de nouveaux clients.
- `clients_a_tester_.xlsx` : exemple de données en entrée.
- `.gitignore` : fichiers à exclure du versionnage Git.

## Comment utiliser ce projet

1. Cloner le dépôt : git clone https://github.com/marthaavilas/telco-churn-prediction.git

2. Ouvrir le fichier `telco-customer.ipynb` dans Jupyter Notebook.
3. Charger un fichier Excel de clients à tester (mêmes colonnes que `X_test`).
4. Lancer les cellules pour obtenir les prédictions.
5. Le résultat sera exporté automatiquement dans `resultats_clients_predits.xlsx`.

## Compétences mobilisées

- Python (Pandas, Scikit-learn, Matplotlib, Seaborn)
- Machine Learning (classification binaire, tuning d'hyperparamètres)
- Modèles supervisés : LightGBM, Random Forest, XGBoost, Régression Logistique
- Visualisation des résultats et interprétation métier
- Export des résultats pour usage non technique
