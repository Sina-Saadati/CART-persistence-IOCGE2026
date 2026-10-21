# CART-persistence-IOCGE2026
Supplement, figures and code for the IOCGE 2026 poster: a multi-cohort single-cell analysis of CAR-T persistence and decline in relapsed B-ALL (hypothesis-generating; mechanistic results are in silico).
# A Multi-Cohort Single-Cell Analysis of CAR-T Cell Persistence and Decline in Relapsed B-ALL

Poster for the 3rd International Online Conference on Genes (IOCGE 2026), 2–4 December 2026, Sciforum-210300.
Authors: Sina Saadati, Ali Rajabi, Reza Safaralizadeh. Dept. of Animal Biology, University of Tabriz.
Contact: sina.saadati.ac@gmail.com

## Contents
- `poster/` – final poster (PDF)
- `supplement/` – detailed figure captions, per-patient tables, definitions, software versions
- `figures/` – panels A–K as PNG
- `tables/` – small derived tables

## Data sources (public)
| Cohort | GEO | Role |
|---|---|---|
| Discovery | GSE235760 | clonal fate, persistence signature |
| Validation | GSE162975 | signature projection, receiver cells |
| Blasts | GSE153697 | NicheNet sender |

## Key caveats
- Relapse group is small (5 patients); 44/47 RE cells in the CellOracle set come from one patient.
- Cells and clones are nested in patients; tests are descriptive.
- Receptor (CD40) support is weak; the NFKBIA/TNFAIP3 signal is not LTB-specific.

## Software
R 4.5.2; Seurat 5.5.1; SeuratObject 5.4.0; scRepertoire 2.6.2; nichenetr 2.2.1.1.

## License
Text and figures: CC BY 4.0. Code: MIT.
