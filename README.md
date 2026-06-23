# Détection Prédictive de Fraude Bancaire 🏦⚠️

Ce dépôt héberge un projet complet de Data Science visant à concevoir un modèle d'intelligence artificielle capable d'identifier les transactions financières frauduleuses en quasi temps réel. Face à une fraude bancaire moderne de plus en plus algorithmique, discrète et fragmentée, ce système s'appuie sur le Machine Learning pour repérer les signaux faibles qui échappent aux contrôles traditionnels.

---

## 📌 Contexte et Problématique

Ce projet est né d'un événement réel : une attaque informatique par transactions fragmentées subie par un membre de ma famille, où de petites sommes ont été subtilisées de manière répétée durant la nuit sans déclencher les alertes classiques. 

**L'objectif clé :** Développer un classifieur hautement performant capable de maximiser la détection des fraudes (taux de rappel élevé) tout en minimisant les faux positifs, préservant ainsi l'expérience et la fluidité du parcours client.

## 📊 Le Dataset

L'analyse est menée sur une base de données transactionnelle massive contenant **6 362 620 transactions** et **11 variables initiales** (montants, types de transactions, soldes avant/après opération). 
* **Défi majeur :** Un déséquilibre extrême des classes, la fraude ne représentant que **0,1 %** du volume total des données.

## 🛠️ Feature Engineering (Le cœur du signal)

Pour donner au modèle une forte capacité de discrimination, des variables dérivées stratégiques ont été calculées afin de capturer les anomalies de flux logiques :
- `DiffSoldeOrig` & `DiffSoldeDest` : Vérifient la cohérence mathématique des soldes avant/après opération (l'argent a-t-il disparu ou est-il apparu anormalement ?).
- `PourcentageMontantOrig` : Mesure le rapport entre le montant transféré et le solde initial du client.
- `activiteAnormale` : Variable combinée signalant une double anomalie simultanée (origine et destination).

Une Analyse en Composantes Principales (ACP) confirme que ces nouvelles variables capturent et répartissent nettement mieux la variance utile que les indicateurs bruts.

## 🚀 Modélisation et Performances

Le framework repose sur l'algorithme **XGBoost (XGBClassifier)**, idéal pour traiter les relations non linéaires complexes et le fort déséquilibre de classes sans nécessiter de rééchantillonnage lourd.

### Paramètres clés :
- `learning_rate` : 0.1
- `max_depth` : 6
- `subsample` : 0.8
- `enable_categorical` : True

### Résultats :
Le modèle final atteint une performance exceptionnelle de **99 % de F1-score**, garantissant une détection hautement fiable des pertes financières directes.

## 📁 Structure du Projet

```text
├── data/
│   └── fraud_data.csv          # Dataset de base (6.3M+ lignes)
├── notebooks/
│   └── fraud_detection.ipynb   # Analyse exploratoire (EDA), ACP & Modélisation
├── requirements.txt            # Dépendances du projet
└── README.md                   # Documentation
```

## 🔧 Installation et Démarrage rapide

### Prérequis
- Python 3.10+
- Les modules scientifiques indispensables (`pandas`, `numpy`, `scikit-learn`, `xgboost`, `plotly`, `shap`).

### Configuration
1. Clonez ce dépôt :
   ```bash
   git clone https://github.com
   cd predictive-fraud-detection
   ```

2. Installez les packages requis :
   ```bash
   pip install -r requirements.txt
   ```

3. Exécutez le script d'évaluation ou explorez le notebook pour visualiser la matrice de confusion et l'interprétabilité des variables via SHAP.

## 🤝 Contact

**ABDOULAYE TANGARA**
* Fintech & IA Product Manager
* Email : abdoulayetangara722@gmail.com

---
*"To get something you never had, you’ve got to do something you never did. Get your mind right"*
