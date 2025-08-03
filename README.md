# MISO FTR Spread Scoring & Selection

This project develops a data-driven pipeline to identify promising Financial Transmission Rights (FTR) spreads in the MISO electricity market using historical congestion behavior, clustering techniques, and performance scoring.

---

## Project Overview

This repository contains a structured approach to:

1. **Clean and structure MISO Day-Ahead LMP data**
2. **Score nodes based on congestion characteristics**
3. **Group nodes into behavioral clusters**
4. **Select and rank spreads with high potential FTR alignment**
5. **Evaluate historical spread performance**

---

## Motivation

The MISO FTR market offers opportunities to hedge or speculate on locational congestion. However, identifying profitable node-to-node spreads is complex due to:

- Network topology
- Constraint dynamics
- Volatility in hourly congestion prices

This project builds a toolchain that analyzes congestion behavior statistically, finds structure in node relationships, and isolates spreads with strong historical signals — creating a repeatable method for FTR discovery and analysis.

---

## File Structure

| Notebook | Purpose |
|----------|---------|
| `1_Data_Cleaning.ipynb` | Parses and processes MISO Day-Ahead LMP data into a clean hourly time series per node, extracting congestion components |
| `2_Scoring_Grouping.ipynb` | Computes statistical scores (mean, std, skew, kurtosis, etc.) per node and clusters nodes with similar congestion patterns |
| `3_Strategy_Performance.ipynb` | Selects top scoring spreads, matches source and sink nodes, and evaluates historical performance of candidate FTR strategies |

---

## Methodology Highlights

- **Congestion Scoring**: Nodes are scored using descriptive statistics of congestion price series (e.g., mean congestion, volatility, kurtosis, % positive hours)
- **Clustering**: Nodes are grouped using KMeans to identify behavioral similarity, improving match potential and reducing noise
- **Spread Matching**: For a given sink node, the best historical source node is selected based on spread metrics and cluster overlap
- **Performance Evaluation**: Strategy backtests are simulated using historical spreads to estimate expected PnL behavior

---

## Key Features

- Handles thousands of hourly LMP time series
- Highlights consistently congested or anti-congested nodes
- Visual and tabular output for top candidate spreads
- Designed to align with MISO’s **720-hour FTR product convention** (normalized monthly MW)

---

## Requirements

- Python 3.8+
- `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- Data: MISO Day-Ahead LMP data

---

## Disclaimer

This project is for research and educational purposes only. It does not constitute financial advice or guarantee market performance. The MISO market is complex and subject to regulatory, operational, and physical constraints not fully captured in this model.

