# Shapley Supercluster Galaxy Analysis with R

This repository contains an R Markdown analysis of the **Shapley Supercluster (SCl 124)**, the largest galaxy concentration in our local universe. The project applies **Hierarchical** and **K-Means** clustering algorithms to identify and analyze distinct galaxy groupings based on physical and spatial characteristics.


---

## 🌌 About the Shapley Supercluster

The **Shapley Supercluster**, or **Shapley Concentration (SCl 124)**, is the most massive structure in our local universe. It forms a gravitationally bound system instead of expanding with the Hubble flow.

**Key Features:**
- Appears as a significant overdensity in the cosmic distribution of galaxies.
- Located in the **constellation Centaurus**.
- Roughly **650 million light-years** from Earth.
- Essential for understanding **large-scale cosmic structure**.

---

##  Project Goal

This project aims to:

1. Analyze the **physical** and **spatial** attributes of galaxies in the Shapley Supercluster.
2. Apply **unsupervised clustering** techniques — *K-Means* and *Hierarchical (Ward.D2)* — to identify natural groupings.
3. **Visualize** and interpret clustering results within celestial coordinates (RA/Dec).

---

##  The Dataset

The dataset contains five columns for each galaxy:

| Variable | Description                                | Value Range     | Units     |
|----------|--------------------------------------------|-----------------|-----------|
| `R.A.`   | Right Ascension (celestial longitude)      | 0°–360°         | Degrees   |
| `Dec.`   | Declination (celestial latitude)           | -90°–+90°       | Degrees   |
| `Mag`    | Apparent Magnitude (brightness)            | ~10–20          | Magnitude |
| `V`      | Radial Velocity (recessional)              | Positive        | km/s      |
| `SigV`   | Measurement error in velocity (dispersion) | Positive        | km/s      |

**Source**: Kaggle – Shapley Galaxy Dataset

---

##  Analysis Pipeline

### 1. Data Preparation
- Load CSV data.
- Basic exploratory data analysis (EDA).
- Histogram distributions for all features.

### 2. Missing Value Handling
- Remove rows with missing `Mag` values (essential for brightness analysis).

### 3. Hierarchical Clustering
- Standardize data (Z-scores).
- Compute distance matrix (Euclidean).
- Apply `hclust()` with `ward.D2` method.
- Cut dendrogram into **4 clusters**.

### 4. K-Means Clustering
- Determine `k` using **Elbow Method** and **Silhouette Analysis**.
- Run `kmeans()` with `k = 4` on scaled `Mag`, `V`, `SigV`.
- Visualize results in physical and celestial space.

### 5. Method Comparison
- Evaluate alignment using **Confusion Matrix** and **Adjusted Rand Index (ARI)**.
- ARI ≈ `0.658` indicates substantial agreement between methods.

---

##  Key Findings

- **Four Galaxy Groups**: Both clustering methods independently identified 4 distinct groups with differing physical characteristics.
- **Spatial Patterns**: Clusters form recognizable structures in RA/Dec sky maps — not random groupings.
- **Velocity Differentiation**: Clusters differ significantly in average radial velocity, implying real 3D depth structures.
- **Method Comparison**:
  - Hierarchical: Best for structural insight without `k` assumption.
  - K-Means: Fast and effective for physical variable clustering once `k` is known.

