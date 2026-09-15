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
├── Notebooks/
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
│   └── Tables/
│       └── table_baseline_per_class.csv
│       └── table_chronological_baseline_full.csv
│       └── table_chronological_final_test_results.csv
│       └── table_chronological_split_info.csv
│       └── table_chronological_wilcoxon.csv
│       └── table_contextual_correlations.csv
│       └── table_cross_project_folds_all_models.csv
│       └── table_feature_ranking_all_protocols.csv
│       └── table_protocol_deltas_all_models.csv
│       └── table_random_OOF_final_test_results.csv
│       └── table_random_OOF_wilcoxon.csv
│       └── table_random_baseline_full.csv
│       └── table_random_final_test_results.csv
│       └── table_random_split_info.csv
│       └── table_random_wilcoxon.csv
│       └── table_within_repo_wilcoxon_all_models.csv
│   └── Figures/
│       └──fig_chronological_confusion_matrix.png
│       └── fig_chronological_feature_importance_top10.png
│       └── fig_feature_rank_bumpchart.png
│       └── fig_random_OOF_confusion_matrix.png
│       └── fig_random_confusion_matrix.png
│       └── fig_random_feature_importance_top10.png
│       └── fig_roc_overlay_all_protocols.png
├── requirements.txt
```

**Reproducing the results**

Notebooks are numbered in the order they should be executed. Each notebook reads only from its designated input folder(s) and writes only to its own output folder, so re-running any single notebook does not affect the outputs of others.

All notebooks were originally run in Google Colab. File paths reference Google Drive by default; adjust the `PROJECT` variable at the top of each notebook if running locally.

All experiments were performed in Google Colab using Python 3.13.15.
See **requirements.txt** for exact package versions.
