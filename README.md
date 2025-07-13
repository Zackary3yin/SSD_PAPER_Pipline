# SSD\_PAPER\_Pipline

This repository contains the full analysis pipeline for the SSD-based EEG trajectory study. All code and procedures are organized in a single Jupyter notebook: **`Whole pipline github.ipynb`**, which should be executed sequentially from top to bottom.

## 🔍 Outline of the Pipeline

The full workflow is divided into **three main parts**:

---

### 1. Spike Frequency Analysis

* Analyzes dynamic evolution of **spike frequency** (derived from SSD annotations).
* Includes statistical summaries and visualizations of spike rate distributions over time and outcomes.
* Input data is derived from preprocessed SSD spike files.

### 2. Multiple Features Clustering Analysis

* Performs clustering on selected EEG features (e.g., BCI, entropy, amplitude, skewness).
* Uses dimensionality reduction, DTW-based k-means, and visualization of temporal trajectories.
* Helps identify patient subgroups with shared EEG patterns.

### 3. Deep Learning Analysis

* Applies LSTM models to predict CPC outcomes and cluster assignments over time.
* Evaluates per-hour prediction performance and temporal dynamics.
* Compares different labeling strategies (CPC vs. unsupervised clusters).

---

## 📁 Data Sources

All datasets are derived from two large-scale feature directories on Wynton HPC:

* EEG Feature Directory:

  ```
  /wynton/group/amorim/ICARE_new_features/new_icare_features_new
  ```
* SSD Spike Frequency Directory:

  ```
  /wynton/group/amorim/CDACEEG_Arrest_Pravin/vk_R_wave_in_SSD_spike_freq_loc/Spike_freq
  ```

These raw directories are **too large to be stored in the repository**. If you have Wynton access, you can retrieve the necessary files from those locations.

---

## 📦 Preprocessed Datasets

This repo includes two cleaned datasets ready for analysis:

| File Name                      | Used In Parts | Description                                            |
| ------------------------------ | ------------- | ------------------------------------------------------ |
| `all_feature_data_6-84.csv`    | Parts 1 & 2   | EEG feature matrix (6–84h window), spike & cluster use |
| `all_feature_data-16start.csv` | Part 3        | EEG features aligned to 16h post-ROSC for LSTM input   |

These datasets are sufficient for reproducing all figures and results in the notebook.

---

---

## ⚠️ Notes on Data Extraction Cells

To avoid unintended large-scale processing, the notebook’s three code cells responsible for **generating datasets from raw feature directories** have been converted into **markdown cells**.

If you wish to regenerate the datasets from scratch, you can:

1. Change the corresponding markdown blocks back to code.
2. Ensure you have access to Wynton and the full feature directories mentioned above.

---
