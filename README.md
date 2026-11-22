# Resilient, Recovered, or Vulnerable? Enrollment Trajectories at U.S. Four-Year Institutions (2018–2024)

Code and data for the DSC 680 capstone project (MS in Data Science, Utica University) by Yangchun Ma.

## Project summary
This project asks whether Fall 2018 institutional characteristics can classify which U.S. four-year public and private nonprofit institutions became resilient, recovered, or vulnerable in enrollment between Fall 2018 and Fall 2024, including those that closed or merged. It compares multinomial logistic regression and random forest models with a baseline, using repeated stratified cross-validation, and examines which groups of characteristics carry the signal, whether this differs by sector, and whether private nonprofit institutions that exited shared a distinct 2018 profile.

## Repository contents
| Path | Description |
|---|---|
| `notebooks/01_data_preparation.ipynb` | Data preparation: reads the Scorecard and IPEDS files, applies the sample filters, combines campuses by OPEID6, builds the enrollment index and labels, and verifies exits |
| `notebooks/02_EDA.ipynb` | Exploratory data analysis, noise check, and selection of the five exit-model predictors |
| `notebooks/03_Models.ipynb` | Models, permutation importance, remove-and-refit, odds ratios, sector models, sensitivity check, exit models, and SHAP |
| `data/institutions.csv` | Analysis file (1,608 institutions, 54 columns) produced by notebook 01 |
| `data/exit_events_verified.csv` | Closures and mergers effective by Fall 2024, verified by hand with at least two sources |
| `data/trend_extremes_checked.csv` | Manual checks of extreme pre-2018 enrollment changes |
| `data/metadata_table.xlsx` | Variable definitions, sources, units, and levels |
| `requirements.txt` | Python package versions used in the analysis |

## Data sources
- U.S. Department of Education. College Scorecard data: yearly institution files 2018-19 to 2024-25, the 2013-14 file, and the Most Recent Cohort file. https://collegescorecard.ed.gov/data/
- National Center for Education Statistics. IPEDS 2018 directory information (HD2018). https://nces.ed.gov/ipeds/datacenter/DataFiles.aspx

The raw files are public and large, so they are not included here. To rerun notebook 01, download them from the links above and update the file paths in that notebook.

## How to run
1. Open a notebook in Google Colab (File → Open notebook → GitHub, then enter `ycma-data/DSC-680-Capstone`).
2. Notebooks 02 and 03 load `data/institutions.csv` directly from this repository, so they run without notebook 01.
3. Run the cells in order. Notebook 03 takes about [X] minutes with the full settings (10 repeats of 5-fold cross-validation). For a quick test, set `N_REPEATS = 2` and `TUNE = False` in its setup cell.
4. To run locally instead of Colab: `pip install -r requirements.txt`.

## Notes on use
The models describe patterns across groups of institutions. They are not designed to score, rank, or predict the future of any individual institution, and this repository does not report individual risk scores.

## Citation
Ma, Y. (2026). *Resilient, recovered, or vulnerable? A machine learning approach to enrollment trajectories at U.S. four-year institutions (2018–2024)* [Source code]. GitHub. https://github.com/ycma-data/DSC-680-Capstone
