# 🗺️ Coimbra Urban Accessibility & Network Analysis
### Analisi delle Isocrone e Modellazione della Rete Stradale tramite OpenStreetMap

Questo progetto si focalizza sullo studio della **mobilità urbana** nella città di Coimbra (Portogallo). Utilizzando grafi stradali reali e algoritmi di percorso minimo, l'applicazione definisce le aree di accessibilità (isocrone) basate sui tempi di percorrenza effettivi.

## 🚀 Panoramica del Progetto
A differenza delle analisi basate sul raggio d'aria (distanza euclidea), questo studio utilizza la **teoria dei grafi** per modellare la città come una rete complessa. Il progetto permette di visualizzare fin dove è possibile arrivare partendo da un punto centrale (es. Praça da República) in 5, 10 o 15 minuti di guida.

## 🛠️ Stack Tecnologico & Metodologia
Il progetto implementa le seguenti librerie e concetti di **Geospatial Data Science**:

* **OSMnx:** Per il download e la modellazione del grafo stradale (`network_type='drive'`) direttamente da OpenStreetMap.
* **NetworkX:** Per il calcolo del sottografo dei nodi raggiungibili (Ego Graph) tramite l'algoritmo di Dijkstra.
* **Folium:** Per la visualizzazione cartografica interattiva.
* **Geopandas & Shapely:** Per la manipolazione delle geometrie e la creazione del **Convex Hull** (l'area poligonale dell'isocrona).



## 📁 Struttura della Repository
- `/data`: Cartella dedicata ai dataset degli incidenti e della mobilità.
- `app.py`: Il codice dell'applicazione Streamlit che integra l'analisi dinamica.
- `requirements.txt`: Elenco delle dipendenze necessarie per il deploy.

## 🧮 Logica di Calcolo
Il modello non si limita alla distanza, ma analizza la **topologia stradale**:
1.  **Sensi di Marcia:** Il grafo è orientato; se una strada è a senso unico, il calcolo ne tiene conto.
2.  **Velocità e Tempi:** Viene calcolato l'attributo `travel_time` per ogni segmento stradale:
    $$Tempo (s) = \frac{Lunghezza (m)}{Velocità (m/s)}$$
3.  **Generazione Isocrone:** Vengono estratti i nodi raggiungibili entro una soglia temporale e uniti in un poligono convesso sfumato.



## 🔧 Configurazione e Installazione
Per eseguire il progetto localmente:
1. Clonare la repository: `git clone https://github.com/TUO-USERNAME/NOME-REPO.git`
2. Installare le dipendenze: `pip install -r requirements.txt`
3. Eseguire l'app: `streamlit run app.py`

---
*Progetto realizzato per l'esame di Marketing & Customer Analytics.*
