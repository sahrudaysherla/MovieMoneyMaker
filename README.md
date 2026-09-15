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
