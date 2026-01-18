## Green vs Ordinary: Sustainable Sharpe Ratio (SSR)

# Summary

This project builds and compares Green and Ordinary/Brown equity baskets using historical market data, macro factors and carbon/ESG information. It introduces a Sustainable Sharpe Ratio (SSR) that augments the traditional Sharpe ratio with emissions or ESG metrics to evaluate “sustainable value per unit of risk.”
​

Over the sample, the Green basket delivers higher returns and a higher Sharpe ratio than the Brown basket, and this advantage becomes more pronounced once sustainability is incorporated via SSR.
​

## Key Results
The Green basket shows a higher CAGR and higher Sharpe ratio than the Brown basket over 2015–2025 using equal‑weighted daily excess returns.
​

Green outperformance is regime‑dependent: it tends to lead during periods of strong climate policy, elevated ESG attention and supportive macro conditions, while Brown assets outperform in commodity spikes, inflation shocks or sharp rate‑hike regimes.
​

A Sustainable Sharpe Ratio (SSR), constructed by combining Sharpe with carbon/ESG metrics, further widens the Green basket’s advantage and highlights subsectors that offer better sustainable risk‑adjusted returns.
​

## Project Structure
#  Core notebooks:

Yahoo Finance.ipynb – Downloads and cleans daily prices for Green (ENPH, TSLA, NEE) and Brown (XOM, CVX, EOG) baskets using yfinance, computes daily returns and saves daily_returns.csv.
​

FRED.ipynb – Pulls the 3‑month T‑bill rate from FRED, converts it into a daily decimal risk‑free series aligned to trading days, and saves rf_daily.csv.
​

GHG:Carbon Emissions.ipynb – Loads global CO₂ / GHG data, constructs an annual macro carbon factor, forward‑fills it to a daily series, and exports ghg_macro.csv.
​

Market Risk Premium.ipynb – Builds a proxy for the market portfolio (e.g. S&P 500), computes daily market returns and a market risk premium series, and saves cleaned_market_risk_premium.csv.
​

Data Alignment and Merging.ipynb – Aligns portfolio returns, risk‑free rates, macro variables and carbon factors on a common daily index, producing aligned_data.csv and basket‑level metrics in basket_metrics.csv.
​

final_notebook.ipynb – End‑to‑end workflow: performance metrics, rolling Green–Brown differentials, regime tagging and SSR computation / portfolio interpretation.
​

# Key CSV outputs:

daily_returns.csv – Equal‑weighted daily returns for Green and Brown baskets derived from adjusted close prices.
​

rf_daily.csv – Cleaned and aligned daily risk‑free rate from FRED, in decimal form.
​

ghg_macro.csv – Daily macro carbon factor constructed from annual global emissions growth.
​

cleaned_market_risk_premium.csv – Daily market excess return proxy.
​

aligned_data.csv – Fully merged dataset of basket returns, risk‑free rate, market factor and GHG factor.
​

basket_metrics.csv – Summary statistics (CAGR, volatility, Sharpe, and SSR fields) for Green vs Brown baskets.
​

# Methodology
# Return and risk computation

Download daily prices for selected Green and Brown tickers via yfinance, robustly handling both single‑ and multi‑index data structures.
​

Compute equal‑weighted daily returns and excess returns (Rp − Rf) for each basket, then derive annualised return, volatility and a standard Sharpe ratio using 252 trading days.
​

# Sustainability integration

Load global GHG / emissions data, clean and standardise the emissions series, and construct an annual macro carbon growth factor.
​

Align the factor to daily frequency via forward‑fill and merge it with returns, risk‑free rate and market data in a single daily panel.
​

# Sustainable Sharpe Ratio (SSR)

Start from the conventional Sharpe ratio for each basket or subsector.
​

Combine Sharpe with emissions or ESG information (e.g. Sharpe divided by carbon intensity or scaled by ESG score) to obtain an SSR that rewards both financial performance and sustainability.
​

# Regime analysis

Compute rolling 12‑month Green–Brown excess performance and relate it to macro and carbon regimes (policy cycles, commodity shocks, interest‑rate cycles, GHG dynamics).
​

Use these regimes to interpret when Green tilts add resilience and when Brown exposure offers diversification and inflation hedging.
​

