# sprint-overrun-prediction

Replication package for sprint-overrun classification study (random vs. chronological split, threshold calibration strategy) 
The protocol influences reported ML model performance in predicting sprint-overrun risk in Agile project management.

This repository contains the code, processed data, and results supporting the paper: **From Permissive to Rigorous: The Impact of Evaluation Protocol on Machine Learning Performance in Agile Sprint Overrun Classification**.

Seven ML models (Random Forest, XGBoost, Gradient Boosting, AdaBoost, Decision Tree, Logistic Regression, MLP) are evaluated under three protocols of increasing rigour:

  - Protocol A (permissive): random split, threshold calibrated on the test set
  - Protocol B (intermediate): random split, threshold calibrated via out-of-fold (OOF) predictions on the training set
  - Protocol C (rigorous): chronological split, OOF-calibrated threshold

This study uses the **AgES dataset** (Shankar et al., 2026), publicly available at:
    - GitHub: https://github.com/shankasp/AgES
    - Zenodo: https://doi.org/10.5281/zenodo.14759545

**Repository structure**


```
project_directory/
├── Datasets/
│   └── df_final.csv
│   └── table_repository.counts.csv
├── notebooks/
│   └── 01_data_preparation.py
│   └── 02_chronological_split_and_benchmark.py
│   └── 02_random_split_and_benchmark.py
│   └── 03_chronological_optimization.py
│   └── 03_random_optimization.py
│   └── 03_random_oof_threshold.py
│   └── 04_chronological_statistical_testing.py
│   └── 04_random_statistical_testing.py
│   └── 05_cross_project_split.py
│   └── 06_protocol_comparison.py
├── Results/

```

**Reproducing the results**

Notebooks are numbered in the order they should be executed. Each notebook reads only from its designated input folder(s) and writes only to its own output folder, so re-running any single notebook does not affect the outputs of others.

All notebooks were originally run in Google Colab. File paths reference Google Drive by default; adjust the `PROJECT` variable at the top of each notebook if running locally.
