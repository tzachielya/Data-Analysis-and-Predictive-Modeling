# Data Analysis & Predictive Modeling

**An academic team project combining data integration, exploratory analysis, feature engineering, and supervised machine learning to analyze and predict competitive outcomes.**

**Case study:** Eurovision Song Contest results and song-level characteristics (1956–2025).

## Project at a glance

| Dimension | What the project covered |
| --- | --- |
| Objective | Explore measurable factors associated with success and estimate whether an entry finishes in the Top 1, 2, or 3 |
| Dataset | 1,758 entries assembled from multiple sources; approximately 1,400 finalists retained after cleaning for modeling |
| Methods | Data cleaning and merging, exploratory analysis, NLP features, supervised classification, cross-validation, and visualization |
| Models | Logistic Regression (TF-IDF and structured features), Histogram-based Gradient Boosting, and a probability-averaging ensemble |
| Evaluation | Year-grouped five-fold cross-validation; AUROC, average precision, F1, and Hits@K |
| Tools | Python, pandas, scikit-learn, NumPy, SciPy, and data-processing/plotting libraries |

## The problem

Predicting competitive outcomes is difficult when data is spread across sources, identifiers need reconciliation, and outcomes depend on a mix of measurable signals and context. The team built a structured analytical workflow to consolidate datasets, define measurable outcomes, compare approaches, and communicate limitations alongside results.

Eurovision is the **real-world case study**, rather than the headline objective. The transferable skills are **data quality, problem definition, model evaluation, decision-making with evidence, and communication**.

## Methodology

1. **Data integration:** Consolidated results, entry metadata, lyrics-derived attributes, and contextual information; cleaned and reconciled identifiers across sources.
2. **Exploratory analysis:** Examined patterns involving running order, tempo, and past performance; visualized associations without claiming causality.
3. **Feature engineering:** Constructed numeric and categorical features and lyric-text representations using TF-IDF.
4. **Model comparison:** Evaluated regularized Logistic Regression, Histogram-based Gradient Boosting, and a simple probability-averaging ensemble.
5. **Evaluation:** Used five-fold GroupKFold by contest year to assess performance on held-out years and reduce cross-edition leakage.

## Selected cross-validation results

Mean results across five held-out-year folds, from the original saved project artifacts:

| Outcome | Model | Mean AUROC | Mean average precision |
| --- | --- | ---: | ---: |
| Top 1 | HGB | 0.716 | 0.155 |
| Top 2 | Ensemble | 0.754 | 0.330 |
| Top 3 | Ensemble | 0.743 | 0.351 |

The exact-winner task was harder than predicting broader Top-2 or Top-3 outcomes. **These are offline cross-validation scores, not production outcomes or guarantees for future contests.** See [the complete summary](results/cross_validation_summary.json).

## Interactive demo and supporting coursework

### Interactive prediction demo

The team also presented a user-facing **Top-K prediction interface**. The [demo presentation](docs/presentations/Interactive_Prediction_Demo.pdf) describes a **React frontend with a FastAPI backend**, where users can enter song characteristics, select Top-1/Top-2/Top-3 and a model, and view predicted probabilities. It includes a screenshot of the interface.

**Scope note:** The frontend/backend implementation is not part of the curated source files in this repository; the slides document the team's demonstration, not a currently hosted or independently verified production service.

### Local differential privacy presentation

As supporting academic course material, a related presentation covers **Local Differential Privacy (LDP)**: how data can be randomized on a user's device before sharing, balancing privacy and analytical utility. [View the LDP presentation (PDF)](docs/presentations/Local_Differential_Privacy_Presentation.pdf).

**Scope note:** This is an educational presentation associated with the coursework. It is **not a claim that LDP was implemented or integrated into the predictive-model pipeline**.

## Skills illustrated

- **Problem framing:** Translating a broad question into measurable outcomes and evaluation criteria.
- **Analytical decision-making:** Comparing model alternatives and accounting for uncertainty and trade-offs.
- **Team collaboration:** Coordinating an academic team across data preparation, analysis, modeling, and reporting.
- **Communication:** Explaining technical approaches and results through accessible summaries and visual analysis.

## Repository structure

```text
analysing/               Exploratory analysis scripts
create_data_set_code/    Data gathering and integration scripts
model/                   Preprocessing, training, and evaluation code
results/                 Saved aggregate cross-validation scores
create_dataset.py        Dataset assembly script
PROJECT_CONTEXT.md       Brief note for recruiters
README.md                Project overview
```

## Data availability and reproducibility

This is a **curated academic code portfolio**, not a standalone reproducible release. The original raw and processed datasets are intentionally excluded because some contain third-party content (including lyrics) or potentially sensitive artist-level information. Some scripts need original inputs, network access, or additional dependencies, and may need adaptation before they run.

The original academic report is excluded because it contains team members' personal contact details and student identifiers. No claim is made that the saved scores have been independently reproduced from this curated repository.

## Team and attribution

Developed by a **three-person academic team** at the Hebrew University of Jerusalem as part of *A Needle in a Data Haystack*. The team granted permission to share the collaborative project. This repository does not claim any single member implemented all components independently.

## Limitations and sources

Historical observational associations are not causal evidence. Class imbalance, changes in competition format, data quality, fairness, licensing, and privacy may affect interpretation. This is an academic project, **not a deployed product**.

The original academic report cited EurovisionWorld, community-maintained Eurovision datasets, and other publicly available contextual material. Third-party resources remain the property of their respective publishers. No third-party datasets or lyrics are redistributed here. No software license is asserted for the team's joint code.
