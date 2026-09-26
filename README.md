# Open Cluster Membership Analysis Using Gaia Data

A Python-based analysis pipeline for identifying and characterizing open-cluster members using Gaia astrometric and photometric data.

The project combines data preprocessing, proper-motion and parallax filtering, Minimum Spanning Tree (MST) analysis, Gaussian Mixture Models (GMM), statistical outlier filtering, and King-profile fitting.

## Overview

This project develops a multi-stage workflow for studying stellar populations and identifying candidate members of an open cluster from Gaia data.

The analysis includes:

- Gaia data preprocessing
- Proper-motion and parallax filtering
- Color–Magnitude Diagram (CMD) analysis
- Minimum Spanning Tree (MST) clustering
- Statistical outlier rejection
- Gaussian Mixture Model (GMM) clustering
- Membership probability analysis
- Spatial and proper-motion distributions
- King density-profile fitting
- Core and tidal-radius estimation
- Comparison with previously reported cluster members

## Data

The analysis uses astrometric and photometric parameters from the Gaia catalog, including:

- Right Ascension (RA)
- Declination (Dec)
- Parallax
- Proper motion in RA (`pmra`)
- Proper motion in Dec (`pmdec`)
- Gaia G magnitude
- BP-RP color
- BP-G and G-RP colors
- Astrometric uncertainties
- Gaia stellar parameters

The workflow is demonstrated for some open clusters.

## Analysis Pipeline

### 1. Gaia Data Preprocessing

The initial Gaia catalog is cleaned by removing unnecessary columns and entries with missing values.

Initial quality filtering includes:

- Positive parallax
- Parallax uncertainty threshold
- Proper-motion constraints
- Parallax constraints

The resulting dataset is visualized using color–magnitude diagrams.

### 2. Proper-Motion and Parallax Filtering

Stars are initially selected according to their proximity to the characteristic proper motion and parallax of the target cluster.

The filtering is performed using:

- `pmra`
- `pmdec`
- Parallax

This step reduces the initial Gaia field population before applying clustering methods.

### 3. Minimum Spanning Tree (MST)

A Minimum Spanning Tree is constructed in standardized astrometric parameter space.

The MST analysis uses:

- Right Ascension
- Declination
- Parallax

The data are standardized before constructing the nearest-neighbor graph and minimum spanning tree.

The MST edge-weight distribution is used to determine a filtering threshold and separate the main spatial/astrometric population from additional sources.

### 4. Statistical Outlier Filtering

After MST filtering, additional statistical filtering is applied.

The following parameters are standardized:

- Parallax
- RA
- Dec
- Proper motion in RA
- Proper motion in Dec

Sources with standardized values beyond the selected threshold are removed as statistical outliers.

### 5. Gaussian Mixture Model

A Gaussian Mixture Model is then applied to the remaining sources.

The clustering parameters include:

- `pmra`
- `pmdec`
- Parallax
- RA
- Dec

The GMM provides:

- Cluster assignments
- Membership probabilities

The resulting populations are visualized in:

- Color–magnitude space
- Spatial coordinates
- Proper-motion space
- Parallax-related parameter spaces

### 6. Membership Probability

The GMM probability is used to identify higher-confidence candidate members.

Different probability thresholds can be applied to investigate the resulting member population.

### 7. King Density Profile

The spatial distribution of the selected cluster population is analyzed using a King-type density profile.

The fitted parameters include:

- Background density
- Central density
- Core radius

A tidal-radius estimate is also calculated from the fitted parameters and covariance matrix.

The resulting density profile is used to characterize the spatial structure of the selected stellar population.

### 8. Cluster Properties

The analysis calculates mean cluster properties from the selected members, including:

- Mean RA
- Mean Dec
- Mean proper motion in RA
- Mean proper motion in Dec
- Mean parallax
- Mean astrometric uncertainties

These quantities are stored for comparison and further analysis.


## Comparison with Previous Catalogs

The selected NGC 2244 members are compared with two external membership datasets:

- CG catalog
- Hunt catalog

The comparison includes color–magnitude diagrams and the number of identified members.


## Visualizations

The project generates several astronomical diagnostic plots, including:

- Gaia Color–Magnitude Diagrams
- Proper-motion distributions
- Spatial RA–Dec distributions
- Parallax distributions
- MST edge-weight distributions
- GMM cluster distributions
- KDE plots
- Black-body-related color diagrams
- King density profiles
- Field vs. cluster comparisons
- Comparison with previously reported cluster members

## Methods and Libraries

The project uses:

- Python
- NumPy
- Pandas
- SciPy
- Matplotlib
- Seaborn
- Astropy
- scikit-learn
- NetworkX
- SciencePlots

Main methods include:

- Gaia catalog analysis
- Nearest-neighbor analysis
- Minimum Spanning Tree
- Gaussian Mixture Models
- Statistical filtering
- Nonlinear curve fitting
- King-profile fitting
- Astronomical coordinate transformations
