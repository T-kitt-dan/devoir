# ETE435 — Géoinformatique · Devoir 1

**Ingénierie des données géospatiales, fiabilité des données, calculs distanciels et analyse de proximité**

[![Ouvrir dans Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/T-kitt-dan/devoir/master?filepath=devoir1_ETE435.ipynb)

> Cliquez sur le badge **Binder** ci-dessus pour exécuter le notebook directement dans votre navigateur, **sans rien installer**.

---

## Description

Ce projet traite un jeu de données réel d'aéroports canadiens (source : OurAirports). Il couvre :

- **Nettoyage de données** : détection et suppression des valeurs non numériques et des coordonnées aberrantes
- **Formule de Haversine** : calcul de distances géodésiques entre aéroports
- **SIG avec GeoPandas** : création d'un GeoDataFrame et export en GeoJSON (EPSG:4326)
- **Analyse de proximité** : identification des grands aéroports canadiens et leurs distances à Montréal (CYUL)

---

## Contenu du dépôt

| Fichier | Description |
|---|---|
| `devoir1_ETE435.ipynb` | Notebook Jupyter principal (avec toutes les sorties) |
| `ETE_435_Donnees_Devoir_1_H26 (1).csv` | Données brutes originales fournies pour le devoir |
| `airports_clean.csv` | Données nettoyées (356 aéroports valides) |
| `large_airports_canada.geojson` | 24 grands aéroports — format GeoJSON, EPSG:4326 |
| `requirements.txt` | Liste exacte des dépendances Python |

---

## Option 1 — Exécution en ligne (recommandée, aucune installation)

Cliquez sur le badge Binder en haut de cette page, ou utilisez ce lien direct :

**https://mybinder.org/v2/gh/T-kitt-dan/devoir/master?filepath=devoir1_ETE435.ipynb**

Binder charge automatiquement le dépôt, installe les dépendances et ouvre le notebook dans un environnement Jupyter. Comptez environ 1 à 3 minutes pour le démarrage.

---

## Option 2 — Exécution locale

### Prérequis

- Python 3.10 ou supérieur (testé avec Python 3.13.14)
- Git

### Étapes

**1. Cloner le dépôt**

```bash
git clone https://github.com/T-kitt-dan/devoir.git
cd devoir
```

**2. Créer un environnement virtuel**

```bash
python -m venv venv_devoir2
```

Activer l'environnement :

- Windows : `venv_devoir2\Scripts\activate`
- macOS/Linux : `source venv_devoir2/bin/activate`

**3. Installer les dépendances**

```bash
pip install -r requirements.txt
```

Packages principaux installés :

| Package | Version |
|---|---|
| pandas | 3.0.3 |
| geopandas | 1.1.4 |
| shapely | 2.1.2 |
| numpy | 2.5.0 |
| pyproj | 3.7.2 |
| notebook | 7.6.0 |

**4. Lancer Jupyter Notebook**

```bash
jupyter notebook devoir1_ETE435.ipynb
```

**5. Exécuter le notebook**

Dans Jupyter : `Kernel → Restart & Run All`

Le notebook lira automatiquement `ETE_435_Donnees_Devoir_1_H26 (1).csv` (fourni dans le dépôt) et produira :

- `airports_clean.csv` — données nettoyées
- `large_airports_canada.geojson` — fichier GeoJSON des grands aéroports

---

## Résultats obtenus

- **Données initiales** : 1 242 lignes brutes
- **Après nettoyage** : 356 aéroports valides (coordonnées vérifiées)
- **Anomalies corrigées** : valeurs textuelles dans les colonnes numériques (`"ETE435"`, `"CEL15"`), latitude impossible (92,57°)
- **Validation Haversine** : CYYZ → CYVR = **3 345,66 km** (±0,1 % vs géodésique réelle)
- **Grands aéroports** : 24 aéroports de type `large_airport` au Canada
- **Plus éloigné de CYUL** : CYXY (Whitehorse, YT) à **4 242,43 km**

---

## Auteurs

Groupe Érudit — ETE435 Géoinformatique, Été 2026  
Université du Québec
