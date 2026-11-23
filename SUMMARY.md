# Determinants of the Net Interest Margin of Vietnamese Commercial Banks, 2013–2023

One-page summary. Figures are taken from the thesis tables and re-checked against the data file.

**Question.** Which bank-specific and macroeconomic factors, and the COVID-19 period, are associated with the net interest margin (NIM) of listed Vietnamese commercial banks?

**Data.** Balanced panel of 27 listed joint-stock commercial banks, 2013–2023, 297 bank-year observations. Dependent variable: NIM. Eight explanatory variables: capital ratio (CAP), loan-to-deposit ratio (LDR), non-performing loan ratio (NPL), capital adequacy ratio (CAR), exchange rate (ER), inflation (INF), GDP growth (GDP) and a COVID-19 period dummy.

**Method.** Pooled OLS, fixed effects (FEM), random effects (REM) and feasible GLS (FGLS) in Stata 17. Diagnostics: Hausman test p = 0.6969; mean VIF 1.59; heteroskedasticity rejected (p < 0.0001); first-order autocorrelation rejected (p = 0.0009). FGLS is the preferred specification because the error-structure tests reject homoskedastic and uncorrelated errors. Standardised coefficients are computed for this page as $\beta^* = \beta\,\sigma_x/\sigma_{NIM}$.

**Findings (FGLS, 5% level).**

| Variable | Sign | Coefficient | Standardised β* |
|---|---|---|---|
| CAP | + | 0.1093 | +0.27 |
| LDR | + | 0.0135 | +0.17 |
| NPL | − | −0.0586 | −0.10 |
| COVID19 | + | +0.2011 | +0.07 |
| GDP | + | 0.0381 | +0.05 |
| CAR, ER, INF | not significant | | |

**Correction to the printed thesis.** The thesis prints a negative COVID19 coefficient and accepts the hypothesis that the pandemic lowered NIM. The variable was coded Yes = 1, No = 2 by Stata, which reverses the sign. Re-running the regressions reproduces the printed values under that coding and gives the positive sign under Yes = 1, No = 0, with every other coefficient and p-value unchanged. The positive sign matches the thesis's own descriptive statistics (mean NIM 3.32% in the COVID-19 period versus 2.99% otherwise). The hypothesis of a negative effect is therefore not supported. See `ERRATA.md`.

**Limits.** The COVID-19 dummy coincides with 2020–2022 for every bank and the models contain no year effects, so the coefficient absorbs everything specific to that period and is not a causal estimate of the pandemic. The relationships are statistical associations, not causal effects. Ten further print inconsistencies in the thesis are listed and flagged in the report appendix (VF-2 to VF-11).
