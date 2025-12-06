# Mini-Projet Churn Prediction

## 📌 Description du projet
Ce projet construit un pipeline complet de Data Science pour prédire le churn des clients.  
Il comprend :
- Analyse exploratoire (EDA)
- Nettoyage et préparation des données
- Encodage et normalisation
- Construction d’un modèle supervisé (Logistic Regression)
- Évaluation avec métriques pertinentes
- Documentation professionnelle

## 📁 Structure du projet
```
.
├── data_churn.csv
├── notebook.ipynb
├── README.md
└── model_outputs/
```

## 🔧 Installation & environnement
Créer un environnement Python :

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate    # Windows
```

Installer les dépendances :

```bash
pip install pandas scikit-learn matplotlib seaborn jupyter
```

## ▶️ Exécution du notebook
Lancer Jupyter Notebook :

```bash
jupyter notebook
```

Ouvrir et exécuter :

```
notebook.ipynb
```

Le notebook réalisera automatiquement :
1. Chargement du dataset  
2. Analyse exploratoire  
3. Nettoyage des données  
4. Split train/test  
5. Préprocessing (OneHotEncoder + StandardScaler)  
6. Entraînement du modèle  
7. Évaluation détaillée (classification report, confusion matrix, ROC-AUC)  

## 📊 Résultats principaux attendus
- Matrices de confusion  
- Scores F1, précision, recall  
- ROC-AUC > 0.90 selon version du modèle  
- Analyse des biais potentiels  

## 🧪 Reproductibilité
- `random_state = 42`
- Pipeline scikit-learn unifié
- Nettoyage documenté

## 📄 Licence
Projet académique — usage libre non commercial.
