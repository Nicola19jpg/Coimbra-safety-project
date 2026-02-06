# 📊 Analisi Integrata della Sicurezza e Mobilità Urbana - Coimbra
### Data Science applicata all'incidentalità stradale e all'accessibilità

Questo progetto accademico presenta un'analisi geospaziale avanzata della città di Coimbra (Portogallo), unendo lo studio statistico degli incidenti stradali con la modellazione dinamica della rete viaria.

## 🚀 Obiettivi del Progetto
L'obiettivo è fornire uno strumento analitico che identifichi i "punti neri" della città e valuti l'efficienza dei soccorsi e della mobilità attraverso la teoria dei grafi e algoritmi di Machine Learning.

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

### 3. Modellazione della Rete Stradale (OSMnx)
Utilizzando la libreria `OSMnx`, la città di Coimbra è stata trasformata in un **Grafo Orientato**.
- **Topologia:** Il modello rispetta i sensi unici di marcia e i limiti di velocità.
- **Edge Speeds:** Assegnazione delle velocità medie per trasformare la distanza fisica in tempi di percorrenza reali.

### 4. Analisi delle Isocrone
Generazione di poligoni di accessibilità basati sul tempo (5, 10, 15 minuti) partendo da nodi strategici.
- **Algoritmo di Dijkstra:** Utilizzato per trovare il cammino minimo sul grafo.
- **Geometria:** Utilizzo del *Convex Hull* per definire i confini delle aree raggiungibili entro la soglia temporale impostata.

### 5. Visualizzazione Interattiva (Folium)
Integrazione di tutti i layer informativi su mappe interattive:
- **HeatMap:** Per la densità visiva degli incidenti.
- **Marker Clusters:** Per l'esplorazione granulare dei dati.
- **Isochrone Layers:** Poligoni colorati sfumati per l'analisi dell'accessibilità.

## 🛠️ Stack Tecnologico
- **Python** (Pandas, Numpy)
- **Scikit-Learn** (DBSCAN)
- **Geospatial Tools** (OSMnx, NetworkX, Geopandas, Shapely)
- **Visualization** (Folium, Matplotlib)

## 🔧 Installazione
```bash
pip install osmnx folium streamlit-folium scikit-learn geopandas
