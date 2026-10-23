# Supplementary Information

**A Multi-Cohort Single-Cell Analysis of CAR-T Cell Persistence and Decline in Relapsed B-ALL**
IOCGE 2026 (3rd International Online Conference on Genes), Session S5 Cancer Genetics, poster Sciforum-210300.
Authors: Sina Saadati, Ali Rajabi, Reza Safaralizadeh. Department of Animal Biology, Faculty of Natural Sciences, University of Tabriz, Iran.

This document accompanies the poster. It reports an exploratory reanalysis of public single-cell data. Cells and clones are nested within patients, so all tests are descriptive, and the mechanistic results (NicheNet, CellOracle) are computational predictions. Panel letters A–K correspond to the poster.

## Contents
1. Panel map and detailed figure captions (A–K)
2. Methods details
3. Supplementary tables S1–S8
4. Definitions and data notes
5. Extended limitations
6. Software and reproducibility
7. References

---

## 1. Panel map and detailed captions

| Poster | Content | File in `figures/` |
|---|---|---|
| A | Persistence score vs time (CR vs RE) | `A_persistence_trend.png` |
| B | Clone size by clonal-fate class | `B_clone_size.png` |
| C | Persister clones, infusion vs peak | `C_persister_expansion.png` |
| D | NicheNet ligand ranking | `D_ligand_ranking.png` |
| E | Receptor detection | `E_receptor_detection.png` |
| F | Ranks of NFKBIA/TNFAIP3/BTG1 across ligands | `F_ligand_target_ranks.png` |
| G | UMAP, clinical origin and clusters | `G_umap_context.png` |
| H | MAFF→NFKBIA edge strength by cluster | `H_maff_cluster_association.png` |
| I | Simulated cell-state shift after MAFF knockout | `I_vector_field.png` |
| J | Predicted NFKBIA change per cell | `J_delta_nfkbia.png` |
| K | Knockout effect, CR vs RE | `K_ko_effect_bar.png` |

**A.** Faint points: single cells; thin lines with open circles: patient-level means; thick lines with filled circles: mean of patient means (open thick circles: single-patient weeks). Spearman ρ pooled over cells (not independent); patient-timepoint means test at lower resolution (CR n = 26; RE n = 10). Patient composition differs between weeks (CR: 12, RE: 5 patients in total). RE trajectories are heterogeneous (RE02 rising, RE03 falling). OT and NR patients not shown.

**B.** Clone size (cells per TCR clone) by clonal-fate class in the discovery cohort (5 patients; clones nested within patients). Persister clones are detected at both infusion and peak (≥ 2 cells by definition; size is summed over both timepoints, whereas the other classes are single-timepoint), so the comparison is descriptive, not a test of expansion. Only 1,075 of 4,998 persister-class cells are CAR-positive.

**C.** Persister clones (n = 389; 5 patients): cells per clone at infusion vs peak. Each point = clones with identical counts (area proportional to the number of clones; no jitter); dashed line: no change. Pooled cells 1,841 → 3,157 (~1.7×); 153 clones expanded, 135 were unchanged and 101 contracted. Descriptive tests (clones nested in patients, not independent): raw-count paired Wilcoxon p = 2.0 × 10⁻⁴ (ties excluded; n = 254), depth-normalised p = 1.7 × 10⁻⁵ (n = 389). The effect is heterogeneous: per-patient raw-count tests are significant only in P1 and P3 (Table S1). 77/153 expanded clones start from a single cell at infusion; 120/135 unchanged clones are single-cell clones at both timepoints. The expansion is also seen in CAR⁺ cells (428 → 647) as well as CAR⁻ cells (1,413 → 2,510).

**D.** NicheNet ligand activity (corrected AUPR) of 143 candidate ligands expressed in relapse blasts (GSE153697, 1 patient; T2-CD19neg), predicted to regulate a 14-gene set upregulated in declining persisters (47 RE vs 419 CR cells; RE cells mostly from one patient). LTB (receptors: LTBR, TNFRSF1A, CD40; TNF-receptor family) has the highest corrected AUPR but not the highest AUROC (0.663; rank 111/143); the ranking is based on three genes (NFKBIA, TNFAIP3, BTG1). Rank-2 GLG1 binds SELE/MOG/UNC5B. Several top ligands (TNF, CD40, IL1B, TRAF2) are NF-κB activators, so the signal may be NF-κB-generic. LTB was selected manually from the AUPR ranking.

**E.** Percentage of cells with detected expression (> 0) of the three LTB receptors; whiskers: 95% Wilson CI. Three sets are shown because they differ by design: CR stable, filtered (n = 419; 7 patients); RE declining, filtered (n = 47; mostly one patient); RE declining, NicheNet receiver set (n = 120; 3 patients; contains the 73 cells removed by the B-lineage marker filter). CD40 is detected only in the unfiltered receiver set (10/120) and in 0/47 filtered RE cells, consistent with possible B-cell contamination; TNFRSF1A is detected less often in RE than CR. Cells are not independent.

**F.** Rank of NFKBIA, TNFAIP3 and BTG1 (members of the 14-gene set of interest: DE genes in 47 RE declining vs 419 CR stable cells) in the NicheNet target list of the five highest-activity ligands (33,354 genes; 1 = strongest). LTB has the best joint ranks (NFKBIA 4, TNFAIP3 5, BTG1 31), but NFKBIA/TNFAIP3 also rank in the top 20 for GLG1, CD40 and TNF, so the overlap is not LTB-specific. NicheNet weights are model scores, not statistical estimates; absolute weights for these genes are higher for TNF, IL1B and CD40 (0.15–0.28) than for LTB (0.08). † TNFAIP3 is part of the persistence signature. The other 10 genes of the set that are present in the model rank ≥ 1,121 for LTB (MT-RNR2 is absent from the model).

**G.** UMAP of 466 CellOracle cells: 419 CR stable and 47 RE declining. Left: clinical origin (RE drawn on top). Right: Louvain clusters; clusters 1 and 3 come almost entirely from a single CR patient (CR04, CR05; both at 12 weeks), i.e. patient-specific rather than shared states. RE cells are found only in clusters 0 (40) and 2 (7), which each contain cells from ≥ 8 patients. 44/47 RE cells come from one patient (RE02; 41 at 9 weeks), versus 7 CR patients.

**H.** Top: percentage of RE declining cells per Louvain cluster of the CellOracle set (466 cells; counts shown). Bottom: coefficient of the MAFF→NFKBIA edge in the cluster-specific GRN (absent in cluster 1; set to 0 for the correlation). Spearman ρ across n = 4 clusters is descriptive only (p = 0.051). Edge strength varies with cluster size (253, 99, 78, 36 cells); 44/47 RE cells come from one patient (RE02), and 40/47 fall in cluster 0.

**I.** In silico simulation (CellOracle; MAFF expression set to 0; 3 propagation steps), not an experiment. Streamlines show the predicted direction of cell-state shift on the UMAP of the 466 cells (CR stable 419, RE declining 47; RE cells mostly from one patient), restricted to grid points with enough cells (818/1,600). The predicted shift is larger than the randomised control at these grid points (median shift magnitude 0.107 vs 0.035; 90th percentile 0.426 vs 0.098; mean 3.7×) and differs in direction (median cosine −0.12); grid points are spatially correlated, so no test is reported (Table S7).

**J.** In silico MAFF knockout (CellOracle): predicted change in NFKBIA expression (a.u.; linear colour scale, darker = larger decrease) for each of the 466 cells (CR stable 419; RE declining 47, outlined in orange). Cells in cluster 1 are unaffected (no MAFF→NFKBIA edge), and the largest effects are in the upper lobe (cluster 2; mean −0.29 in CR, −0.41 in RE, n = 7). Of the 72 cells with a decrease > 0.2, 56 are CR stable, but RE cells more often show a strong decrease (34% vs 13%). The size of the effect scales with baseline NFKBIA/MAFF expression, and 44/47 RE cells come from one patient.

**K.** Bars: mean ± SEM of predicted Δ expression after in silico MAFF KO (CellOracle). n = 419 CR stable vs 47 RE declining cells (individual cells, not independent patient-level replicates); 44/47 RE cells come from one patient (RE02). The larger absolute NFKBIA drop in RE is accompanied by higher baseline MAFF expression in these cells (imputed layer: 0.35 vs 0.22); adjusting for baseline MAFF and NFKBIA expression reduces the group difference by about half (Table S6d).

---

## 2. Methods details

**Cohorts.** Discovery: GSE235760 (5 patients; paired infusion product and peak; scRNA-seq with αβTCR; CAR⁺ and CAR⁻ T cells). Validation: GSE162975 (26 B-ALL patients; serial sampling; 7,577 CAR⁺ cells in the analysed object; weeks 0–16). Blasts: GSE153697 (one relapse patient; CD19⁻ relapse blasts, T2-CD19neg, used as NicheNet sender).

**Clonal fate (discovery).** Clones were defined per patient with the strict clonotype of scRepertoire (clone = patient + clonotype). Classes: Persister (detected at both infusion and peak; ≥ 2 cells by definition), IP-restricted/extinction (infusion only), Peak-only/de novo (peak only). Class sizes: Table S1. Persister clone expansion was assessed with paired Wilcoxon tests on raw counts (changed clones only) and on depth-normalised frequencies (cells per clone divided by the patient-timepoint total).

**Persistence signature.** Persister cells (all cells from persister clones at both timepoints) were compared with IP-restricted cells (Wilcoxon test; min.pct 0.1; |log2FC| > 0.25; adj. p < 0.05). The top 50 up- and 50 down-regulated genes by log2FC formed the signature. A module score (up − down) was computed per cell in the validation cohort (persistence net score). The signature genes are provided in `tables/persistence_signature_genes.csv`; *TNFAIP3* is in the up-list and *LTB* in the down-list.

**Receiver cells and gene set of interest (NicheNet).** RE-patient cells at weeks 9 and 12 with a persistence score ≥ the 66th percentile of RE late cells (120 cells, 3 patients: RE01 38, RE02 61, RE03 21) formed the receiver set. The comparison set comprised CR cells at weeks 9 and 12 above the same score cutoff. Cells expressing any of 11 B-lineage/blast marker genes (CD79A, CD79B, MS4A1, IGHD, IGHM, TCL1A, BANK1, DNTT, IGKC, VPREB1, VPREB3) were removed, leaving 419 CR stable and 47 RE declining cells (the CellOracle set). The gene set of interest was the genes upregulated in RE declining vs CR stable (Wilcoxon; min.pct 0.1; log2FC > 0.25; adj. p < 0.05; only positive): 14 genes (Table S3); background: genes expressed in the receiver cells. Ligands expressed by relapse blasts were ranked by corrected AUPR; the top 10 targets of the manually selected ligand (LTB) were extracted. Receptors were not run through the NicheNet receptor-expression step; instead receptor detection was quantified directly (Table S4).

**CellOracle.** The 466-cell set was clustered (Louvain; clusters 0–3 = 253/99/78/36 cells); cluster-specific GRNs were built from the human promoter base GRN (2,000 filtered links per cluster); *MAFF* expression was set to 0 and the shift simulated with 3 propagation steps. Per-cell predicted change was extracted for NFKBIA and TNFAIP3.

**Statistics.** Spearman correlations and Wilcoxon tests are descriptive, because cells and clones are nested in patients. Adjusted p-values are Bonferroni-corrected (Seurat default). Error bars: SEM (panel K) and 95% Wilson CI (panel E).

---

## 3. Supplementary tables

### Table S1. Discovery cohort: clone sizes and persister expansion

**S1a. Clone size by class** (clone = patient + strict clonotype + class)

| Class | Clones | Mean cells/clone | Median | Max |
|---|---|---|---|---|
| IP-restricted (extinction) | 16,489 | 1.03 | 1.0 | 15 |
| Peak-only (de novo) | 13,768 | 1.14 | 1.0 | 64 |
| Persister | 389 | 12.85 | 4.0 | 188 |

**S1b. Share of clones by size bin (%)**

| Class | 1 | 2 | 3–5 | 6–10 | > 10 |
|---|---|---|---|---|---|
| IP-restricted (extinction) | 98.2 | 1.4 | 0.4 | 0.1 | 0.0 |
| Peak-only (de novo) | 95.3 | 2.8 | 1.4 | 0.3 | 0.3 |
| Persister | 0.0 | 30.8 | 26.0 | 19.0 | 24.2 |

**S1c. Persister clones per patient (infusion vs peak)**

| Patient | Persister clones | Expanded | Unchanged | Contracted | Persister cells (infusion → peak) | Median depth-normalised fold-change | Paired Wilcoxon p (raw counts, changed clones) |
|---|---|---|---|---|---|---|---|
| P1 | 82 | 37 | 30 | 15 | 258 → 411 | 1.32 | 9.0 × 10⁻⁴ |
| P2 | 95 | 33 | 31 | 31 | 521 → 820 | 1.15 | 0.97 |
| P3 | 93 | 32 | 45 | 16 | 171 → 804 | 0.78 | 5.2 × 10⁻⁴ |
| P4 | 95 | 42 | 23 | 30 | 824 → 1,038 | 1.07 | 0.20 |
| P5 | 24 | 9 | 6 | 9 | 67 → 84 | 0.81 | 0.88 |

Raw-count tests use clones whose count changed; per-patient p-values are uncorrected, and the two significant values remain below 0.05 after Bonferroni correction for five patients. The per-patient median of the depth-normalised fold-change mainly reflects the sequencing-depth ratio between timepoints, because unchanged clones (mostly single-cell clones) determine the median: equal raw counts correspond to a value below 1 when the peak sample is larger (for example P3, 5,962 vs 4,634 cells). Pooled: 389 clones; 153 expanded / 135 unchanged / 101 contracted; cells 1,841 → 3,157; median normalised fold-change 1.15 (largely a depth effect, see above); paired Wilcoxon p = 2.0 × 10⁻⁴ (raw, n = 254) and 1.7 × 10⁻⁵ (normalised, n = 389).

**S1d. Cells per patient and timepoint (cells with TCR in the clonal-fate table)**

| Patient | Cells at infusion | Cells at peak |
|---|---|---|
| P1 | 4,610 | 3,500 |
| P2 | 3,696 | 3,214 |
| P3 | 4,634 | 5,962 |
| P4 | 3,646 | 3,414 |
| P5 | 2,246 | 2,788 |

**S1e. Persister-class cells by CAR status**

| CAR status | Infusion cells | Peak cells |
|---|---|---|
| neg | 1,413 | 2,510 |
| pos | 428 | 647 |

### Table S2. Validation cohort (GSE162975)

**S2a. Cells and patients per label in the analysed object**

| Group | Cells | Patients |
|---|---|---|
| CR | 3,804 | 12 |
| NR | 671 | 3 |
| OT | 1,656 | 6 |
| RE | 1,446 | 5 |

**S2b. Patients per week (CR and RE)**

| Week | CR | RE |
|---|---|---|
| 1 | 5 | 2 |
| 3 | 6 | 3 |
| 6 | 4 | 1 |
| 9 | 5 | 2 |
| 12 | 4 | 2 |
| 14 | 1 | 0 |
| 16 | 1 | 0 |

**S2c. RE patients: mean persistence score per week (number of cells)**

| Patient | Week 1 | Week 3 | Week 6 | Week 9 | Week 12 |
|---|---|---|---|---|---|
| RE01 | – | – | – | – | 0.08 (n=152) |
| RE02 | – | −0.08 (n=141) | 0.40 (n=153) | 0.48 (n=83) | 0.41 (n=9) |
| RE03 | 0.67 (n=187) | 0.65 (n=60) | – | 0.05 (n=109) | – |
| RE04 | 0.41 (n=140) | – | – | – | – |
| RE05 | – | 0.59 (n=78) | – | – | – |

In RE, week-1 values come from RE03/RE04, week-12 values mainly from RE01 (152 of 161 cells). Within-patient trends: RE02 rises (ρ = +0.56) and RE03 falls (ρ = −0.57); only these two RE patients have ≥ 3 timepoints.

**S2d. Correlation of persistence score with time (weeks ≥ 1)**

| Group | Cells (wk ≥ 1) | Patients | ρ (cells) | p (cells) | Patient-timepoints | ρ (patient-timepoint means) | p |
|---|---|---|---|---|---|---|---|
| CR | 3,197 | 12 | 0.232 | 3.5 × 10⁻⁴⁰ | 26 | 0.198 | 0.33 |
| RE | 1,112 | 5 | −0.334 | 2.0 × 10⁻³⁰ | 10 | −0.483 | 0.16 |

### Table S3. NicheNet gene set of interest and ligand ranking

**S3a. The 14-gene set (RE declining vs CR stable; fractions of cells expressing) with rank/weight in the LTB target list**
(33,354 genes in the model; MT-RNR2 is absent from the model)

| Gene | log2FC (RE vs CR) | Fraction of RE cells | Fraction of CR cells | Adj. p | LTB rank | LTB weight |
|---|---|---|---|---|---|---|
| NFKBIA | 2.05 | 0.957 | 0.857 | 1.2 × 10⁻⁸ | 4 | 0.0796 |
| HLA-C | 0.7 | 1.0 | 0.995 | 3.9 × 10⁻⁶ | 14,816 | 0.0025 |
| BTG1 | 1.33 | 0.957 | 0.909 | 1 × 10⁻⁵ | 31 | 0.0731 |
| MT1E | 3.99 | 0.638 | 0.301 | 2.9 × 10⁻⁵ | 8,293 | 0.0044 |
| MT-RNR2 | 0.62 | 1.0 | 1.0 | 3.8 × 10⁻⁵ | not in model | – |
| MT1X | 3.43 | 0.702 | 0.425 | 5.7 × 10⁻⁵ | 6,739 | 0.0049 |
| RBM38 | 2.74 | 0.617 | 0.327 | 0.00031 | 1,178 | 0.0087 |
| MT1G | 5.7 | 0.17 | 0.019 | 0.0011 | 3,445 | 0.0064 |
| TNFAIP3 † | 1.55 | 0.894 | 0.749 | 0.0028 | 5 | 0.0785 |
| SBDS | 2.25 | 0.638 | 0.344 | 0.0077 | 13,836 | 0.0028 |
| GNLY † | 0.94 | 0.979 | 0.947 | 0.01 | 10,625 | 0.0037 |
| SYCE2 | 4.73 | 0.128 | 0.012 | 0.013 | 12,125 | 0.0033 |
| CCNL1 | 1.38 | 0.809 | 0.737 | 0.018 | 7,509 | 0.0046 |
| PER1 | 3.21 | 0.34 | 0.11 | 0.031 | 1,121 | 0.0088 |

† Gene that is also part of the persistence signature (TNFAIP3, GNLY).

**S3b. Top 10 ligands by corrected AUPR (143 ligands tested)**

| AUPR rank | Ligand | Corrected AUPR | AUROC | Pearson |
|---|---|---|---|---|
| 1 | LTB | 0.0552 | 0.6633 | 0.0433 |
| 2 | GLG1 | 0.0308 | 0.7457 | 0.0601 |
| 3 | CD40 | 0.0288 | 0.7245 | 0.0876 |
| 4 | TNF | 0.0195 | 0.7758 | 0.0818 |
| 5 | IL1B | 0.0171 | 0.8171 | 0.0888 |
| 6 | CLEC11A | 0.0124 | 0.6447 | 0.0409 |
| 7 | SARAF | 0.011 | 0.7096 | 0.0449 |
| 8 | CD38 | 0.009 | 0.695 | 0.0378 |
| 9 | HMGB1 | 0.0089 | 0.7038 | 0.0504 |
| 10 | TRAF2 | 0.0088 | 0.6643 | 0.0327 |

LTB AUROC rank: 111/143.

**S3c. Rank (weight) of NFKBIA, TNFAIP3 and BTG1 in the target list of the five highest-activity ligands**

| Ligand | BTG1 | NFKBIA | TNFAIP3 |
|---|---|---|---|
| LTB | 31 (w=0.073) | 4 (w=0.080) | 5 (w=0.079) |
| GLG1 | 1,450 (w=0.008) | 13 (w=0.026) | 2 (w=0.030) |
| CD40 | 69 (w=0.142) | 11 (w=0.152) | 4 (w=0.155) |
| TNF | 1,105 (w=0.056) | 13 (w=0.273) | 9 (w=0.277) |
| IL1B | 2,396 (w=0.014) | 19 (w=0.222) | 65 (w=0.192) |

**S3d. Number of genes of the set found in the top-n predicted targets of each ligand**

| Ligand | top 10 | top 25 | top 50 | top 100 | top 250 | top 500 |
|---|---|---|---|---|---|---|
| LTB | 2 | 2 | 3 | 3 | 3 | 3 |
| TNF | 1 | 2 | 2 | 2 | 4 | 5 |
| IL1B | 0 | 1 | 2 | 3 | 4 | 5 |
| GLG1 | 1 | 2 | 2 | 2 | 2 | 3 |
| CD40 | 1 | 2 | 2 | 3 | 3 | 5 |

Removing the two persistence-signature genes of the set (TNFAIP3 and GNLY) leaves NFKBIA (and BTG1 for n ≥ 50) among the top LTB targets.

### Table S4. Receptor detection (cells with expression > 0)

| Set | n cells | CD40 | LTBR | TNFRSF1A |
|---|---|---|---|---|
| CR stable, filtered | 419 | 8/419 (1.9%) | 25/419 (6.0%) | 157/419 (37.5%) |
| RE declining, filtered | 47 | 0/47 (0.0%) | 1/47 (2.1%) | 4/47 (8.5%) |
| RE declining, receiver set (unfiltered) | 120 | 10/120 (8.3%) | 2/120 (1.7%) | 11/120 (9.2%) |

### Table S5. Composition of the CellOracle set (466 cells)

**S5a. Cells per cluster and clinical origin**

| Cluster | CR stable | RE declining |
|---|---|---|
| 0 | 213 | 40 |
| 1 | 99 | 0 |
| 2 | 71 | 7 |
| 3 | 36 | 0 |

**S5b. Cells per cluster and patient** (clusters 1 and 3 are almost single-patient)

| Cluster | CR03 | CR04 | CR05 | CR06 | CR07 | CR08 | CR10 | RE02 | RE03 |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 5 | 1 | 25 | 16 | 27 | 46 | 93 | 37 | 3 |
| 1 | 0 | 94 | 0 | 1 | 0 | 1 | 3 | 0 | 0 |
| 2 | 4 | 15 | 3 | 13 | 14 | 1 | 21 | 7 | 0 |
| 3 | 0 | 1 | 35 | 0 | 0 | 0 | 0 | 0 | 0 |

**S5c. Cells per cluster and timepoint**

| Cluster | 9 wk | 12 wk |
|---|---|---|
| 0 | 193 | 60 |
| 1 | 5 | 94 |
| 2 | 42 | 36 |
| 3 | 0 | 36 |

**S5d. Cells per patient and timepoint**

| Patient | 9 wk | 12 wk |
|---|---|---|
| CR03 | 0 | 9 |
| CR04 | 0 | 111 |
| CR05 | 0 | 63 |
| CR06 | 30 | 0 |
| CR07 | 1 | 40 |
| CR08 | 48 | 0 |
| CR10 | 117 | 0 |
| RE02 | 41 | 3 |
| RE03 | 3 | 0 |

### Table S6. In silico MAFF knockout: predicted NFKBIA change

**S6a. By group (all cells)**

| Group | Mean | SD | Cells |
|---|---|---|---|
| CR stable | −0.0892 | 0.1451 | 419 |
| RE declining | −0.1892 | 0.1659 | 47 |

TNFAIP3 (very small effect):

| Group | Mean | SD | Cells |
|---|---|---|---|
| CR stable | −0.0125 | 0.0243 | 419 |
| RE declining | −0.0165 | 0.0261 | 47 |

**S6b. Controls for composition**

Week-9 cells only (44 of 47 RE cells are from week 9):

| Group | Mean | SD | Cells |
|---|---|---|---|
| CR stable | −0.1009 | 0.1441 | 196 |
| RE declining | −0.1898 | 0.1674 | 44 |

Cluster 0 only:

| Group | Mean | Cells |
|---|---|---|
| CR stable | −0.0663 | 213 |
| RE declining | −0.1499 | 40 |

Per-cluster and group:

| Cluster | Group | Mean | Cells |
|---|---|---|---|
| 0 | CR stable | −0.066 | 213 |
| 0 | RE declining | −0.150 | 40 |
| 1 | CR stable | 0.000 | 99 |
| 2 | CR stable | −0.288 | 71 |
| 2 | RE declining | −0.414 | 7 |
| 3 | CR stable | −0.077 | 36 |

Mean per patient (all CR patients, followed by the two RE patients):

| Patient | Mean | Cells |
|---|---|---|
| CR03 | −0.1572 | 9 |
| CR04 | −0.0422 | 111 |
| CR05 | −0.0804 | 63 |
| CR06 | −0.1426 | 30 |
| CR07 | −0.1648 | 41 |
| CR08 | −0.0458 | 48 |
| CR10 | −0.1107 | 117 |
| RE02 | −0.1989 | 44 |
| RE03 | −0.0471 | 3 |

**S6c. MAFF→NFKBIA edge coefficient per cluster** (absent in cluster 1)

| Cluster | MAFF→NFKBIA edge coefficient |
|---|---|
| 0 | 0.4963 |
| 1 | absent |
| 2 | 0.2857 |
| 3 | 0.1935 |

**S6d. Baseline expression.** Using the CellOracle imputed layer, mean baseline *MAFF* expression was 0.221 in CR stable and 0.349 in RE declining cells. The relative change in *NFKBIA* (sum of predicted change divided by sum of baseline expression) was −4.1% in CR and −7.3% in RE. The predicted *NFKBIA* change correlated with baseline *MAFF* (Spearman ρ = −0.85) and baseline *NFKBIA* (ρ = −0.74) across cells. The RE–CR difference in predicted change was −0.100 before and −0.045 after adjustment for baseline *MAFF* and *NFKBIA* expression (linear model). Among cells in the upper half of baseline *MAFF* expression, the mean change was −0.195 in CR (n = 170) and −0.266 in RE (n = 31). The linear model was fitted at the cell level and ignores clustering within patients. Baseline expression therefore explains about half of the larger decrease in RE cells, and the remaining difference is based almost entirely on one patient (RE02).

### Table S7. Vector field vs randomised control (panel I)

| Metric | Knockout | Randomised control |
|---|---|---|
| Grid points with enough cells | 818 / 1,600 (782 low-mass points masked) | same |
| Median shift magnitude | 0.107 | 0.035 |
| 90th percentile | 0.426 | 0.098 |
| Mean | 0.168 | 0.045 (ratio 3.7×) |
| Points with larger knockout shift | 78% | – |
| Median cosine (knockout vs control direction) | −0.12 | – |

Grid points are spatially correlated; no p-value is reported.

### Table S8. Signature sensitivity analysis (time-matched comparison)

The signature was derived from all persister cells (63% from the peak timepoint) vs IP-restricted cells (all from infusion). To test whether it reflects timepoint, the comparison was repeated with infusion cells only (1,841 persister vs 16,991 IP-restricted cells):

| Metric | Value |
|---|---|
| DE genes (adj. p < 0.05, \|log2FC\| > 0.25) | 737 (vs 1,747 in the pooled comparison) |
| Overlap with original top-50 up genes | 24 / 50 |
| Overlap with original top-50 down genes | 31 / 50 |
| Spearman ρ of log2FC over 496 shared genes | 0.813 |
| *TNFAIP3* in time-matched table | absent |
| *LTB* in time-matched table | present |

The complete table is available in the repository (`tables/persistence_markers_infusion_matched.csv`).

---

## 4. Definitions and data notes

- CR (complete response) and RE (relapse) follow the group labels of the validation dataset. NR and OT are additional labels in the same dataset (671 and 1,656 cells; 3 and 6 patients). Their definitions could not be located in the dataset records, and these patients were not analysed.
- The analysed validation object contains 7,577 cells (CR 3,804, NR 671, OT 1,656, RE 1,446); the study abstract reports 7,578.
- Rows at timepoint 0 (1,706 cells) were excluded from the time-trend analysis, which used the 5,871 cells at weeks ≥ 1.
- Discovery-cohort persister clones contain CAR⁺ and CAR⁻ cells (1,075 of 4,998 persister-class cells are CAR⁺); the validation cohort contains CAR⁺ cells only.
- The cohorts come from separate studies with different protocols (blasts: 10x 5′; see [1], [2], [3]), so projecting the signature onto the validation cohort is not a within-study validation.
- γδ T cells cannot be tracked by αβTCR and are not represented in the clonal analysis [1].

## 5. Extended limitations

1. Few relapse patients (5 in the validation cohort); 44/47 RE cells in the CellOracle set come from one patient (RE02), so patient-level conclusions are not possible.
2. Cells and clones are nested in patients; reported p-values are descriptive.
3. The CR and RE comparison sets were selected with the same persistence-score cutoff and filtered for B-lineage markers; the filter removed 73 of 120 RE receiver cells. Subtypes with B-cell transcriptional features were reported in association with relapse in the source study of GSE162975 [2]. The removed cells may therefore include a B-like CAR-T state in addition to contaminating cells; the present data cannot distinguish these possibilities.
4. *CD40* is not supported by receptor expression in filtered RE cells; *LTB* was selected manually from the AUPR ranking (AUROC rank 111/143) and the NFKBIA/TNFAIP3 signal is shared with other NF-κB-activating ligands.
5. The correlation between edge strength and RE enrichment is based on four clusters, may be confounded by cluster size, and includes two clusters (1 and 3) that come almost entirely from single patients.
6. The knockout effect size scales with baseline expression (Table S6d); no experimental validation is available.
7. The persistence signature is derived from pooled cells including peak-time cells (Table S8).

## 6. Software and reproducibility

| Component | Version |
|---|---|
| R | 4.5.2 |
| Seurat / SeuratObject | 5.5.1 / 5.4.0 |
| scRepertoire | 2.6.2 |
| nichenetr | 2.2.1.1 |
| dplyr / tidyr | 1.2.1 / 1.3.2 |
| ggplot2 / ggtext | 4.0.3 / 0.2.0 |
| Python (plotting session, Colab) | 3.13.16; numpy 2.1.3; pandas 2.2.3; scipy 1.16.3; matplotlib 3.10.0 |
| CellOracle | 0.20.0 (Python 3.10; scanpy 1.9.8) |

Raw data: GEO accessions GSE235760, GSE162975, GSE153697. Prior-knowledge models: NicheNet ligand–target matrix, weighted networks and ligand–receptor network (nichenetr). Large intermediate objects (.rds) are not provided. Scripts in `code/` and derived tables in `tables/` allow the figures to be regenerated.

## 7. References

1. Guerrero-Murillo M et al. *Cell Rep Med* 2024;5:101803 (GSE235760).
2. GEO GSE162975 (CAR19/22 B-ALL cohort); ASH 2023 abstract, *Blood* 2023;142(Suppl 1):4851.
3. Rabilloud T et al. *Nat Commun* 2021;12:865 (GSE153697).
4. Hao Y et al. *Nat Biotechnol* 2024;42:293 (Seurat v5).
5. Yang Q et al. *PLoS Comput Biol* 2025;21:e1012760 (scRepertoire 2).
6. Browaeys R et al. *Nat Methods* 2020;17:159 (NicheNet).
7. Kamimoto K et al. *Nature* 2023;614:742 (CellOracle).

