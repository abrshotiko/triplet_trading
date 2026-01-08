Triplet Trading Strategy

TO RUN THE CODE IN YOUR BROWSER VISIT 
https://shorturl.at/WOhSb

A small research project exploring a cointegration-based trading strategy on three assets using classical time-series tools.

The goal here wasn’t to build a production-ready strategy, but to understand how triplet relationships behave, how stable cointegration is over time, and how a VECM can be used to model both short-term dynamics and long-term equilibrium.

What this project does

This notebook walks through a full research flow for a triplet trading idea:

inspect and clean price data

reduce noise by working at a weekly frequency

test for unit roots and integration order

test for cointegration across three assets

estimate a Vector Error Correction Model (VECM)

interpret the resulting dynamics

The focus is on understanding the structure, not maximizing backtest performance.

Data handling

Prices are resampled to weekly frequency to reduce noise and trading frequency.

A structural break is observed around mid-2020, so the analysis is restarted after that point to avoid mixing regimes.

This keeps the cointegration tests and model estimates more stable.

Stationarity and unit root testing

Augmented Dickey–Fuller (ADF) tests are applied to each price series.

As expected for asset prices, the null of a unit root cannot be rejected.

After first differencing, the series become stationary, indicating I(1) behavior.

This is consistent with the assumptions required for cointegration analysis.

Cointegration analysis

Johansen cointegration tests are used to evaluate whether a stable long-run relationship exists among the three assets.

The trace statistic is used to determine the cointegration rank.

Results suggest the presence of a cointegrating relationship over the selected sample.

VECM modeling

A Vector Error Correction Model (VECM) is estimated to capture:

short-term return dynamics

long-term equilibrium forces

Key components examined:

Beta: cointegration vectors (long-run relationships)

Alpha: adjustment speeds back toward equilibrium

Constant terms: shifts in the equilibrium level

From the fitted model, sensitivities and response behavior across assets can be inspected.

Why a triplet (not pairs)

Pairs trading is well-studied. This project looks at:

whether adding a third asset stabilizes relationships

how adjustment speeds differ across assets

whether equilibrium correction is shared or dominated by one series

It’s mainly an exploration of structure and interpretation, not signal optimization.

Tech stack

Python

NumPy / pandas

statsmodels (ADF, Johansen test, VECM, VAR)

matplotlib

Everything runs inside a single Jupyter notebook.