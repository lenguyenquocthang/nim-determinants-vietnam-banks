# Determinants of the Net Interest Margin of Vietnamese Commercial Banks, 2013–2023

Các yếu tố ảnh hưởng đến tỷ lệ thu nhập lãi cận biên (NIM) của các ngân hàng thương mại Việt Nam, 2013–2023. Graduation thesis, Mathematical Economics.

Balanced panel of 27 listed joint-stock banks (297 bank-year observations), Pooled OLS, FEM, REM and FGLS in Stata 17.

**Live site:** https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/

| Content | Link |
|---|---|
| Research report (VI/EN) | [Open the report](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/report/) |
| Interactive presentation (VI/EN) | [Open the presentation](https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/presentation/) |
| Robustness re-estimation (code, results) | [reestimation/](reestimation/): wild cluster bootstrap by year, Nickell-bias correction, Mundlak test, leave-one-bank-out, out-of-sample RMSE |
| One-page English summary | [SUMMARY.md](SUMMARY.md) |
| Errata | [ERRATA.md](ERRATA.md) |
| Original thesis | [thesis folder](thesis) |
| Data | [data folder](data) |

## Note on the COVID-19 coefficient

The printed thesis reports a negative COVID19 coefficient. The sign is an artefact of Stata coding the variable Yes = 1, No = 2; the correct sign is positive and the corresponding hypothesis is not supported. The report and the presentation use the corrected sign and say so. Details and the reproduction are in [ERRATA.md](ERRATA.md).

## Structure

Each HTML page is a single static file with no build step and no external requests: index.html (landing page), report/index.html (research report), presentation/index.html (interactive presentation), reestimation/ (Python re-estimation code and results; the data workbook is in data/). The original thesis is in thesis/, the panel data in data/, and the summary and errata are SUMMARY.md and ERRATA.md.

Academic analysis, not investment advice.
