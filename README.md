# Occupancy and N-mixture models for Gilded Sapphire hummingbirds

This repository contains an R Markdown project designed for analyzing ecological data related to Gilded Sapphire hummingbird populations. It employs both **Occupancy Models** (using the `unmarked` package) and **N-mixture Models** (using Bayesian inference with `R2jags`) to estimate population parameters while accounting for imperfect detection.

## Table of Contents

* [Project Overview](#project-overview)

* [Features](#features)

* [Models Implemented](#models-implemented)

* [Output Files](#output-files)

* [Contributing](#contributing)

* [License](#license)

## Project Overview

The core of this project is an R Markdown (`.Rmd`) file that integrates R code, statistical output, and explanatory text. It focuses on:

* **Occupancy Modeling:** Estimating the probability that a species occupies a site and the dynamics of colonization and extinction across multiple seasons.

* **N-mixture Modeling:** Estimating the absolute abundance of individuals at sites, accounting for the fact that not all individuals present are detected.

* **Covariate Effects:** Investigating how environmental variables (e.g., time of day, flower abundance, habitat type) influence detection probabilities, colonization, extinction, and abundance.

* **Model Selection:** Using AICc (for `unmarked` models) and DIC (for `R2jags` models) to compare and select the best-fitting models.

## Features

* **Multi-season Occupancy Analysis:** Implements `colext` models for dynamic occupancy estimation.

* **Bayesian N-mixture Models:** Utilizes `R2jags` for flexible Bayesian modeling of abundance.

* **Data Preparation Pipelines:** Demonstrates `dplyr` and `tidyr` for efficient data manipulation.

* **Model Comparison:** Provides AIC and DIC comparisons for model selection.

* **Visualization:** Generates informative plots (e.g., detection probability curves, seasonal abundance trends) using `ggplot2`.

* **Reproducible Workflow:** All analysis steps are contained within a single `.Rmd` file, promoting reproducibility.

* ## Models Implemented

### Occupancy Models (`unmarked`)

* **Null Model (fm0):** Constant psi, gamma, epsilon, p.

* **Time Model (fm1):** Detection (p) depends on `hour` and `flower_abun`.

* **Habitat Model (fm2):** Colonization (gamma) and Extinction (epsilon) depend on `habitat_type`.

* **Flower Model (fm3):** Colonization (gamma) and Extinction (epsilon) depend on `mean_flower_abundance`.

### N-mixture Models (`R2jags`)

* **Null Model (fm0_jags):** Constant lambda, phi, gamma, p.

* **Time Model (fm1_jags):** Detection (p) depends on `hour` and `flower_abun`.

* **Habitat Model (fm2_jags):** Colonization (gamma) and Survival (phi) depend on `habitat_type`.

* **Flower Abundance Model (fm3_jags):** Colonization (gamma) and Survival (phi) depend on `mean_flower_abundance`.

## Output Files

Upon knitting the `.Rmd` file, the following output files may be generated:

* `Occupancy and N-mixture models Gilded sapphire.html` (or `.pdf`, `.docx` depending on output format)

* `aicTable_occupancy.csv`: AIC table for the `unmarked` models.

* `fit_fmX_nmixture_summary.csv`: Summary statistics for the N-mixture models (e.g., `fit_fm0_nmixture_summary.csv`).

* `posterior_samples_fmX_nmixture.rds`: Saved posterior samples from the N-mixture models (e.g., `posterior_samples_fm0_nmixture.rds`).

* Plots (if `ggsave` commands are uncommented and `eval=TRUE`):

  * `detection_hour_plot.png`

  * `detection_flower_plot.png`

  * `seasonal_abundance_plot.png`

## Contributing

Contributions are welcome! If you have suggestions for improvements, bug fixes, or new features, please open an issue or submit a pull request.

## License

This project is open-source and available under the [MIT License](LICENSE).
