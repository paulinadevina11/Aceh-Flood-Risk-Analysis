# End-to-End Data Science Analysis of Flood Risk in Aceh Province
### From Raw Environmental Data to Data-Driven Disaster Mitigation Using Machine Learning

The floods that struck Aceh Province in the last December 2025 resulted in severe social, economic, and environmental impacts across multiple districts.Public discourse often frames such disasters as a direct consequence of extreme rainfall alone. This project challenges that assumption by applying a rigorous end-to-end Data Science pipeline to uncover deeper structural drivers of flood severity. By integrating heterogeneous environmental, demographic, and impact datasets, this study aims to statistically isolate the root contributors to flood-related fatalities and provide a data-driven framework for disaster risk mitigation.

## Technical Methodology
This repository demonstrates a complete, reproducible data engineering and machine learning workflow, from raw data ingestion to actionable insights.
### 1. Data Engineering & Aggregation
Multidimensional datasets from diverse sources were integrated at the district (kabupaten) level, such as:
- Geospatial Data: Tree Cover Loss / Deforestation (Global Forest Watch, 2001-2024)
- Meteorogical Data: Historical rainfall intensity (Badan Pusat Statistik Aceh, 2017-2019)
- Topographical Data: Average land slope per district to estimate surface runoff potential (Dokumen RTRW & BPS Kabupaten (Aceh Besar, Aceh Tenggara, Aceh Tamiang, et al.), "Data Kemiringan Lahan dan Topografi."
- Demographic and Impact Data: Population density and flood casualty statistics (BNPB, December 2025 event)
#### Techniques Applied:
- Data cleaning and standardization of administrative boundaries
- Handling missing values
- Feature scaling using StandardScaler to normalize heterogeneous units (hectares, percentages, population density)

### 2. Exploratory Data Analysis (EDA)
Statistical profiling revealed a critical insight:
- Although high rainfall intensity is relatively uniform across Aceh, flood-related fatalities are highly uneven across districts.
- Correlation analysis shows a strong positive linear relationship between cumulative deforestation and casualty counts.
- Environmental degradation emerged as a stronger predictor of disaster severity than rainfall alone.

This finding challenges the dominant rainfall-centric narrative and highlights the role of land-use change in amplifying flood risk.

### 3. Machine Learning Implementation (Unsupervised Clustering)
To move beyond descriptive statistics, this project employs Unsupervised Machine Learning using the K-Means clustering algorithm. Belo is the objective:
Segment the 23 districts of Aceh into objective Flood Risk Zones based on shared environmental and socio-demographic characteristics.

Result:
The model successfully identified a distinct High-Risk Cluster (Red Zone), primarily consisting of:
- Aceh Utara
- Aceh Timur

These districts exhibit a dangerous combination of:
- Extreme cumulative deforestation (>15,000 Ha)
- Vulnerable topography with high runoff potential
- High human exposure

## Actionable Insights & Policy Relevance
This project serves as a prototype for a Disaster Decision Support System (DSS).
Rather than relying on reactive emergency response, the results enable proactive, targeted mitigation strategies, including:
- Prioritizing reforestation and watershed rehabilitation
- Strengthening flood control infrastructure (dykes, drainage systems)
- Implementing “Triage Mitigation”, where resources are allocated first to statistically identified Red Zone districts. 

By grounding disaster mitigation in data, this framework supports evidence-based policymaking and more efficient allocation of limited public resources.

## 📘 How to Read This Repository (Important)
This project is structured as a step-by-step data science pipeline, where each Jupyter Notebook represents one analytical stage.
⚠️ Please read and execute the notebooks in order, as later notebooks depend on outputs generated earlier.

📂 Notebook Execution Flow
- (1)Curah_Hujan.ipynb = Processes historical rainfall data to understand precipitation patterns across districts.

- (2)Deforestasi.ipynb = Analyzes cumulative tree cover loss (deforestation) using Global Forest Watch data.

- (3)Kemiringan_Lahan.ipynb = Computes average land slope per district to assess runoff and flood acceleration risk.

- (4)Kepadatan_Penduduk.ipynb = Processes population density data as a human exposure indicator.

- (5)Analisis_Dampak.ipynb = Analyzes flood impacts, including casualty statistics and socio-economic effects.

- Aggregate.ipynb = This notebook merges all processed datasets (rainfall, deforestation, slope, population density, and impact data) into a single master dataset used for modeling. It also performs final data cleaning, feature alignment by district, and preparation of machine-learning-ready tables. 

- (6)Clustering.ipynb = Applies K-Means clustering on the aggregated dataset to classify districts into flood-risk zones.

## ⚠️ Important Reminder = Do not skip Aggregate.ipynb

Running Clustering.ipynb without executing previous notebooks will result in undefined variables or missing features

Notebook numbering reflects the logical data flow, not just file order
