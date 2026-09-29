# SLDM_Country_Segmentation_SOM_KMeans

Unsupervised segmentation of 195 countries using a **Self-Organizing Map (SOM/Kohonen) with
K-Means clustering over the neural weight prototypes.**

## Dataset

`world-data` — 195 countries × 35 attributes (demographics, health, economy, environment,
geography). Preprocessed into 4 derived subsets (median imputation, quantile discretization,
economic and demographic sub-sets).

## Approach

- Cleanse/normalize (missing imputation, count-encoding, MinMax, missing-as-category).
- Train SOM grids (9 configs: 14×14 → 40×10), select best by **Quantization Error** and
  **Topographic Error**.
- K-Means on neuron prototypes; **K=7** chosen via elbow method + Kneedle.
- Interpret clusters via U-Matrix, activation/classification maps, centroid heatmap, world
  choropleth, and per-country distance-to-centroid.

## Results

| Configuration | QE | TE |
|---|---|---|
| Best (40×10, LR 0.10, 200k epochs) | **0.7150** | **0.0000** |
| Economic subset (10 vars) | 0.4217 | 0.0051 |
| Demographic subset (11 vars) | 0.3051 | — |

Outliers detected: Monaco, South Africa, Somalia, Marshall Islands, San Marino, Turkmenistan,
Libya, North Korea.

## Reproduce

`PW1_GROUP_2.ipynb` — the single notebook for the whole practical. Download
`world-data.csv`, open in Jupyter/Colab, run top to bottom.
