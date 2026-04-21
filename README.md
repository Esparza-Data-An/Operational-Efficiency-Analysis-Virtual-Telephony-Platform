# Inefficient Operator Detection — CallMeMaybe

## Overview
This project develops a data-driven methodology to identify underperforming 
operators within a virtual telephony platform (CallMeMaybe), defining 
inefficiency as a combination of high missed call rates, prolonged wait times, 
and low outbound call volume.

## Note on Language
The Jupyter notebook and internal comments are currently in Spanish. 
An English version is in progress.

## Tools & Libraries
Python · Pandas · SciPy · Seaborn · Matplotlib · Tableau

## Methodology
- **EDA & Data Cleaning:** Volume-weighted analysis using `calls_count` to 
  correct for dataset skewness, revealing a true missed call rate above 50% — 
  nearly 20 points higher than naive estimates.
- **Operator Metrics:** Five aggregated metrics derived per operator: average 
  wait time, incoming missed rate, outbound missed rate, total outbound volume, 
  and zero-duration call ratio.
- **Inefficiency Scoring:** Evidence-based thresholds assigned 1 point per 
  rule violated. Operators scoring ≥ 3 classified as critically inefficient.
- **Hypothesis Testing:** Three hypotheses validated using Mann-Whitney U and 
  Spearman correlation (α = 0.05), confirming the scoring system's reliability 
  and detecting a systematic "ghost call" pattern (ρ = 0.9996).

## Key Results
- **70 critically inefficient operators** identified (6.6% of total).
- 2 extreme cases with outbound loss rates ≥ 83% and near-zero call duration.
- Statistical validation confirmed significant separation between efficient 
  and inefficient operator groups (p ≈ 0).

## Recommendations
- Priority review of all 70 flagged operators, with immediate focus on the 
  2 highest-scoring cases.
- Technical audit of call routing to investigate ghost call patterns.
- Role reassignment for operators with low outbound volume but outbound 
  responsibilities.
- Implementation of periodic monthly monitoring using this scoring pipeline.

## Interactive Dashboard
Explore inefficient operators with filters by overall and individual scores:
[View on Tableau Public](https://public.tableau.com/views/Listadeoperadores-CallMeMaybe/Dashboard2)

## Project Structure
```
├── data/
│   ├── telecom_dataset_new.csv        # Raw call data
│   ├── telecom_clients.csv            # Raw client data
│   └── processed/
│       ├── operators_cleaned.csv      # Cleaned operators DataFrame
│       ├── clients_cleaned.csv        # Cleaned clients DataFrame
│       ├── metrics_operadores.csv     # Aggregated metrics per operator
│       ├── ranking_operadores_completo.csv        # All operators ranked
│       └── operadores_ineficaces_score_3_o_mas.csv # 70 critical operators
├── Operadores_ineficaces_CallMeMaybe.ipynb  # Main notebook (Spanish)
├── presentation.pdf                   # Key findings summary
└── README.md
