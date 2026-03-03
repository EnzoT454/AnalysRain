#  Analyse des Précipitations Canadiennes
**IFT-3700 – Science des Données**

##  Description
Ce projet a pour objectif d’analyser des données de précipitations provenant de stations météorologiques canadiennes à l’aide de **NumPy**, **Pandas** et **SciPy**.

À partir d’un fichier brut (`precipitation.csv`), nous réalisons les étapes suivantes :
* **Agrégation :** Génération des totaux mensuels et du nombre d’observations.
* **Statistiques :** Calcul des précipitations moyennes et trimestrielles.
* **Géospatial :** Mesure des distances géographiques entre les stations.
* **Analyse de données :** Calcul de la corrélation des précipitations quotidiennes.

> Ce projet met l’accent sur la **vectorisation**, la manipulation efficace de DataFrames et les bonnes pratiques en science des données.

---

##  Structure du Projet

```text
.
├── data
│   ├── precipitation.csv     # Données brutes quotidiennes
│   ├── totals.csv            # Totaux mensuels par station
│   ├── counts.csv            # Nombre d'observations mensuelles
│   └── monthdata.npz         # Version NumPy des données
│
├── monthly_totals.py         # Nettoyage, pivot, distances, corrélations
├── np_summary.py             # Analyse avec NumPy
├── pd_summary.py             # Analyse avec Pandas
│
├── environment.yml           # Environnement Conda
├── requirements.txt          # Dépendances pip
└── README.md
```
##  Fonctionnement Général
### 1- Analyse NumPy (np_summary.py)

Calcule :

* Ville avec précipitations minimales
* Moyenne par mois
* Moyenne par ville
* Totaux trimestriels

Utilise uniquement des opérations matricielles vectorisées.

### 2- Analyse Pandas (pd_summary.py)

Même logique que NumPy mais avec :

* DataFrames
* Index nommés
* Résultats plus interprétables

### 3- Transformation et Analyse Complète (monthly_totals.py)

* Nettoyage et Agrégation : Conversion des dates (YYYY-MM), groupby par station/mois et passage au format "wide" via pivot().

* Distances Géographiques : Utilisation de GeoPy pour le calcul pairwise avec pdist et squareform.

* Corrélations : Implémentation manuelle de la corrélation de Pearson et comparaison avec DataFrame.corr().


###  Outils & Concepts Clés

* Langage : Python 3.9+
* Librairies : NumPy, Pandas, SciPy, GeoPy.
* Concepts : GroupBy, Pivot, Corrélation de Pearson, Distance géodésique.

###  Installation & Exécution

#### 1- Option Conda

```bash
conda env create --file environment.yml
conda activate ift6758-conda-env
```

#### 2- Option pip + virtualenv

```bash
python3 -m venv ift6758-venv
source ift6758-venv/bin/activate
pip install -r requirements.txt
```

### Lancer les analyses

```bash
# NumPy
python np_summary.py

# Pandas
python pd_summary.py

# Transformation + Corrélations + Distances
python monthly_totals.py

```

###  Résultats Attendus

Des tables mensuelles nettoyées et structurées.Une matrice $N \times N$ des distances entre stations.Une matrice $N \times N$ des corrélations de précipitations.















