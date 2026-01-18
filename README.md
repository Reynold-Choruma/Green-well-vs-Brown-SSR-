# Green vs Ordinary: Sustainable Sharpe Ratio (SSR)

[![Made with Python](https://img.shields.io/badge/Made%20with-Python-3776AB?logo=python&logoColor=white)]()
[![Data Sources](https://img.shields.io/badge/Data-Yahoo%20Finance%20%7C%20FRED%20%7C%20GHG-green)]()

Green vs Brown: Sustainable Sharpe Ratio (SSR) – Quant project on climate‑aware risk‑adjusted returns using Python, FRED and Yahoo Finance.

> **Quick stats (2015–2025, equal‑weighted baskets)**  
> Green: CAGR ≈ 27.7%, vol ≈ 39.9%, Sharpe ≈ 0.81  
> Brown: CAGR ≈ 4.8%, vol ≈ 29.6%, Sharpe ≈ 0.31

## Project Overview
The analysis studies Green vs Brown baskets along four dimensions:
​

#  Return – CAGR and cumulative performance

Risk – annualised volatility and maximum drawdown

Risk‑adjusted return – standard Sharpe ratio

Sustainability – GHG / ESG metrics and a derived Sustainable Sharpe Ratio (SSR)

The workflow is implemented in Jupyter notebooks and produces reusable CSVs for downstream modelling.
​

# Key Findings
The Green basket (ENPH, TSLA, NEE) exhibits higher CAGR and a higher Sharpe ratio than the Brown basket (XOM, CVX, EOG) over 2015–2025, using equal‑weighted daily excess returns.
​

Green’s outperformance is regime‑dependent: it tends to lead when climate policy momentum and ESG attention are strong, while Brown assets perform better during commodity price spikes, inflation shocks and aggressive rate‑hike periods.
​

A Sustainable Sharpe Ratio (SSR) that combines Sharpe with emissions/ESG metrics further widens the Green basket’s advantage and highlights subsectors with superior “sustainable value per unit of risk.”
​

#  Methodology
# Data and returns
Download daily prices for Green and Brown tickers from Yahoo Finance, robust to both single‑ and multi‑index formats, and compute equal‑weighted daily returns.
​

Obtain the 3‑month T‑bill rate from FRED, convert it into a daily decimal risk‑free series, forward‑fill publication gaps and align it exactly to trading days.
​

# Compute daily excess returns 
R
p
−
R
f
R 
p
 −R 
f
  # for Green and Brown baskets and derive:
​

Annualised mean return and volatility (252 trading days)

Sharpe ratio = annualised mean / annualised volatility

CAGR from the geometric product of daily excess returns

# Sustainability data and SSR
Load global CO₂ / GHG data, standardise emissions columns and construct an annual macro carbon growth factor, then forward‑fill it to a daily series.
​

Merge basket returns, risk‑free rate, market factor and carbon factor into a single aligned daily dataset for analysis and plotting.
​

Define a Sustainable Sharpe Ratio (SSR) by combining the conventional Sharpe ratio with carbon/ESG metrics (e.g. Sharpe divided by carbon intensity or scaled by an ESG score) at basket or subsector level, and store results in summary tables.
​

# Regime analysis
Compute rolling 12‑month Green–Brown performance differentials and relate them to interest‑rate moves, commodity prices and macro carbon dynamics.
​

Identify regimes where Green tilts add resilience and sustainable growth, and regimes where Brown exposure acts as a diversifier and inflation hedge.
​

# Repository Structure
# Notebooks

Yahoo Finance.ipynb – Download and clean adjusted prices for Green and Brown tickers, compute daily returns, and export daily_returns.csv.
​

FRED.ipynb – Retrieve the risk‑free series from FRED, transform to daily decimal rates, align to trading days, and save rf_daily.csv.
​

GHG:Carbon Emissions.ipynb – Load and clean GHG / CO₂ data, build an annual macro carbon factor, forward‑fill to daily frequency, and save ghg_macro.csv.
​

Market Risk Premium.ipynb – Construct a market proxy (e.g. S&P 500), compute daily market returns and a market risk premium series, exporting cleaned_market_risk_premium.csv.
​

Data Alignment and Merging.ipynb – Align all series on the intersection of trading days and produce aligned_data.csv and basket_metrics.csv.
​

final_notebook.ipynb – End‑to‑end analysis: metrics, cumulative and rolling plots, regime analysis and SSR calculations.
​

# Key data outputs

daily_returns.csv – Daily returns for individual tickers and equal‑weighted baskets.
​

rf_daily.csv – Cleaned daily risk‑free rate aligned to trading days.
​

ghg_macro.csv – Daily macro carbon growth factor.
​

cleaned_market_risk_premium.csv – Daily market excess return proxy.
​

aligned_data.csv – Fully merged panel for returns, risk‑free, market and carbon variables.
​

basket_metrics.csv – Summary metrics (CAGR, volatility, Sharpe, and SSR fields) for Green and Brown baskets.
​

# How to Run
Install dependencies

bash
pip install pandas numpy yfinance fredapi matplotlib
Set up FRED access

Obtain a FRED API key and insert it in FRED.ipynb where the Fred() object is initialised.
​

# Execute notebooks in order

Yahoo Finance.ipynb

FRED.ipynb

GHG:Carbon Emissions.ipynb

Market Risk Premium.ipynb

Data Alignment and Merging.ipynb

final_notebook.ipynb
​

Each step writes intermediate CSVs so the analysis can be resumed or extended from the aligned dataset.

# Disclaimer
This project is for research and educational purposes only and does not constitute investment advice. Data sources, ESG metrics and SSR definitions are illustrative and may not capture all dimensions of sustainable investing.
​



