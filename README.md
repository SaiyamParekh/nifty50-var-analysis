# Nifty 50 Portfolio VaR & Expected Shortfall Analysis

A multi-stock Value at Risk (VaR) model built on a portfolio of Nifty 50 constituents,
using three standard methodologies and Expected Shortfall (ES) alongside each — rather
than relying on a single VaR estimate, which says nothing about the severity of losses
beyond the threshold.

## What this covers

- A 10-stock portfolio spanning banking, IT, energy, FMCG, telecom, and industrials
  (equal-weighted; cap-weighting is a documented next step)
- **Historical Simulation VaR/ES** — empirical quantile of actual past portfolio returns,
  no distributional assumption
- **Parametric (Variance-Covariance) VaR/ES** — closed-form, assumes normally
  distributed returns, derived from the full asset covariance matrix (`w^T Σ w`)
- **Monte Carlo Simulation VaR/ES** — 50,000 correlated return scenarios via Cholesky
  decomposition of the covariance matrix
- Side-by-side comparison across methods at 95% and 99% confidence
- Explicit discussion of assumptions, where the methods diverge, and why

## Why a portfolio rather than the index alone

Modeling individual constituents rather than just the Nifty 50 index itself forces the
use of a real covariance matrix and correlation structure — the same underlying mechanic
used in institutional portfolio risk tools, rather than a single-time-series exercise.

## Assumptions and limitations

- Equal-weighted, not cap-weighted (stated explicitly as a simplification)
- Daily simple returns over a ~3-year lookback window
- Parametric VaR assumes normality, which is known to understate tail risk for equities
- All three methods share the same backward-looking covariance matrix as an input, and
  none of them account for correlations spiking during stress periods

## Tools

Python, pandas, numpy, scipy, yfinance, matplotlib.

## Setup

```bash
pip install -r requirements.txt
```

Then run `Nifty 50 Portfolio VaR Analysis.ipynb` top to bottom.
