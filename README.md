# Ecological-integration-hypotheses-as-an-overlooked-source-of-predictive-uncertainty-
We present a hierarchical framework that explicitly treats alternative integration operators as competing ecological hypotheses. 
Software environment
All analyses were conducted in R version 4.6.0 (R Core Team, 2026). The workflow was implemented as a modular collection of scripts, each responsible for a single component of the modelling framework. This structure allows each stage of the analysis to be reproduced independently while preserving complete reproducibility of the integrated workflow.
The principal R packages used include:
Package	Purpose
terra	raster processing, NetCDF handling, climate data processing
ggplot2	figure generation
dplyr	data manipulation
tidyr	data reshaping
minpack.lm	nonlinear least-squares fitting
MASS	statistical procedures and uncertainty analysis
Additional packages required for model evaluation and spatial analyses are loaded within the corresponding scripts.
R/
│
├── 00_run_model.R
│
├── 01_parameters.R
├── 02_development.R
├── 03_mortality.R
├── 04_fecundity.R
├── 05_persistence.R
├── 06_uncertainty.R
│
├── 08_figures.R
├── 09_biological_verification.R
│
├── 10_Pathogene_thermalreponses.R
├── 11_ECF_Integration_Pathways.R
│
├── 12_Climate_Data_Download_Preprocessing.R
├── 13_ECF_Daily_Mechanistic_Suitability_Model.R
├── 14_Post-processing_of_Mechanistic_Suitability_Products.R
├── 15_ECF_Spatial_and_Temporal_Visualization.R
└── 16_ECF_Model_Evaluation_Selection_and_Uncertainty_Analysis.R


The master script (00_run_model.R) reproduces the complete vector persistence framework, whereas the remaining scripts implement the climate preprocessing, pathogen persistence model, ecological integration, spatial prediction, visualization, and model evaluation.
Execution workflow
The computational workflow follows the sequence below.
Step	Script	Function
1	00_run_model.R	Master script controlling execution
2	01_parameters.R	Biological parameter definitions
3	02_development.R	Temperature-dependent development models
4	03_mortality.R	Stage-specific mortality models
5	04_fecundity.R	Fecundity model and parameter uncertainty
6	05_persistence.R	Analytical vector persistence model
7	06_uncertainty.R	Monte Carlo uncertainty propagation
8	08_figures.R	Publication-quality figures
9	09_biological_verification.R	Biological consistency checks
10	10_Pathogene_thermalreponses.R	Pathogen thermal response models
11	11_ECF_Integration_Pathways.R	Ecological integration operators
12	12_Climate_Data_Download_Preprocessing.R	Download and preprocessing of daily GDEX climate data
13	13_ECF_Daily_Mechanistic_Suitability_Model.R	Daily mechanistic suitability simulation
14	14_Post-processing_of_Mechanistic_Suitability_Products.R	Derivation of climatologies and summary products
15	15_ECF_Spatial_and_Temporal_Visualization.R	Map production and seasonal visualization
16	16_ECF_Model_Evaluation_Selection_and_Uncertainty_Analysis.R	Quantitative evaluation and uncertainty analysis

Input datasets
The framework requires four categories of input data.
Climate data
•	Daily near-surface air temperature
•	Daily atmospheric pressure
•	Daily specific humidity
obtained from the GDEX archive for 1981–2008.
These variables are converted to
•	Temperature (°C)
•	Relative humidity (%)
before simulation.
Biological parameters
The vector persistence model uses experimentally derived thermal responses describing
•	development,
•	mortality,
•	fecundity,
•	host-finding,
while the pathogen persistence model uses experimentally fitted responses describing
•	parasite maturation,
•	vector-to-host transmission,
•	host-to-vector acquisition.
Occurrence records
Independent occurrence records of Theileria parva were used for model evaluation.

Computational workflow
The complete computational workflow is summarised below.
Daily climate data
          │
          ▼
Temperature
Relative humidity
          │
          ▼
─────────────────────────────────
Vector persistence model
─────────────────────────────────
Development
Mortality
Fecundity
Host finding
          │
          ▼
Vector persistence (RV)

─────────────────────────────────
Pathogen persistence model
─────────────────────────────────
Host acquisition
Parasite maturation
Transmission
          │
          ▼
Pathogen persistence (RP)

          │
          ▼
Ecological integration
(Multiplicative
Arithmetic
Geometric
Limiting
Weighted
Fuzzy)

          │
          ▼
Daily suitability maps

          │
          ▼
Seasonal climatologies

          │
          ▼
Long-term suitability

          │
          ▼
Model evaluation

Generated outputs
Execution of the complete workflow produces the following outputs.
Climate products
•	Daily temperature rasters (°C)
•	Daily relative humidity rasters (%)
Mechanistic products
•	Daily vector persistence (R_V)
•	Daily pathogen persistence (R_P)
•	Daily integrated suitability
Spatial products
•	Long-term mean suitability
•	Monthly climatologies

Reproducibility
The complete analysis can be reproduced by executing the scripts sequentially from 00_run_model.R through 16_ECF_Model_Evaluation_Selection_and_Uncertainty_Analysis.R. Each script performs a single well-defined task and produces standardized outputs that serve as inputs for the subsequent stage. This modular architecture facilitates reproducibility, simplifies maintenance, and allows individual model components to be updated independently without altering the overall analytical framework.
<img width="468" height="638" alt="image" src="https://github.com/user-attachments/assets/c8704129-2dab-43c1-a27a-2cde96990af2" />
