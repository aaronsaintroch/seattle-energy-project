# 🏙️ Seattle Energy Project

Projet de data science réalisé dans le cadre de la mission OpenClassrooms  
**« Anticipez les besoins en consommation de bâtiments »**.

> 🏙️ Un projet de data science appliqué à la transition énergétique de la ville de Seattle, avec pour objectif de prédire la consommation énergétique de bâtiments non résidentiels à partir de leurs caractéristiques observables.

---

## 🎯 Contexte

Vous travaillez en tant que **Data Scientist pour la ville de Seattle**.  
Pour atteindre son objectif de **neutralité carbone à l’horizon 2050**, la ville cherche à mieux comprendre et anticiper la **consommation énergétique** ainsi que les **émissions des bâtiments non résidentiels**.

Dans ce projet, l’objectif est de construire un modèle capable de **prédire la consommation énergétique totale de bâtiments non destinés à l’habitation**, à partir de leurs caractéristiques :

- structurelles ;
- fonctionnelles ;
- temporelles ;
- géographiques.

L’enjeu est de proposer une approche utile pour **prioriser les analyses**, **orienter les audits** et **mieux cibler les bâtiments les plus énergivores**, même lorsque les mesures complètes ne sont pas disponibles.

---

## 🚀 Objectifs du projet

Ce projet vise à :

- réaliser une **analyse exploratoire** des données ;
- nettoyer et préparer les données pour la modélisation ;
- construire de nouvelles variables via du **feature engineering** ;
- comparer plusieurs modèles supervisés de régression ;
- optimiser le meilleur modèle ;
- identifier les variables les plus influentes sur la prédiction ;
- formaliser les résultats dans une présentation claire et orientée métier.

---

## 🧾 Données utilisées

Le projet repose principalement sur le fichier :

- `2016_Building_Energy_Benchmarking.csv`

Une extension historique a également été exploitée pour enrichir l’analyse :

- `Building_Energy_Benchmarking_Data,_2015-Present_20260330.csv`

---

## 📂 Emplacement attendu des données

Les fichiers de données **ne sont pas versionnés** dans ce dépôt.  
Ils doivent être placés localement dans :

```text
data/raw/


Structure attendue :

PythonProject3/
├── data/
│   ├── raw/
│   │   ├── 2016_Building_Energy_Benchmarking.csv
│   │   ├── Building_Energy_Benchmarking_Data,_2015-Present_20260330.csv
│   │   └── RFScanReport.csv
│   └── processed/
```

---

## 🧹 Préparation des données

Les principales étapes de préparation incluent :

- filtrage des bâtiments **non résidentiels** ;
- conservation des observations **Compliant** ;
- exclusion des lignes marquées comme `DefaultData` ;
- retrait des outliers déjà signalés ;
- suppression des colonnes trop incomplètes ;
- suppression des lignes sans cible exploitable ou sans surface valide ;
- prévention du **data leakage** par exclusion des variables trop directement liées à la cible.

---

## 🛠️ Feature engineering

Plusieurs variables ont été créées pour enrichir le signal disponible.

### 📆 Variables temporelles

- `BuildingAge`
- `DecadeBuilt`

### 🏢 Variables structurelles

- `HasParking`
- `ParkingRatio`
- `BuildingAreaRatio`
- `AvgFloorArea`
- `LogPropertyGFATotal`

### 🧩 Variables d’usage

- `IsMultiUse`
- `NumberOfUses`
- `LargestUseShare`
- `HasSecondUse`

### 🗺️ Variables de regroupement

- `NeighborhoodGroup`
- `PrimaryPropertyTypeGroup`

### ⚡ Indicateurs énergétiques binaires

- `HasSteam`
- `HasNaturalGas`
- `HasElectricity`

---

## 🤖 Modélisation

Les modèles testés dans le notebook principal sont :

- `DummyRegressor` *(baseline)*
- `LinearRegression`
- `SVR`
- `RandomForestRegressor`

### 📏 Métriques utilisées

- **RMSE**
- **MAE**
- **R²**

### 🔁 Validation

- séparation **train / test** ;
- **validation croisée** ;
- optimisation du meilleur modèle avec **GridSearchCV**.

---

## 📈 Interprétation du modèle

Le meilleur modèle est ensuite interprété avec une approche de **feature importance globale**, afin d’identifier les variables les plus influentes dans la prédiction de la consommation énergétique.

Les facteurs les plus structurants sont globalement liés à :

- la **taille** du bâtiment ;
- son **usage principal** ;
- sa **complexité fonctionnelle** ;
- certaines caractéristiques **spatiales** et **structurelles**.

---

## 📚 Notebooks du projet

### 1. Notebook principal

```text
notebooks/P3_Seattle_Energy.ipynb
```

Contient :

- l’analyse exploratoire ;
- le feature engineering ;
- la préparation des données ;
- la comparaison des modèles ;
- l’optimisation et l’interprétation du meilleur modèle.

### 2. Notebook historique

```text
notebooks/P3_Seattle_Energy_historical.ipynb
```

Contient :

- l’exploitation du fichier historique ;
- l’harmonisation avec les données 2016 ;
- une séparation temporelle ;
- une modélisation complémentaire sur plusieurs années.

---

## 📎 Présentations

Pour faciliter la lecture du projet, les supports sont disponibles en deux formats :

- **PDF** : consultation rapide et compatible GitHub
- **KEY** : version éditable Apple Keynote

### Storytelling
- [Version PDF](figures/notesbooks/presentations/Seattle_Energy_Storytelling.pdf)
- [Version Keynote](figures/notesbooks/presentations/Seattle_Energy_Storytelling.key)

### Résultats
- [Version PDF](figures/notesbooks/presentations/Seattle_Energy_Results_Presentation.pdf)
- [Version Keynote](figures/notesbooks/presentations/Seattle_Energy_Results_Presentation.key)

### Présentation projet
- [Version PDF](<figures/notesbooks/presentations/Seattle_Energy_Project_Presentation 2.pdf>)
- [Version Keynote](<figures/notesbooks/presentations/Seattle_Energy_Project_Presentation 2.key>)

## 🗂️ Structure du projet
```text
PythonProject3/
├── data/
│   ├── raw/
│   │   ├── .gitkeep
│   │   ├── 2016_Building_Energy_Benchmarking.csv
│   │   ├── Building_Energy_Benchmarking_Data,_2015-Present_20260330.csv
│   │   └── RFScanReport.csv
│   └── processed/
│       └── .gitkeep
├── figures/
│   └── notesbooks/
│       └── presentations/
│           ├── Seattle_Energy_Project_Presentation 2.key
│           ├── Seattle_Energy_Results_Presentation.key
│           └── Seattle_Energy_Storytelling.key
├── notebooks/
│   ├── P3_Seattle_Energy.ipynb
│   └── P3_Seattle_Energy_historical.ipynb
├── scripts/
├── .editorconfig
├── .gitignore
└── README.md

```text
## 📦 Livrables

Le projet comprend notamment :

- le notebook principal ;
- le notebook historique ;
- plusieurs présentations de soutenance au format `.key` ;
- les graphiques utilisés pour l’analyse et la communication.
---

## 🖥️ Environnement technique

Projet réalisé avec :

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Scikit-learn**
- **Jupyter / PyCharm**

---

## ▶️ Lancer le projet

### 1. Cloner le dépôt

```bash
git clone <URL_DU_DEPOT>
cd PythonProject3
```

### 2. Créer et activer l’environnement virtuel

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Installer les dépendances principales

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter ipykernel
```

### 4. Ajouter les fichiers de données dans

```text
data/raw/
```

### 5. Ouvrir les notebooks

```bash
jupyter lab
```

ou directement dans **PyCharm**.

---

## 🧠 Résumé

Ce projet montre comment une démarche de data science peut être mobilisée pour :

- mieux comprendre la consommation énergétique des bâtiments ;
- construire des variables métier pertinentes ;
- comparer et optimiser plusieurs modèles de régression ;
- produire une lecture exploitable pour la décision publique.

---

## 👤 Auteur

**Vincent Desmouceaux**  
Projet réalisé dans le cadre du parcours **Data Scientist / Machine Learning** chez OpenClassrooms.
