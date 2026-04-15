# Trader Behavior vs Market Sentiment Analysis

## Project Overview
This repository contains a submission-ready data analysis project that studies how trader behavior and trading performance change across market sentiment regimes using:

- `fear_greed_index.csv`
- `historical_data.csv`

The objective is to evaluate whether traders behave differently on **Fear** vs **Greed** days, determine whether sentiment affects profitability and risk-taking behavior, identify useful trader segments, and propose actionable trading rules based on the findings.

---

## What This Project Covers

### Part A — Data Preparation
- Loads both datasets
- Documents:
  - number of rows and columns
  - missing values
  - duplicate records
- Converts timestamps and aligns datasets at the **daily** level
- Creates the main analytical metrics:
  - daily PnL
  - win rate
  - average trade size
  - number of trades per day
  - long/short ratio
  - drawdown proxy

### Part B — Analysis
- Compares performance between **Fear** and **Greed** days
- Evaluates whether sentiment changes trader behavior:
  - trade frequency
  - average position size
  - long/short bias
  - aggressiveness proxy
- Includes trader segmentation such as:
  - frequent vs infrequent traders
  - larger-size vs smaller-size traders
  - consistent vs inconsistent traders

### Part C — Actionable Output
- Recommends practical strategy rules informed by the analysis

---

## Repository Structure

```bash
trader_sentiment_submission_repo/
│
├── notebooks/
│   └── trader_sentiment_analysis.ipynb
│
├── data/
│   ├── fear_greed_index.csv
│   ├── historical_data.csv
│   └── README.md
│
├── charts/
├── outputs/
│
├── short_writeup.md
├── README.md
├── requirements.txt
└── .gitignore
```

---

## How to Run

### Option 1: Google Colab
1. Open `notebooks/trader_sentiment_analysis.ipynb` in Colab
2. Upload:
   - `fear_greed_index.csv`
   - `historical_data.csv`
3. Update file paths if needed:
   - `/content/fear_greed_index.csv`
   - `/content/historical_data.csv`
4. Run all cells from top to bottom

### Option 2: Local Environment
1. Clone this repository
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Place the datasets in the `data/` folder
4. Open and run the notebook

---

## Methodology

### 1. Data Validation
Both datasets are first inspected for:
- shape
- missing values
- duplicates
- timestamp consistency

The provided files were found to contain:
- no missing values
- no duplicate rows

### 2. Timestamp Alignment
The trading dataset includes both `Timestamp` and `Timestamp IST`.  
Because these fields do not always align consistently, the notebook uses **`Timestamp IST`** as the primary timestamp for daily aggregation.

The sentiment dataset timestamp is converted into a calendar date, and both datasets are merged at the **date** level.

### 3. Feature Engineering
The notebook creates the following metrics:
- **Daily PnL** = total closed PnL per day
- **Win Rate** = fraction of profitable trades
- **Average Trade Size** = average notional trade size
- **Trade Frequency** = number of trades per day
- **Long Ratio** = share of buy-side trades
- **Drawdown Proxy** = cumulative PnL minus cumulative PnL peak

### 4. Segmentation
The notebook segments traders into interpretable groups such as:
- **Frequent vs Infrequent** traders
- **Larger-size vs Smaller-size** traders
- **Consistent vs Inconsistent** traders

These segments are then compared across performance and behavior measures.

---

## Key Findings

### 1. Fear days outperformed Greed days
The analysis found stronger average profitability during Fear regimes than Greed regimes in the sample.

**Interpretation:**  
Fear may encourage more selective trading, while Greed may invite overconfidence and lower-quality risk-taking.

### 2. Greed days were associated with more aggressive behavior
On Greed days, traders appeared to:
- take larger positions
- lean more long
- show more optimistic directional exposure

**Interpretation:**  
Aggressive behavior increased, but returns did not improve proportionally.

### 3. Discipline and consistency were more valuable than raw aggressiveness
Segment analysis suggested that stable, consistent traders performed better than traders who simply traded bigger or more aggressively.

---

## Strategy Recommendations

### Strategy 1 — Reduce aggressive exposure during Greed regimes
When sentiment is in a Greed state, traders with large-size or aggressive behavior should reduce position sizing or leverage proxy.

**Why:**  
Greed-driven behavior appears to increase exposure without producing equally strong performance gains.

### Strategy 2 — Encourage disciplined participation during Fear regimes
Fear regimes appear more favorable for disciplined traders. Trade participation can be maintained or slightly increased for consistent traders, but trade size should remain controlled.

### Strategy 3 — Optimize for consistency, not just scale
Risk frameworks and allocation decisions should favor traders with stable, repeatable outcomes rather than those who rely on oversized positions.

---

## Deliverables
This repository is structured to include:
- a Colab-ready notebook
- a short write-up
- a reproducible dependency file
- a clean submission layout for GitHub

---

## Suggested Enhancements
Optional future additions:
- predictive model for profitability bucket
- clustering traders into behavioral archetypes
- Streamlit dashboard for interactive exploration
- richer risk-adjusted performance metrics

---

## Author Note
This project is designed as a structured, reproducible, and reviewer-friendly submission for a Python-based data analysis task.