# PerceptEarth

**Global layers of human urban perception derived from AlphaEarth Foundation satellite embeddings**

PerceptEarth is an open research pipeline for generating global, perception-informed urban layers from satellite foundation model embeddings. The project links human urban perception data, initially derived from the Place Pulse dataset, with AlphaEarth Foundation satellite embedding representations to model how people perceive urban environments across dimensions such as beauty, safety, liveliness, pleasantness, and related perceptual qualities.

The goal is to make it possible to study human perception of urban environments at global scale, especially in places where street-level imagery, human rating campaigns, or local perception surveys are unavailable. Instead of treating perception as a purely local or image-specific attribute, PerceptEarth explores whether remotely sensed contextual features can approximate broader patterns of human visual perception and produce globally consistent raster layers for urban analysis.

> This repository is currently under preparation. Models, data links, documentation, and reproducible code will be added progressively.

---

## What will be released here?

This repository will host the public-facing materials for PerceptEarth, including:

- trained model files for predicting urban perception indices from AlphaEarth satellite embeddings;
- reproducible code for feature extraction, neighbourhood-context construction, model training, validation, and raster prediction;
- documentation for each released perception layer;
- links to yearly global raster outputs;
- metadata describing spatial resolution, coverage, model version, perception dimension, and validation strategy;
- example notebooks for using the layers in urban analytics, environmental exposure studies, and comparative regional research.

---

## Planned data products

PerceptEarth will provide annual global raster layers for urban population centres with **50,000 inhabitants or more**. Each layer will represent a model-derived, relative perception index. The first planned products include:

| Layer | Description | Status |
|---|---|---|
| Beauty | Predicted relative perception of urban beauty | Coming soon |
| Safety | Predicted relative perception of urban safety | Coming soon |
| Liveliness | Predicted relative perception of urban liveliness | Coming soon |
| Pleasantness | Composite layer combining positively oriented perception dimensions | Coming soon |
| Additional dimensions | Other perception dimensions derived from available human comparison data | Under evaluation |


---

## Planned yearly data links

Data links will be added here as releases become available.

| Year | Global raster layers | Metadata | Status |
|---|---|---|---|
| 2017 | Link coming soon | Link coming soon | Planned |
| 2018 | Link coming soon | Link coming soon | Planned |
| 2019 | Link coming soon | Link coming soon | Planned |
| 2020 | Link coming soon | Link coming soon | Planned |
| 2021 | Link coming soon | Link coming soon | Planned |
| 2022 | Link coming soon | Link coming soon | Planned |
| 2023 | Link coming soon | Link coming soon | Planned |
| 2024 | Link coming soon | Link coming soon | Planned |

The final year range may change depending on AlphaEarth data availability, model validation, and quality checks.

---

## Methodological overview

The PerceptEarth workflow has five main stages.

### 1. Human perception scoring

The project starts from human pairwise comparisons of street-level scenes. These comparisons are not treated as direct ratings. Instead, a ranking-based model is used to infer relative latent perception scores for geolocated images. The resulting scores are normalized to a 0 to 10 index for modelling and interpretation.

### 2. Satellite embedding extraction

For each geolocated image, AlphaEarth Foundation satellite embeddings are extracted at the corresponding location. These embeddings encode multispectral and spatial information about the built and natural environment.

### 3. Multi-scale context descriptors

Because human perception is shaped by surrounding urban context rather than by a single pixel, PerceptEarth expands the representation around each location. For multiple neighbourhood radii, the pipeline computes distance-decayed weighted statistics of embedding dimensions, including means and standard deviations. Nearby areas receive stronger weights than distant areas.

### 4. Prediction modelling and validation

Gradient boosting regression models are trained to predict normalized perception indices from AlphaEarth-derived context descriptors. Validation emphasizes spatial generalization, including city-level or region-level holdout strategies to reduce spatial leakage and test transfer to unseen urban contexts.

### 5. Global layer generation

The trained models are applied to AlphaEarth embeddings for global urban population centres. The output is a set of continuous raster layers representing predicted perception indices across urban areas worldwide.

---

## Repository structure

The repository structure will be expanded as the project develops. A planned structure is shown below.

```text
perceptearth/
├── README.md
├── LICENSE
├── CITATION.cff
├── docs/
│   ├── data_dictionary.md
│   ├── model_cards/
│   └── layer_metadata/
├── notebooks/
│   ├── 01_extract_place_pulse_scores.ipynb
│   ├── 02_extract_alphaearth_embeddings.ipynb
│   ├── 03_build_context_descriptors.ipynb
│   ├── 04_train_models.ipynb
│   ├── 05_validate_spatial_transfer.ipynb
│   └── 06_apply_models_to_global_centres.ipynb
├── src/
│   └── perceptearth/
├── models/
│   └── coming_soon.txt
├── data_links/
│   └── yearly_layers.md
└── examples/
    └── coming_soon.md
```

---

## Example use cases

PerceptEarth layers are intended to support research on:

- comparative urban attractiveness;
- environmental exposure and perceived urban quality;
- equity in access to pleasant, safe, and lively urban environments;
- urban form and human perception at continental or global scale;
- climate-sensitive urban analytics;
- integration of perception-informed covariates into mobility, health, and regional studies.

---

## Important notes

PerceptEarth layers should be interpreted carefully.

- The layers are **model predictions**, not direct measurements of individual opinions.
- The perception indices are **relative**, not absolute universal scores.
- Results may reflect biases in the underlying human comparison data, geographic coverage, satellite embeddings, and model transferability.
- The layers are designed for aggregate research and policy analysis, not for evaluating individual people, households, or private properties.
- All releases will include metadata and validation information to support responsible use.

---

## Citation

A formal citation will be added when the first public release is available.

For now, please cite the project as:

> Malekzadeh, M., Willberg, E., Torkko, J., & Toivonen, T. (forthcoming). *PerceptEarth: Global layers of human urban perception derived from AlphaEarth Foundation satellite embeddings*.

---

## Authors

**Milad Malekzadeh**  
**Elias Willberg**  
**Jussi Torkko**  
**Tuuli Toivonen**  

Digital Geography Lab  
Department of Geosciences and Geography  
University of Helsinki, Finland

---

## Contact

For questions about the project, please contact:

**Milad Malekzadeh**  
Digital Geography Lab, University of Helsinki  
`milad.malekzadeh@helsinki.fi`

---

## Status

This repository is in active preparation. Public models, data links, and documentation will be added after validation and release checks are complete.
