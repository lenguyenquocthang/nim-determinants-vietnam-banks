# Determinants of the Net Interest Margin of Vietnamese Commercial Banks, 2013–2023

Các yếu tố ảnh hưởng đến tỷ lệ thu nhập lãi cận biên (NIM) của các ngân hàng thương mại Việt Nam, 2013–2023. Graduation thesis, Mathematical Economics.

Balanced panel of 27 listed joint-stock banks (297 bank-year observations), Pooled OLS, FEM, REM and FGLS in Stata 17.

| | |
|---|---|
| Research report (VI/EN) | [`report/`](report/index.html) |
| Interactive walkthrough (VI/EN) | [`storytelling/`](storytelling/index.html) |
| One-page English summary | [`SUMMARY.md`](SUMMARY.md) |
| Errata | [`ERRATA.md`](ERRATA.md) |
| Original thesis | [`thesis/`](thesis/) |
| Data | [`data/`](data/) |

Live pages (GitHub Pages): https://lenguyenquocthang.github.io/nim-determinants-vietnam-banks/

## Note on the COVID-19 coefficient

The printed thesis reports a negative COVID19 coefficient. The sign is an artefact of Stata coding the variable Yes = 1, No = 2; the correct sign is positive and the corresponding hypothesis is not supported. The report and the walkthrough use the corrected sign and say so. Details and the reproduction are in [`ERRATA.md`](ERRATA.md).

## Structure

```
index.html            landing page
report/index.html     research report, self-contained
storytelling/index.html  interactive walkthrough, self-contained
thesis/               original thesis (docx, pdf)
data/                 panel data (xlsx)
SUMMARY.md  ERRATA.md
```

Each HTML page is a single static file with no build step and no external requests.

Academic analysis, not investment advice.
