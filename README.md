# Determinants of Net Interest Margin in Vietnamese Joint-Stock Banks, 2013–2023

Panel-econometric study of bank net interest margin (NIM) for **27 listed Vietnamese joint-stock commercial banks over 2013–2023 (N·T = 297, balanced)**, including a COVID-19 period effect. Part of my [quant portfolio](https://github.com/lenguyenquocthang/quant-portfolio); a related study is [nim-determinants-vietnam-banks-2018-2023](https://github.com/lenguyenquocthang/nim-determinants-vietnam-banks-2018-2023).

**Pages:** [Landing](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/) · [Interactive walkthrough](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/storytelling/) · [Research report](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/report/)

## Specification

$$\mathrm{NIM}_{it}=\alpha_i+\beta_1\,\mathrm{CAP}_{it}+\beta_2\,\mathrm{LDR}_{it}+\beta_3\,\mathrm{NPL}_{it}+\beta_4\,\mathrm{CAR}_{it}+\beta_5\,\mathrm{ER}_t+\beta_6\,\mathrm{INF}_t+\beta_7\,\mathrm{GDP}_t+\beta_8\,\mathrm{COVID}_t+\varepsilon_{it}$$

CAP is equity capital size (%), LDR the loan-to-deposit ratio (%), NPL the non-performing loan ratio (%), CAR the capital adequacy ratio (%); ER, INF and GDP are year-level macro series (exchange rate, inflation, GDP growth) and COVID is a dummy for 2020–2022. Estimated by Pooled OLS, FEM, REM and FGLS (Stata 17).

## Model selection and diagnostics
Hausman ($p=0.6969$) does not reject REM against FEM; mean VIF is 1.59. The error-structure tests reject homoskedasticity ($p<0.0001$) and serial independence (autocorrelation $p=0.0009$), so the reported estimator is **FGLS** (Stata `xtgls`).

## Results (FGLS, 5% level)
| Variable | Coef. | Standardised $\beta^*$ | Reading |
|---|---|---|---|
| CAP | +0.1093 | +0.27 | significant, positive |
| LDR | +0.0135 | +0.17 | significant, positive |
| NPL | −0.0586 | −0.10 | significant, negative |
| COVID | +0.2011 | +0.07 | significant, **positive**: the printed negative sign is a coding artefact (see `ERRATA.md`) |
| GDP | +0.0381 | +0.05 | significant, positive |
| CAR, ER, INF | | | not significant |

Standardised effects are computed as $\beta^*=\beta\,\sigma_x/\sigma_{\mathrm{NIM}}$. NIM has mean 3.08% over the panel and 3.32% in the COVID-19 period against 2.99% otherwise.

## Independent re-estimation (Python)
Rebuilt from the raw workbook: the **bank-level** results are robust, the **macro** results are not.
- **Bank effects.** $F=26.5$ for poolability and Breusch–Pagan $LM=657$ (both $p<0.001$) reject a pooled specification; `xtgls` with AR(1) carries no bank effects. FEM with bank-clustered errors: CAP 0.108 ($p=0.004$), LDR 0.024 ($p<0.001$), NPL −0.057 ($p<0.001$), CAR insignificant. Mundlak ($p=0.48$) does not reject RE, but FE is kept for effects correlated with regressors.
- **Macro variables.** ER, INF, GDP and COVID take only $T=11$ distinct values, so bank-clustered errors overstate precision. A wild cluster bootstrap by year (Webb weights, $G=11$) gives GDP $p=0.038$ and COVID $p=0.32$; a Ho–Saunders two-step makes GDP insignificant ($p=0.59$ with COVID).
- **Dynamics.** Persistence is bracketed by pooled $\rho=0.87$ and FEM $\rho=0.46$ (Nickell bias); the Nickell-corrected value is about 0.70. Anderson–Hsiao rests on a weak instrument (first-stage $F\approx3$) and GMM is unstable with $N=27$.
- **Robustness.** Leave-one-bank-out NPL ranges from −0.082 (dropping NVB) to −0.051 (dropping STB) with worst-case $p=0.138$, so the NPL result depends on a few banks.
- **Out of sample.** Rolling-origin RMSE (origin 2017): FEM 0.597, pooled 1.05, naive $\mathrm{NIM}_{t-1}$ **0.464**. The model explains cross-sectional differences rather than predicting next-year NIM.

## Limitations
27 banks (4 state-owned), 11 years, no instruments. The COVID dummy coincides with 2020–2022 for every bank and the thesis models contain no year effects, so the coefficient absorbs everything specific to that period. Results describe associations, not causal effects. Ten further print inconsistencies in the source thesis are flagged in the report appendix.

## Repository
| Path | Content |
|---|---|
| `report/` | Research report (VI/EN), with checks and errata |
| `storytelling/` | Interactive walkthrough (VI/EN, light/dark) |
| `data/` | Balanced panel: NIM, CAR, CAP, LDR, NPL, ER, INF, GDP, COVID |
| `reestimation/` | Python code: Pooled/FEM/REM, Mundlak, wild bootstrap, Nickell, leave-one-out, rolling-origin test |
| `ERRATA.md`, `SUMMARY.md` | COVID sign correction; one-page summary |

```bash
cd reestimation && pip install -r requirements.txt
python run.py --data ../data/panel_data_27_banks_2013_2023.xlsx --out results   # ~10 s
```

Academic analysis, not investment advice.
