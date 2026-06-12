# FraudShield-AI

Projekt grupor për lëndën **Modelet e Mësimit Makinor** — zbulimi i mashtrimit në transaksionet e kartave të kreditit duke përdorur algoritme të ndryshme të machine learning.

## Dataset

- **Burimi:** [Credit Card Fraud Detection — Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)
- **Madhësia:** 284,807 transaksione, 492 mashtrime (0.17%)
- **Features:** 28 variabla PCA (V1–V28) + Amount + Time

## Struktura e projektit

```
FraudShield-AI/
├── data/
│   ├── creditcard.csv          # Dataset origjinal
│   └── processed/              # Të dhënat e parapërpunuara (.npy)
├── notebooks/
│   ├── 01_eda.ipynb            # Exploratory Data Analysis
│   ├── 02_preprocessing.ipynb  # Parapërpunimi, SMOTE, feature selection
│   ├── 03_classification.ipynb # LogReg, KNN, Random Forest, XGBoost
│   ├── 04_neural_network.ipynb # MLP Neural Networks (2 arkitektura)
│   └── 05_clustering.ipynb     # K-Means Clustering
├── models/
│   └── best_model.h5           # Modeli më i mirë i ruajtur
├── images/                     # Grafiku dhe vizualizime
├── docs/                       # Raporti i projektit
├── requirements.txt
└── README.md
```

## Instalimi

### 1. Klono repositorin

```bash
git clone https://github.com/Erjoon7/FraudShield-AI---MMM.git
cd FraudShield-AI---MMM
```

### 2. Instalo bibliotekat

```bash
pip install -r requirements.txt
```

### 3. Shkarko datasetin

Shkarko `creditcard.csv` nga [Kaggle](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) dhe vendose në folderin `data/`.

## Ekzekutimi

Hap Jupyter Notebook dhe ekzekuto notebook-ët në këtë renditje:

```bash
jupyter notebook
```

| Hapi | Notebook | Përshkrimi |
|------|----------|------------|
| 1 | `01_eda.ipynb` | Analiza eksploratore e të dhënave |
| 2 | `02_preprocessing.ipynb` | Parapërpunimi dhe ruajtja e të dhënave |
| 3 | `03_classification.ipynb` | Trajnimi i 4 klasifikuesve |
| 4 | `04_neural_network.ipynb` | Trajnimi i rrjetave neurale |
| 5 | `05_clustering.ipynb` | Analiza e grupimit K-Means |

> **Shënim:** `02_preprocessing.ipynb` duhet ekzekutuar para notebook-eve të tjerë pasi gjeneron të dhënat në `data/processed/`.

## Modelet e implementuara

### Klasifikues
- **Logistic Regression** — klasifikues linear
- **K-Nearest Neighbors** — klasifikues distance-based
- **Random Forest** — ensemble bazuar në pemë vendimmarrëse
- **XGBoost** — gradient boosting

### Rrjeta Neurale
- **Simple MLP** — arkitekturë e thjeshtë (2 shtresa të fshehura)
- **Deep MLP** — arkitekturë e thellë (3 shtresa të fshehura + BatchNormalization + Dropout)

### Grupimi
- **K-Means** — grupim me K=2, vizualizim me PCA 2D

## Rezultatet

| Modeli | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|--------|----------|-----------|--------|----------|---------|
| Logistic Regression | 0.9878 | 0.1069 | 0.8526 | 0.1899 | 0.9639 |
| KNN | 0.9906 | 0.1348 | 0.8526 | 0.2328 | 0.9289 |
| Random Forest | 0.9994 | 0.8765 | 0.7474 | 0.8068 | 0.9395 |
| XGBoost | 0.9973 | 0.3581 | 0.8105 | 0.4968 | 0.9731 |

**Modeli më i mirë (F1-score): Random Forest** — i ruajtur si `models/best_model.h5`
