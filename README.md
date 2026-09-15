# Movie Money Maker: Box Office ROI Optimization

## Overview
This repository contains a complete, end-to-end Machine Learning pipeline designed to optimize box office revenue and maximize Return on Investment (ROI) for feature films. By shifting away from intuition-based film financing, this project utilizes an XGBoost Regressor to identify the structural, financial, and creative parameters that mathematically guarantee the highest probability of commercial success.

## Repository Structure
```text
├── Images/                       # Exported PNGs of EDA and Feature Importance charts
├── Presentations/                # PDF and PPTX versions of the Technical and Business slide decks
├── TMDB_5000_data/               # Raw baseline dataset files
├── .env                          # Contains active TMDB API Key (provided for reviewer convenience)
├── analysis.ipynb                # Main Jupyter Notebook containing all code, EDA, and modeling
├── Instructions.docx             # Original technical assessment prompt
├── movie_revenue_model.pkl       # Serialized XGBoost model for downstream deployment
├── requirements.txt              # Python dependencies
└── tmdb_5000_enriched.csv        # The final, cached dataset (post-API enrichment)

```

## Quick Start & Installation

**1. Environment Setup**
It is recommended to run this project in a virtual environment.

```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate

```

**2. Install Dependencies**

```bash
pip install -r requirements.txt

```

**3. API Key & `.env` Configuration**
*Note: An active `.env` file containing a live TMDB API key has been explicitly included in this submission solely to ensure a frictionless review process. Reviewers can run the `analysis.ipynb` notebook from top to bottom without needing to register for an external developer account.*

## Methodology Highlights

* **Data Enrichment & MLOps:** The baseline IMDB Top 5000 dataset was merged and dynamically enriched using the external TMDB REST API. Missing financial rows were overwritten with live data, and the results were cached locally (`tmdb_5000_enriched.csv`) to ensure absolute reproducibility and bypass API rate limits during model training.
* **Target Encoding with Strict Leakage Prevention:** High-cardinality categorical variables (thousands of unique directors, producers, and actors) were transformed into dense numerical features by mapping them to their historical median revenues. This was computed strictly on the 80% training split to guarantee zero data leakage.
* **Regularization via Frequency Thresholding:** A minimum threshold of 3 appearances was enforced for talent scores to register, falling back to the global median to prevent the model from memorizing single-hit anomalies.
* **Modeling:** An eXtreme Gradient Boosting (XGBoost) Regressor was selected for its scale-invariant architecture. Hyperparameters were optimized via `GridSearchCV` with 5-fold cross-validation.

## Key Business Findings (Project Avery NEXUS)

The predictive engine identified the following optimal parameters for maximizing risk-adjusted ROI:

1. **The Capital Sweet Spot:** Production budgets between **$40M–$100M** provide sufficient scale for global marketing without catastrophic downside risk.
2. **The Genre Opportunity:** **Animation** and **Sci-Fi/Adventure** deliver the highest median returns in the industry while remaining structurally undersupplied compared to highly saturated Drama/Comedy markets.
3. **The Talent Multiplier:** While visionary directors dictate revenue ceilings, elite **producers** maintain a remarkably high, reliable financial baseline across multi-film portfolios.

Applying these parameters to a hypothetical pitch ("Project NEXUS") yielded an estimated out-of-sample ROI of 179% with over $322M in pure projected profit.

## Author

**Sahruday Prakash Sherla**
