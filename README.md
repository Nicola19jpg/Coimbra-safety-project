# Road Safety project - Coimbra

This project focuses on the analysis of urban accidents within the municipality of Coimbra. In particular, for the period 2019–2024, the critical points of the city network and the accident accumulation areas were analyzed, year by year.

##  Objectives
The objective of this project is to identify and visualize road safety critical areas in the city of Coimbra by analyzing traffic accident data from 2019 to 2024, by using python language code.
The analysis focuses on detecting spatial concentrations of accidents and highlighting areas with higher cumulative severity.

### What the code does
This project identifies two types of spatial patterns:

- **Pontos Negros (Black Spots)**  
  Localized areas (200m radius) where traffic accidents are spatially concentrated and present a high cumulative severity index (>20).

- **Accumulation Areas**  
  Larger zones (300m radius) where accidents are distributed over a wider area but still show significant spatial density (>=15).

The code processes georeferenced accident data, applies clustering algorithms, filters clusters based on severity thresholds, and produces **interactive maps** to explore the results.


### Methodology
- Accident coordinates (latitude and longitude) are converted into spatial objects.
- Data are projected into a metric coordinate reference system to allow distance-based clustering.
- Clustering algorithms are applied to group nearby accidents.
- Clusters are filtered based on cumulative severity indicators.
- Results are visualized through interactive Folium maps with popup about accidents info.

---

### Clustering Methods

#### DBSCAN
DBSCAN (Density-Based Spatial Clustering of Applications with Noise)  groups data that are closely located within a fixed distance (eps) and a minimum number of points.All the points that don't belong to any cluster are grouped in the Noise cluster (-1), meaning they are discarded from the cluster list
- Strength: effective for identifying compact and well-defined clusters.
- Limitation: sensitive to the *chaining effect*, where clusters may grow by linking points through intermediate distances, event though they overcome the fixed distance.

#### HDBSCAN

It extends DBSCAN by allowing variable density (excess of mass concept) within a cluster and automatically identifying as noise point the ones that aren't located in *excess of mass zone*.

- Strength: better handling of heterogeneous spatial densities.
- Limitation: cluster interpretation depends on parameter choices and may produce less intuitive boundaries.

---

### Challenges and Improvements
- Managing the chaining effect in DBSCAN.
- Interpreting HDBSCAN results and cluster reliability.
- Comparing clustering results with HDBSCAN and DBSCAN methods.

Possible future improvements include:

- Integration of frequency distribution.
- Comparison with additional spatial analysis techniques.

---

##  **Repository Structure**

* `data/`: Folder containing input datasets and processed data.
* `template accumulation areas`: Template for accumulation area analysis.
* `template pontos negros`: Template for black spot analysis.
* `requirements.txt`: List of required Python dependencies.

## Installation

### Requirements
All required Python libraries are listed in the `requirements.txt` file.

### Setup
```bash
pip install -r requirements.txt


