# Road Safety project -  Coimbra

Questo progetto riguarda l'analisi sulla incidentalitá urbana per il comune di Coimbra. In particolare, per il periodo 2019-2024 sono stati analizzati i punti critici della rete cittadina e le area di accumulazione di incidenti, anno per anno.

##  Obiettivi del Progetto
L'obiettivo è fornire uno strumento analitico che identifichi i "punti neri" della rete stradale e le "aree di accumulazione di incidenti" aumentando rapidita di esecuziona ma senza perdere efficacia

## 📁 Struttura dell'Analisi (Capitoli)

### 1. Pre-processing e Calcolo della Gravità
I dati grezzi dell'incidentalità sono stati filtrati e arricchiti. È stato implementato un **Indice di Gravità Ponderato** per classificare il rischio reale di ogni incidente:
- **Morti:** peso 10
- **Feriti Gravi:** peso 5
- **Feriti Lievi:** peso 3

### 2. Clustering Spaziale (DBSCAN)
Per identificare scientificamente gli **Hotspot** (zone ad alta densità di incidenti), è stato utilizzato l'algoritmo **DBSCAN** (*Density-Based Spatial Clustering of Applications with Noise*) o il suo "cugino" **HDBSCAN**
- **Metodologia:** Utilizzo della distanza di *Haversine* per gestire coordinate sferiche.
- **Risultato:** Identificazione dei cluster principali che rappresentano le aree di intervento prioritario, escludendo il rumore statistico (incidenti isolati).


## 🛠️ Stack Tecnologico
- **Python** (Pandas, Numpy)
- **Scikit-Learn** (DBSCAN)
- **Geospatial Tools** (OSMnx, NetworkX, Geopandas, Shapely)
- **Visualization** (Folium, Matplotlib)

## 🔧 Installazione
```bash
!pip install folium geopandas scikit-learn hdbscan --quiet


##  **Struttura del Repository**

* `data/`: Cartella contenente i dataset di input e i dati elaborati.
* `template accumulation areas`: Template per l'analisi delle aree di accumulo.
* `template pontos negros`: Template per l'analisi dei punti neri .
* `requirements.txt`: Elenco delle dipendenze Python necessarie.

##  Requisiti e Installazione

Assicurati di avere Python installato. Per installare tutte le librerie necessarie, esegui:

```bash
pip install -r requirements.txt

# Road Safety Hotspots Detection – Coimbra (2019–2024)

## Objective
The objective of this project is to identify and visualize road safety critical areas in the city of Coimbra by analyzing traffic accident data from 2019 to 2024.  
The analysis focuses on detecting spatial concentrations of accidents and highlighting areas with higher cumulative severity.

---

## Description

### What the code does
This project identifies two types of spatial patterns:

- **Pontos Negros (Black Spots)**  
  Localized areas where traffic accidents are spatially concentrated and present a high cumulative severity index.

- **Accumulation Areas**  
  Larger zones where accidents are distributed over a wider area but still show significant spatial density and risk.

The code processes georeferenced accident data, applies clustering algorithms, filters clusters based on severity thresholds, and produces **interactive maps** to explore the results.

---

### Methodology
- Accident coordinates (latitude and longitude) are converted into spatial objects.
- Data are projected into a metric coordinate reference system to allow distance-based clustering.
- Clustering algorithms are applied to group nearby accidents.
- Clusters are filtered based on cumulative severity indicators.
- Results are visualized through interactive Folium maps with popup info about accidents.

---

### Technologies and Algorithms

#### DBSCAN
DBSCAN is used to detect **Pontos Negros**.  
It groups accidents that are closely located within a fixed distance (eps) and a minimum number of points.

- Strength: effective for identifying compact and well-defined clusters.
- Limitation: sensitive to the *chaining effect*, where clusters may grow by linking points through intermediate distances.

#### HDBSCAN
HDBSCAN is used to detect **Accumulation Areas**.  
It extends DBSCAN by allowing variable density clusters and automatically identifying noise.

- Strength: better handling of heterogeneous spatial densities.
- Limitation: cluster interpretation depends on parameter choices and may produce less intuitive boundaries.

---

### Challenges and Improvements
- Managing the chaining effect in DBSCAN.
- Interpreting HDBSCAN results and cluster reliability.
- Ensuring spatial consistency across different years.

Possible future improvements include:
- Sensitivity analysis of clustering parameters.
- Integration of frequency distributio.
- Comparison with additional spatial analysis techniques.

---

## Installation

### Requirements
All required Python libraries are listed in the `requirements.txt` file.

### Setup
```bash
pip install -r requirements.txt


