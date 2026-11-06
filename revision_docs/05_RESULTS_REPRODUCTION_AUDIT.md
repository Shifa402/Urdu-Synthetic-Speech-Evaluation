# 05: Results Reproduction Audit

## Audit Overview & Traceability Methodology

This document establishes the end-to-end numerical traceability of every table, figure, and quantitative claim reported in the rejected manuscript against the underlying data files and scripts available in `/home/ali-jafar/Urdu-Synthetic-Speech-Evaluation`.

The reproduction audit was conducted using our standalone, reproducible script:  
[`scripts/audit_evaluation_results.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/audit_evaluation_results.py), which generated full verification logs in `evaluation_audit_outputs/`.

---

## 1. Table-by-Table Reproduction Status Register

| Table / Figure | Description | Local Source Data File | Reproduction Status | Key Numerical / Procedural Finding |
|---|---|---|---|---|
| **Abstract** | Quantitative claims (960 pairs, 12.03 dB MCD, 889 cents F0) | `evaluation/results/f0_mcd_per_domain_summary.csv` | **PARTIALLY REPRODUCED** | 960 rows exist, but F0 RMSE has only 958 finite values. 12.03 dB and 888.54 cents verified from raw F0 column. |
| **Table 1** | Architectural properties of 4 TTS systems | Qualitative text / Notebooks | **VERIFIED** | Accurate specifications, but Hugging Face checkpoint links and sampling configs were missing in text. |
| **Table 2** | Summary of evaluation metrics | Qualitative text | **REVISED** | Conceptual error: "Speaker identity preservation" must be demoted to acoustic embedding distance. |
| **Table 3** | Key software components & versions | Qualitative text | **DISCREPANCY** | Stated MCD resampled at 22.05 kHz; JSON config proves evaluation was run at 16 kHz. |
| **Figure X / Chart**| Domain-level MUSHRA scores (`mushra_domain_barchart.png`) | Image file only | **UNVERIFIABLE** | Raw listener ratings absent from repository; cannot re-generate figure from data. |
| **Table 4** | Per-system mean MUSHRA-style scores (1–5) | Text only (lines 884–894) | **UNVERIFIABLE** | **Publication Blocker:** No raw Google Forms CSV export exists in repository. |
| **Table 5** | ABX discrimination accuracy (90.7%) | Text only (lines 931–940) | **UNVERIFIABLE & FLAWED** | Raw survey responses absent. Protocol text describes impossible "A and B identical reference" matching. |
| **Table 6** | Domain-level Resemblyzer similarity | Domain CSV files | **REPRODUCED** | Values closely match cross-domain aggregates from domain CSVs. |
| **Table 7** | Per-system Resemblyzer cosine similarity | Domain CSV files | **REPRODUCED WITH ERROR** | **Integrity / Formatting Error:** Indic-Parler (0.6312) was bolded despite Edge TTS (0.6329) being higher! |
| **Table 8** | Emotion category Resemblyzer similarity | `Emotional/csv_files/*.csv` | **REPRODUCED** | Sad=0.5618, Fear=0.5516, Anger=0.5480, Disgust=0.5395, Happy=0.5350, Boredom=0.5283. |
| **Table 9** | Domain-level mean MCD (dB) | `f0_mcd_per_domain_summary.csv` | **EXACT MATCH** | Conv=6.90 (SD 1.76), Lit=7.87 (SD 1.56), Form=9.12 (SD 1.79), Emot=12.03 (SD 2.69). |
| **Table 10** | Per-system mean MCD (dB) | `f0_mcd_per_domain_tts_model_summary.csv` | **REPRODUCED WITH DISCOVERIES** | (1) Duplicate FLEURS data between Indic & MMS (10.37 dB); (2) Overall mean is an unweighted average of 5 table rows. |
| **Table 11** | Domain-level mean F0 RMSE (cents) | `f0_mcd_per_domain_summary.csv` | **EXACT MATCH ON RAW COLUMN** | Matches `f0_rmse_cents_raw` exactly: Lit=521.24, Form=520.98, Conv=546.02, Emot=888.54. |
| **Table 12** | Per-system mean F0 RMSE (cents) | `f0_mcd_per_domain_tts_model_summary.csv` | **REPRODUCED WITH DISCOVERIES** | (1) Duplicate FLEURS data between Indic & MMS (470.66 cents); (2) Reports `f0_rmse_cents_raw`; (3) 5-row unweighted mean. |

---

## 2. In-Depth Audit of Critical Numerical Discoveries

### Discovery 1: Exact Duplicate Data on Formal FLEURS (Indic-Parler vs MMS-TTS)
A file-by-file comparison of `evaluation/results/f0_mcd_per_file_scores.csv` reveals a severe data integrity artifact:
- For all 30 files in `formal_subset == 'fleurs'`, the calculated `mcd_db`, `f0_rmse_cents`, and `f0_rmse_cents_raw` values for `indic_parler` and `mmstts` are **100% identical to 14 decimal places**:
  - `mcd_db`: 10.36745760315014 dB (all 30 files identical).
  - `f0_rmse_cents_raw`: 470.6585218487355 cents (all 30 files identical).
  - `fastdtw_dist`: identical.
- In Table 10, the authors reported:
  - `Formal (FLEURS)`: Indic-Parler-TTS = 10.37 dB, MMS-TTS = 10.37 dB.
- In Table 12, the authors reported:
  - `Formal (FLEURS)`: Indic-Parler-TTS = 470.66 cents, MMS-TTS = 470.66 cents.
- **Root Cause Analysis:** In the uncommitted scoring script, the audio path or evaluation loop for MMS-TTS on FLEURS accidentally processed or copied the Indic-Parler FLEURS audio output (or vice-versa).
- **Consequence:** Comparative claims between MMS-TTS and Indic-Parler-TTS on FLEURS speech are completely invalid until audio is regenerated and re-scored.

---

### Discovery 2: Mathematical Derivation of Table 10 & Table 12 "Overall Means"
The manuscript reported overall system means that diverged slightly from the pooled sample means calculated across all 240 files:
- **Table 10 Reported vs Recalculated Pooled Mean (MCD):**
  - Edge TTS: Reported = 7.91 dB | Recalculated Pooled = 7.958 dB | Diff = -0.048 dB
  - Gemini TTS: Reported = 9.79 dB | Recalculated Pooled = 9.811 dB | Diff = -0.021 dB
  - Indic-Parler: Reported = 8.41 dB | Recalculated Pooled = 8.273 dB | Diff = +0.137 dB
  - MMS-TTS: Reported = 9.93 dB | Recalculated Pooled = 9.881 dB | Diff = +0.049 dB

- **Mathematical Proof of Author Derivation:**
  The authors computed the overall mean by taking an **unweighted arithmetic average of the 5 table rows**:
  $$\text{Overall Mean} = \frac{\text{Conv} + \text{Lit} + \text{Form(FLEURS)} + \text{Form(UrduSpeech)} + \text{Emot}}{5}$$
  - Edge: $(5.62 + 6.32 + 7.98 + 7.47 + 12.17) / 5 = 39.56 / 5 = \mathbf{7.912} \rightarrow \mathbf{7.91}$
  - Gemini: $(7.30 + 8.67 + 11.15 + 8.24 + 13.58) / 5 = 48.94 / 5 = \mathbf{9.788} \rightarrow \mathbf{9.79}$
  - Indic-Parler: $(6.44 + 7.09 + 10.37 + 7.51 + 10.62) / 5 = 42.03 / 5 = \mathbf{8.406} \rightarrow \mathbf{8.41}$
  - MMS-TTS: $(8.25 + 9.40 + 10.37 + 9.90 + 11.75) / 5 = 49.67 / 5 = \mathbf{9.934} \rightarrow \mathbf{9.93}$

- **Scientific Consequence:** Because Formal speech was divided into two rows of 30 samples each (FLEURS and UrduSpeech), treating each row equally assigned a **40% weight to Formal speech** (60/150 of row weights) and only 20% weight to Emotional speech (60 samples), rather than the true 25% equal weighting per domain.
- **Resolution:** The revised manuscript must transparently explain this row-averaging convention and present the pooled sample mean ($N=240$) alongside it.

---

### Discovery 3: Identification of Reported F0 Column (`f0_rmse_cents_raw`)
`f0_mcd_per_file_scores.csv` contains two F0 RMSE columns:
1. `f0_rmse_cents` (standard pitch-register aligned)
2. `f0_rmse_cents_raw` (unadjusted absolute frequency differences)

Our audit proved conclusively that **Tables 11 and 12 reported numbers from `f0_rmse_cents_raw`**:
- Table 11 Emotional F0 RMSE: Reported = **888.54 cents** (SD 288.75).
  - Recalculated `f0_rmse_cents_raw` = **888.541 cents** (SD 288.751) $\rightarrow$ **Exact Match**.
  - Recalculated `f0_rmse_cents` (standard) = **620.24 cents** (SD 181.02).
- Table 11 Conversational: Reported = **546.02 cents** (SD 114.25).
  - Recalculated `f0_rmse_cents_raw` = **546.023 cents** (SD 114.25) $\rightarrow$ **Exact Match**.
  - Recalculated `f0_rmse_cents` (standard) = **490.70 cents** (SD 96.12).
- Table 12 Overall System Means also match the 5-row average of `f0_rmse_cents_raw`:
  - Edge: $(500.95 + 505.53 + 570.77 + 482.63 + 765.14) / 5 = 2825.02 / 5 = \mathbf{565.004} \rightarrow \mathbf{565.00}$
  - Gemini: $(555.40 + 537.21 + 620.41 + 490.04 + 1027.44) / 5 = 3230.50 / 5 = \mathbf{646.10}$
  - Indic-Parler: $(592.89 + 550.12 + 470.66 + 541.34 + 915.53) / 5 = 3070.54 / 5 = \mathbf{614.108} \rightarrow \mathbf{614.11}$
  - MMS-TTS: $(535.77 + 492.08 + 470.66 + 521.31 + 846.05) / 5 = 2865.87 / 5 = \mathbf{573.174} \rightarrow \mathbf{573.17}$

**Scientific Consequence:** The manuscript never defined what `f0_rmse_cents_raw` was or why it was chosen over the normalized column. Raw F0 penalizes systems heavily for having an inherently different natural vocal register than the reference speaker.

---

### Discovery 4: Missing F0 Values and Concealed Denominators
In `f0_mcd_per_file_scores.csv`, 960 rows are present and all have `ok = True`. However, two rows contain `NaN` across all F0 metrics:
1. **Row 86:** Domain = Conversational, Model = `gemini`, Stem = `sample_32`.
   - `mcd_db` = 13.366 dB, `n_dtw_frames` = 217, `n_f0_frames_used` = **0**.
   - `f0_rmse_cents` = `NaN`, `f0_rmse_cents_raw` = `NaN`.
2. **Row 169:** Domain = Conversational, Model = `indic_parler`, Stem = `sample_53`.
   - `mcd_db` = 17.310 dB, `n_dtw_frames` = 315, `n_f0_frames_used` = **0**.
   - `f0_rmse_cents` = `NaN`, `f0_rmse_cents_raw` = `NaN`.

**Root Cause:** During dynamic time warping alignment, zero mutually voiced frame pairs were identified between reference and synthetic audio (`n_f0_frames_used = 0`). Consequently, division by zero yielded `NaN`.

**Reporting Failure:** The manuscript stated at line 855: *"All 960 reference--synthetic pairs were evaluated without computation failure, confirming complete corpus coverage."* This was false. The true valid denominator for F0 RMSE is **958 pairs** (240 for Edge and MMS; 239 for Gemini and Indic-Parler).

---

### Discovery 5: Table 7 Speaker Similarity Bolding Inversion
In Table 7 (Line 1021 of `cas-sc-template.tex`):
```latex
\textbf{Overall Mean} & 0.6329 & 0.5956 & \textbf{0.6312} & 0.6093 \\
```
- Column 2 is **Edge TTS** (0.6329).
- Column 4 is **Indic-Parler-TTS** (0.6312).
- Edge TTS achieved the highest overall similarity score (0.6329 > 0.6312), yet the manuscript bolded Indic-Parler-TTS.
- This typo has been corrected in the revision source (`manuscript_revision/cas-sc-template.tex`).

