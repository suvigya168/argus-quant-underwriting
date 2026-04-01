ARGUS: Probabilistic M&A Underwriting Engine

National Finalist (Top 8) | IIT BHU AI-Quisition 2026
ARGUS (Advanced Risk-Guided Underwriting System) is a quantitative framework developed to solve the "Deal Sourcing" challenge for mid-cap IT acquisitions. Unlike traditional models that rely on static "mean" estimates, ARGUS utilizes Bayesian Inference to model uncertainty and prioritize capital preservation.

The Problem: The "Mean" Trap
Standard M&A valuations often fail because they assume a single "best-case" growth rate. ARGUS replaces this with a probabilistic distribution, identifying targets that are not just "high-growth," but high-conviction.

Technical Architecture
Data Discipline: Automated ingestion and cleaning of a 400-company universe, enforcing numeric integrity for key underwriting variables such as P/E, ROCE, OPM, and Sales Variance.

Bayesian Posterior Sampling: Implemented using PyMC 5.28, utilizing Markov Chain Monte Carlo (MCMC) to generate growth and margin distributions based on 3-year historical priors.

Monte Carlo Simulations: Executes 4,000 simulations per target to project 5-year Free Cash Flow (FCF) paths under institutional constraints.

The Decision Rule: Risk-Adjusted Alpha
To identify the #1 Top Pick, I implemented a scoring rule that penalizes "high-growth but fragile" companies:

Score = (Mean IRR × Probability > 12%) - |Expected Shortfall × Probability < 0%|

Mean IRR: The average expected return from 4,000 simulations.

Prob > 12%: The confidence level that the investment clears our cost-of-capital (12% Hurdle Rate).

Expected Shortfall (ES): The average loss in the "worst-case" 5% of scenarios (Tail Risk).

Prob < 0%: The risk of absolute capital impairment (losing money).

Underwriting Assumptions
Horizon: 5-Year private asset maturity (Standard private asset benchmark).

Control Premium: 25% (India mid-market benchmark).

Tax/Reinvestment: 25.0% Corporate Tax and 30.0% Reinvestment drag on NOPAT.

Exit: Zero Multiple Expansion (assumes entry P/E = exit P/E) to ensure conservative bias.

Tech Stack
Language: Python.

Modeling: PyMC 5.28 (Probabilistic Programming).

Diagnostics: ArviZ 0.22 (MCMC Chain convergence/R-hat diagnostics).

Data Manipulation: Pandas, NumPy, Matplotlib.
