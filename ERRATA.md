# Errata / Đính chính

## VF-1: sign of the COVID19 coefficient / dấu của hệ số COVID19

**EN.** The thesis prints negative COVID19 coefficients (Pooled OLS −0.1439567, FEM −0.1870423, REM −0.1846686, FGLS −0.201074) and accepts a negative expected sign. The source data stores COVID19 as text ("Có" 81 observations, "Không" 216). Stata's `encode` assigns codes alphabetically (Có = 1, Không = 2), so the coefficient measures the effect of the non-COVID group and carries the opposite sign. Re-estimated on the data file:

- Coding Có = 1, Không = 2 reproduces the printed coefficients exactly and all other coefficients (for example CAP 0.1354034 in Pooled OLS) to the digit.
- Coding Có = 1, Không = 0 flips every COVID19 coefficient to positive (+0.1439567, +0.1870423, +0.1846686, +0.201074); p-values and all other coefficients are unchanged.

Consequence: the hypothesis of a negative COVID-19 effect on NIM is not supported. The thesis files in `thesis/` are the original submitted versions and still contain the printed sign.

**VI.** Luận văn in hệ số COVID19 âm do Stata mã hóa Có = 1, Không = 2 (theo thứ tự chữ cái). Mã lại Có = 1, Không = 0 cho dấu dương; các hệ số khác và mọi p-value không đổi. Giả thuyết COVID-19 làm giảm NIM không được ủng hộ. Các file trong `thesis/` là bản gốc đã nộp và vẫn mang dấu in.

## Other items / Các mục khác

VF-2 to VF-11 (print inconsistencies in the thesis) are listed in the appendix of the research report. They are kept as printed and flagged, not silently corrected.
