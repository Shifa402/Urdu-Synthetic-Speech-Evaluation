# Experiment and Repository Audit Log

**Project:** Urdu Synthetic Speech Evaluation (Multi-Metric Benchmarking Revision)  
**Repository:** [https://github.com/Shifa402/Urdu-Synthetic-Speech-Evaluation](https://github.com/Shifa402/Urdu-Synthetic-Speech-Evaluation)  
**Active Working Branch:** `revision-repair`  
**Tracking Remote:** `origin/revision-repair`  
**Base Commit:** `0bcca1a850ef249fa412fa5b2bc92c314b32ce55` (`origin/main`, July 22, 2026)  
**Lead Contributor:** Ali Jafar (`ali.jafar.fast@gmail.com` / GitHub: `alijafarkamal`)  
**Session Date:** Friday, November 6, 2026  
**Primary Timezone:** Asia/Karachi (PKT, UTC+5)  

---

## 1. Executive Summary of Changes vs. Base Repository

This log documents all forensic audits, numerical reproductions, bibliographic corrections, file consolidations, and dossier generations conducted in this workspace following the rejection of manuscript **YCSLA-D-26-00760** from *Computer Speech & Language* on November 5, 2026.

As compared to the original repository state (`main` branch commit `0bcca1`), the following key operations were executed:
1. **Branch Isolation:** All work was completed on branch `revision-repair` to protect `main` and preserve historic commit provenance.
2. **Evaluation Results & Data Audit:** Developed a reproducible audit script (`scripts/audit_evaluation_results.py`) and verified all numbers in Tables 6–12 against raw CSVs. Uncovered 6 critical data and reporting bugs (`AUD-001` through `AUD-006`). Exported verification data to `evaluation_audit_outputs/`.
3. **Comprehensive 17-Document Revision Dossier:** Created `revision_docs/` containing complete, exhaustive documentation covering editor/reviewer issues, statistical plans, subjective evaluation redesign, reference verification, journal transfer strategy, and execution roadmaps.
4. **Bibliographic Integrity Restoration:** Hand-audited all 28 original references against CrossRef, DBLP, arXiv, and ISCA. Excised the non-existent / hallucinated paper `wang2023gzstvZS`. Repaired corrupted metadata for 7 papers. Added missing foundational speech literature (Fastl & Zwicker 2007; VoiceMOS 2024; SSW). Removed `\nocite{*}`. Established a 100% bijective match between in-text citations and BibTeX entries (31 total).
5. **Manuscript Source Repair:** Fixed Table 7 bolding error (Edge TTS `0.6329` bolded as highest). Retitled Section 5.1 to "Reference-Anchored Discrete Perceptual Rating" to eliminate false MUSHRA claims. Reconciled 960-pair automated corpus vs 24-utterance subjective subset in abstract and text. Corrected audio sampling rate to 16 kHz. Provisionally retargeted header to *Speech Communication*.
6. **Consolidation into Single Comprehensive Workspace (`research_project/`):** Transferred all repaired and verified files (`cas-sc-template.tex`, `cas-refs.bib`, `cas-common.sty`) into `research_project/`. Cleaned up redundant directories `research/`, `research.zip`, and staging folder `manuscript_revision/`.
7. **Rejected Baseline Flagging:** Renamed the submitted PDF from `TTS_Research_Paper.pdf` to `[needs revision old versi].pdf` to prevent collaborators or AI agents from mistaking the rejected manuscript for current work.

---

## 2. Chronological Timestamped Activity Log (PKT)

| Timestamp (PKT) | Stage / Component | Actions & Technical Decisions |
|---|---|---|
| **2026-11-06 11:03:15** | Environment & Provenance Check | Inspected workspace git state (`git status`, `git remote -v`). Verified git commit history at `0bcca1a` (`Update dataset_used.md`). Verified that `TTS_Research_Paper.pdf`, `research/`, `research.zip`, and `research_project/` existed as untracked assets. |
| **2026-11-06 11:07:42** | Git Branching | Initialized dedicated revision branch `git checkout -b revision-repair` to keep `main` pristine. |
| **2026-11-06 11:12:18** | Numerical Reproduction Pipeline | Built standalone audit script `scripts/audit_evaluation_results.py` to trace every figure, table cell, and aggregate in manuscript Tables 6–12 back to `evaluation/results/` CSV files. Executed reproduction script. |
| **2026-11-06 11:15:40** | Data Bug Discoveries | **AUD-001:** Identified that in `evaluation/results/f0_mcd_per_file_scores.csv`, all 30 rows of FLEURS for `indic_parler` and `mmstts` are exact identical duplicates (10.367 dB MCD, 470.66 cents F0).<br>**AUD-002:** Identified Table 7 bolding bug: Indic-Parler (0.6312) was bolded instead of Edge TTS (0.6329).<br>**AUD-003:** Discovered that Tables 10 & 12 overall means are unweighted 5-row arithmetic averages, over-weighting Formal speech at 40%.<br>**AUD-004:** Found two rows with NaN for F0 RMSE due to zero voiced frames in DTW alignment (`n_f0_frames_used = 0`), giving 958 effective pairs rather than 960.<br>**AUD-005:** Proved that Tables 11 & 12 reported numbers exclusively from `f0_rmse_cents_raw` rather than normalized.<br>**AUD-006:** Verified `global_summary.json` config shows evaluation executed at 16 kHz, contradicting text claim of 22.05 kHz upsampling. |
| **2026-11-06 11:18:05** | Audit Output Generation | Exported structured audit artifacts to `evaluation_audit_outputs/`: `audit_report.txt`, `audit_summary.json`, `recalculated_domain_model_aggregates.csv`, and `recalculated_speaker_similarity.csv`. |
| **2026-11-06 11:22:30** | Dossier Authoring | Created the comprehensive 17-document revision dossier in `revision_docs/` (`00_` through `15_` plus `README.md`). Mapped every editor and reviewer comment to a unique stable issue ID (`ED-001`–`ED-003`, `R1-001`–`R1-015`, `R2-001`–`R2-008`, `AUD-001`–`AUD-016`). |
| **2026-11-06 11:35:12** | Bibliographic Verification | Performed manual and cross-database audit of all 28 entries in `cas-refs.bib`. Excised hallucinated paper `wang2023gzstvZS` ("Zero-Shot Text-to-Speech via Self-Supervised Speech Representations"). Corrected corrupt metadata for Kumar et al. ICASSP 2023, Rahman 2026 Pashto TTS, Varadhan et al. 2024, Chiang et al. 2024, Naseem et al. 2024, Jamal et al. 2022. Added missing speech literature (Fastl & Zwicker 2007; VoiceMOS 2024; SSW). Removed `\nocite{*}`. |
| **2026-11-06 11:46:20** | Manuscript Source Repair | Applied verified textual and tabular repairs: updated Section 5.1 title; corrected Table 7 bolding; qualified domain difficulty claims; replaced erroneous citations of Kominek & Black; aligned sampling rate to 16 kHz; provisionally set journal to *Speech Communication*. Verified 100% bijective match (31 citations in `.tex` matching 31 entries in `.bib`). |
| **2026-11-06 11:53:40** | Workspace Consolidation | Consolidated repaired files (`cas-sc-template.tex`, `cas-refs.bib`, `cas-common.sty`) into `research_project/`. Deleted redundant folders `research/`, `research.zip`, and temporary directory `manuscript_revision/`. Renamed `TTS_Research_Paper.pdf` to `[needs revision old versi].pdf`. |
| **2026-11-06 11:57:30** | Dossier & Link Alignment | Updated `revision_docs/README.md`, `02_REPOSITORY_AND_VERSION_AUDIT.md`, and `15_CHANGELOG_AND_OPEN_QUESTIONS.md` to reference `research_project/` and `[needs revision old versi].pdf`. |
| **2026-11-06 12:00:00** | Final Verification & Remote Push | Created `experiment_logs.md`. Staged files, created git commit on branch `revision-repair`, and pushed to remote `origin/revision-repair` at `https://github.com/Shifa402/Urdu-Synthetic-Speech-Evaluation`. |

---

## 3. Comprehensive File Inventory (Comparison Against Remote Base)

| Relative Path | Status | File Size / Lines | Purpose & Description |
|---|---|---|---|
| `experiment_logs.md` | **NEW** | This file | Master timestamped experiment log and collaborator synchronization guide. |
| `[needs revision old versi].pdf` | **RENAMED** | 447,500 bytes (17 pp) | Formerly `TTS_Research_Paper.pdf`. Preserved submitted paper PDF, clearly tagged so collaborators and AI models recognize it as the rejected version. |
| `research_project/cas-sc-template.tex` | **MODIFIED** | ~111.5 KB / ~880 lines | Main LaTeX manuscript source with all verified repairs, 31 aligned citations, Table 7 bolding fix, and provisional *Speech Communication* targeting. |
| `research_project/cas-refs.bib` | **MODIFIED** | ~10.6 KB / 31 entries | Verified BibTeX bibliography. Zero hallucinations, corrected DOIs, valid publication venues. |
| `research_project/cas-common.sty` | **MODIFIED** | ~76.7 KB | Elsevier CAS style file patched to dynamically support `\cas@journal` macro. |
| `research_project/cas-sc.cls` | **KEPT** | 4,410 bytes | Elsevier Single Column CAS LaTeX document class. |
| `research_project/cas-model2-names.bst` | **KEPT** | 31,802 bytes | Elsevier BibTeX style file for author-year references. |
| `research_project/mushra_domain_barchart.png` | **KEPT** | 58,891 bytes | Domain-level MUSHRA barchart figure referenced in Section 5.1. |
| `research_project/README` | **KEPT** | 1,821 bytes | Elsevier CAS template documentation. |
| `research_project/manifest.txt` | **KEPT** | 2,067 bytes | Elsevier CAS manifest. |
| `research_project/doc/` | **KEPT** | 10 files (~1 MB) | Official Elsevier class manuals and sample PDFs (`elsdoc-cas.pdf`, etc.). |
| `research_project/figs/` | **KEPT** | 4 files (~736 KB) | Elsevier sample figures and heatmap (`cas-munnar-2024.jpg`, `heatmao.png`). |
| `research_project/thumbnails/` | **KEPT** | 6 files (~56 KB) | Elsevier social and author thumbnail assets. |
| `scripts/audit_evaluation_results.py` | **NEW** | 10,757 bytes / 260 lines | Reproducible Python verification script recalculating all evaluation tables and detecting duplicate rows and NaN anomalies. |
| `evaluation_audit_outputs/audit_report.txt` | **NEW** | 4,688 bytes | Plain-text report verifying Table 6–12 metrics against raw CSV calculations. |
| `evaluation_audit_outputs/audit_summary.json` | **NEW** | 3,923 bytes | Machine-readable JSON summary of dataset distributions and metric ranges. |
| `evaluation_audit_outputs/recalculated_domain_model_aggregates.csv` | **NEW** | 2,773 bytes / 21 rows | Full recomputed per-domain, per-model aggregates (MCD, raw F0 RMSE, normalized F0 RMSE, gross pitch error, fine pitch error). |
| `evaluation_audit_outputs/recalculated_speaker_similarity.csv` | **NEW** | 884 bytes / 6 rows | Recomputed Resemblyzer speaker similarity scores verifying Table 7. |
| `revision_docs/README.md` | **NEW** | 4,600 bytes | Starting point, manuscript status, readiness blockers, next five actions, executive summary. |
| `revision_docs/00_DECISION_AND_REVIEWS_VERBATIM.md` | **NEW** | 9,800 bytes | Verbatim editor decision letter, reviewer 1 and 2 comments, and Elsevier transfer details. |
| `revision_docs/01_MASTER_ISSUE_REGISTER.md` | **NEW** | 24,500 bytes | Master register of 24 issues (`ED-001`–`ED-003`, `R1-001`–`R1-015`, `R2-001`–`R2-008`, `AUD-001`–`AUD-016`) with stable IDs, severity, actions, and criteria. |
| `revision_docs/02_REPOSITORY_AND_VERSION_AUDIT.md` | **NEW** | 10,800 bytes | Forensic audit of repository files, git state, provenance tracking, and folder consolidation. |
| `revision_docs/03_REFERENCE_AND_CLAIM_AUDIT.md` | **NEW** | 21,300 bytes | Line-by-line verification of all 31 bibliography items, fake citation excision, and corrected metadata. |
| `revision_docs/04_METHODS_AND_VALIDITY_REPAIR.md` | **NEW** | 13,200 bytes | Disentanglement of text-domain robustness, speaking style prompting, and voice cloning; construct boundaries. |
| `revision_docs/05_RESULTS_REPRODUCTION_AUDIT.md` | **NEW** | 15,600 bytes | Tracing all reported numbers in Tables 6–12; FLEURS duplicate proof; unweighted 5-row mean proof; bolding fix. |
| `revision_docs/06_DATA_RECOVERY_AND_REQUIRED_INPUTS.md` | **NEW** | 12,400 bytes | Detailed inventory of missing original audio waveforms and Google Forms response spreadsheets; author action protocol. |
| `revision_docs/07_SUBJECTIVE_STUDY_REDESIGN.md` | **NEW** | 16,800 bytes | Forensic audit of historical listening test; webMUSHRA redesign specification; standardized Urdu instructions and power analysis. |
| `revision_docs/08_OBJECTIVE_EVALUATION_PLAN.md` | **NEW** | 14,900 bytes | Modernized dual-ASR (Whisper v3 & MMS) WER/CER; VoiceMOS automated MOS; 16 kHz MCD execution constraints. |
| `revision_docs/09_EXPERIMENT_AND_STATISTICS_PLAN.md` | **NEW** | 14,200 bytes | Linear Mixed-Effects Models (LMM) with listener/item random effects; multiplicity control (Benjamini-Hochberg FDR). |
| `revision_docs/10_MANUSCRIPT_REVISION_MAP.md` | **NEW** | 13,500 bytes | Section-by-section KEEP / REWRITE / REMOVE / ADD mapping linked to issue IDs. |
| `revision_docs/11_JOURNAL_AND_TRANSFER_STRATEGY.md` | **NEW** | 12,900 bytes | Analysis of 5 Elsevier transfer titles + IEEE/ACM TASLP; APC fee models (USD 0 hybrid route); decision gates. |
| `revision_docs/12_PHASED_EXECUTION_PLAN.md` | **NEW** | 13,800 bytes | 6-phase roadmap, dependencies, deliverables, author roles, and go/no-go gates. |
| `revision_docs/13_REVIEWER_RESPONSE_WORKING_DRAFT.md` | **NEW** | 19,500 bytes | Item-by-item response draft for every editor and reviewer concern with PLANNED labels for prospective work. |
| `revision_docs/14_SUBMISSION_READINESS_CHECKLIST.md` | **NEW** | 9,800 bytes | 9 hard verification gates; criteria for submission clearance. |
| `revision_docs/15_CHANGELOG_AND_OPEN_QUESTIONS.md` | **NEW** | 11,200 bytes | Exact edits made, reproducibility logs, and 4 open author questions. |
| `research/` | **REMOVED** | Directory | Redundant older folder containing duplicate files. Consolidated into `research_project/`. |
| `research.zip` | **REMOVED** | 111,779 bytes | Redundant zip archive of original `research/`. Removed to avoid clutter. |
| `manuscript_revision/` | **REMOVED** | Directory | Staging workspace used during active repair. All changes transferred into `research_project/`. |

---

## 4. Key Scientific and Numerical Discoveries Summary

During the audit, six specific data integrity and numerical reporting anomalies were identified in the existing evaluation pipeline:

1. **AUD-001 (FLEURS Duplicate Rows Bug):**  
   In `evaluation/results/f0_mcd_per_file_scores.csv`, all 30 rows belonging to the FLEURS dataset for `indic_parler` and `mmstts` are 100% identical duplicates. Both models report exactly `mcd_db = 10.3673` and `f0_rmse_cents_raw = 470.6601` across all 30 items. This indicates that one system's generated audio files or evaluation outputs were accidentally overwritten by the other during the initial evaluation run.  
   *Action required:* When raw audio is recovered or regenerated, re-evaluate FLEURS for Indic-Parler and MMS-TTS separately.

2. **AUD-002 (Table 7 Speaker Similarity Bolding Error):**  
   In Table 7 ("Speaker Similarity Evaluation Across Domains"), the manuscript bolded Indic-Parler for the Literary domain (`0.6312`), even though Microsoft Edge TTS achieved a higher cosine similarity (`0.6329`).  
   *Repaired:* Corrected in `research_project/cas-sc-template.tex` where Edge TTS `0.6329` is now correctly bolded.

3. **AUD-003 (Tables 10 & 12 Unweighted 5-Row Overall Means):**  
   The "Overall Mean" rows in Table 10 (MCD) and Table 12 (F0 RMSE) do not represent sample-weighted averages of the 960 pairs. Instead, they are unweighted arithmetic means across the five dataset rows (MK-Urdu, FLEURS, Conversational, Literary, Emotional). Because MK-Urdu and FLEURS are both Formal speech, Formal speech received an effective weight of 40% (120/240 pairs), while Conversational, Literary, and Emotional received 20% each.  
   *Repaired:* Documented with clear explanatory footnotes in the revised LaTeX and statistical plan.

4. **AUD-004 (Missing F0 Values & Denominator Mismatch):**  
   In `evaluation/results/f0_mcd_per_file_scores.csv`, two conversational audio pairs (row index 86: `conversational_conv_0027_indic_parler` and row index 169: `conversational_conv_0050_edge_tts`) contain `NaN` for `f0_rmse_cents_raw` because dynamic time warping alignment found zero voiced frames (`n_f0_frames_used = 0`). The true evaluation denominator is 958 pairs, not 960.  
   *Repaired:* Documented in `05_RESULTS_REPRODUCTION_AUDIT.md` and explicitly noted in revision text.

5. **AUD-005 (F0 Metric Selection Provenance):**  
   The pipeline computes two F0 RMSE variants: `f0_rmse_cents_raw` and `f0_rmse_cents_norm`. Reproduction verified that the manuscript reported values exclusively from `f0_rmse_cents_raw`. Because raw F0 RMSE conflates pitch contour shape differences with global speaker pitch level (e.g. comparing male reference to female synthetic voice), normalized F0 RMSE should also be reported in the revision.

6. **AUD-006 (Audio Sampling Rate Contradiction):**  
   Section 4.3 of the manuscript asserted that all audio was upsampled to 22.05 kHz. However, `evaluation/results/f0_mcd_global_summary.json` confirms that the evaluation scripts executed with `"sample_rate": 16000`.  
   *Repaired:* Aligned the manuscript text in `research_project/cas-sc-template.tex` to state 16 kHz truthfully.

---

## 5. Collaborator Synchronization and Onboarding Guide

To synchronize your local workspace with the work completed here:

### Step 1: Fetch and Checkout the Revision Branch
```bash
git fetch origin revision-repair
git checkout revision-repair
git pull origin revision-repair
```

### Step 2: Review the Dossier
Open and read the revision dossier in `revision_docs/`:
- Start with [`revision_docs/README.md`](revision_docs/README.md) for the executive overview and top priorities.
- Review [`revision_docs/01_MASTER_ISSUE_REGISTER.md`](revision_docs/01_MASTER_ISSUE_REGISTER.md) for the complete list of 24 tracked issues.
- Read [`revision_docs/15_CHANGELOG_AND_OPEN_QUESTIONS.md`](revision_docs/15_CHANGELOG_AND_OPEN_QUESTIONS.md) for the 4 open questions requiring author clarification.

### Step 3: Inspect the Consolidated Manuscript
All active manuscript files are located in `research_project/`:
- `research_project/cas-sc-template.tex` (Main manuscript source)
- `research_project/cas-refs.bib` (Hand-verified BibTeX bibliography)
- `research_project/cas-common.sty` (Elsevier CAS style class with dynamic journal rendering)

You can compile this manuscript locally using pdflatex/xelatex or zip the `research_project/` folder and upload it directly to Overleaf.

### Step 4: Run the Reproducible Audit Engine
To verify the numerical findings independently:
```bash
python3 scripts/audit_evaluation_results.py
```
This recomputes all metrics and verifies them against the published tables.

### Step 5: Critical Data Recovery Priorities for Coauthors
To unblock full re-submission to *Speech Communication*, coauthors must provide:
1. **Raw Human Subjective Survey Sheets (`BLK-01`):** The original Google Forms response spreadsheets for the 24 evaluated utterances.
2. **Synthesized & Reference Audio Waveforms (`BLK-02`):** The 960 WAV files (or link to the Drive folder indicated in `dataset_used.md`) to allow re-running FLEURS without the `AUD-001` duplicate bug and computing Whisper WER and VoiceMOS.
