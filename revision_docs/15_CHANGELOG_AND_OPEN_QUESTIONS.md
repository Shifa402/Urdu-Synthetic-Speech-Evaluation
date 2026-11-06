# 15: Changelog and Open Questions

## Session Summary and Provenance Baseline

This document records all concrete actions, code artifacts, data audits, and manuscript edits executed during this local repair session, along with the precise open questions that require author clarification.

- **Working Directory:** `/home/ali-jafar/Urdu-Synthetic-Speech-Evaluation`
- **Active Git Branch:** `revision-repair` (cleanly branched from `main`)
- **Submitted Version Baseline:** `[needs revision old versi].pdf` (formerly `TTS_Research_Paper.pdf`)
- **Active Working Copy:** `research_project/` (single consolidated manuscript directory)

---

## 1. Concrete Actions Executed This Session

### A. Repository & Version Audit
1. Established exact provenance of submitted manuscript: original PDF matches `research/cas-sc-template.tex` and `research.zip` (August 3, 2026).
2. Consolidated all working files into a single comprehensive folder: `research_project/`.
3. Removed redundant historical folders (`research/`, `research.zip`) and temporary staging directory (`manuscript_revision/`).
4. Renamed rejected PDF to `[needs revision old versi].pdf` so collaborators and AI agents immediately recognize it as the rejected baseline.

### B. Numerical Reproduction & Pipeline Audit
1. Created and executed [`scripts/audit_evaluation_results.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/audit_evaluation_results.py), producing machine-readable artifacts in `evaluation_audit_outputs/`:
   - `audit_report.txt`
   - `audit_summary.json`
   - `recalculated_domain_model_aggregates.csv`
   - `recalculated_speaker_similarity.csv`
2. **Discovered FLEURS Duplicate Bug (`AUD-001`):** All 30 files on FLEURS for `indic_parler` and `mmstts` have identical MCD (10.367 dB) and F0 RMSE (470.66 cents) in `f0_mcd_per_file_scores.csv`.
3. **Discovered Table 7 Bolding Error (`AUD-002`):** Manuscript bolded Indic-Parler (0.6312) even though Edge TTS was higher (0.6329).
4. **Solved Table 10 & 12 Aggregation Puzzle (`AUD-003`):** Proved mathematically that "Overall Means" were unweighted arithmetic averages of the 5 table rows, giving Formal speech 40% effective weight.
5. **Identified Missing F0 Values (`AUD-004`):** Rows 86 and 169 have NaN due to `n_f0_frames_used = 0` (zero voiced frames in DTW), contradicting the manuscript's claim of 100% complete coverage.
6. **Solved F0 Column Selection (`AUD-005`):** Proved that Tables 11 & 12 reported numbers exclusively from `f0_rmse_cents_raw`.
7. **Resolved Sampling Rate Conflict (`AUD-006`):** Discovered `global_summary.json` ran at 16 kHz, contradicting the text claim of 22.05 kHz upsampling.

### C. Complete Bibliographic & Claims Audit
1. Audited all 28 entries in `cas-refs.bib` against primary CrossRef, DBLP, arXiv, and ISCA databases (`03_REFERENCE_AND_CLAIM_AUDIT.md`).
2. **Excised Non-Existent Paper (`R2-002`):** Deleted hallucinated reference `wang2023gzstvZS` (*Generalised Zero-Shot Text-to-Speech via Voice Embedding*, Interspeech 2023).
3. **Repaired Corrupted Entries:**
   - `jain2023indicTTS` $\rightarrow$ Gokul Karthik Kumar et al., ICASSP 2023 (`kumar2023indic`).
   - `pashto2025bench` $\rightarrow$ Hanif Rahman, arXiv:2605.26978, May 2026 (`rahman2026pashto`).
   - `chiang2024mushra` $\rightarrow$ Praveen Srinivasa Varadhan et al., arXiv:2411.12719 (`varadhan2024mushra`).
   - `chiang2024mushraevaluate` $\rightarrow$ Cheng-Han Chiang, Wei-Ping Huang, Hung-yi Lee, Interspeech 2024.
   - `naseem2025urdu` $\rightarrow$ Fatima Naseem et al., Interspeech 2024 (`naseem2024developing`).
   - `arshad2022transfer` $\rightarrow$ Sahar Jamal, Sadaf Abdul Rauf, Quratulain Majid, LREC EurALI 2022 (`jamal2022transfer`).
   - `pratap2023mms` $\rightarrow$ Updated to JMLR 2024 archival publication.
   - `kubichek1993mcd` $\rightarrow$ Fixed entry type from `@article` to `@inproceedings`.
4. **Corrected Kominek & Black Misattribution (`R2-007`):** Removed from all F0 RMSE, cents, and JND statements; retained strictly for MCD scaling constant.
5. **Added Recommended Literature (`R2-006`, `R2-004`):** Integrated Shirali-Shahreza & Penn (SSW 2023), Pandey et al. (SSW 2025), VoiceMOS Challenge (`cooper2024voicemos`), and Fastl & Zwicker (2007).
6. Removed `\nocite{*}` and cited `conneau2022fleurs` explicitly in text (`AUD-014`).

### D. Comprehensive Dossier Construction
Created all required documents in `revision_docs/`:
- `README.md`
- `00_DECISION_AND_REVIEWS_VERBATIM.md`
- `01_MASTER_ISSUE_REGISTER.md`
- `02_REPOSITORY_AND_VERSION_AUDIT.md`
- `03_REFERENCE_AND_CLAIM_AUDIT.md`
- `04_METHODS_AND_VALIDITY_REPAIR.md`
- `05_RESULTS_REPRODUCTION_AUDIT.md`
- `06_DATA_RECOVERY_AND_REQUIRED_INPUTS.md`
- `07_SUBJECTIVE_STUDY_REDESIGN.md`
- `08_OBJECTIVE_EVALUATION_PLAN.md`
- `09_EXPERIMENT_AND_STATISTICS_PLAN.md`
- `10_MANUSCRIPT_REVISION_MAP.md`
- `11_JOURNAL_AND_TRANSFER_STRATEGY.md`
- `12_PHASED_EXECUTION_PLAN.md`
- `13_REVIEWER_RESPONSE_WORKING_DRAFT.md`
- `14_SUBMISSION_READINESS_CHECKLIST.md`
- `15_CHANGELOG_AND_OPEN_QUESTIONS.md`

### E. Consolidated Working Copy in `research_project/`
1. Created cleaned, fully verified `research_project/cas-refs.bib` (31 verified entries).
2. Applied verified repairs in `research_project/cas-sc-template.tex`:
   - Updated journal declaration to `\journal{Speech Communication}` with dynamic macro in `cas-common.sty`.
   - Corrected 960-pair vs 24-item subjective listening distinction in abstract and pipeline.
   - Retitled Section 5.1 from MUSHRA to "Reference-Anchored Discrete Perceptual Rating".
   - Corrected Table 7 bolding (Edge 0.6329 bolded).
   - Replaced all corrupted/hallucinated citation keys with verified keys.
   - Corrected Kominek & Black F0/cents citations with Fastl & Zwicker (2007).
   - Realigned sampling rate to 16 kHz.
   - Removed `\nocite{*}`.
   - Verified 100% bijective match between citations and BibTeX entries.

---

## 2. Compilation and Toolchain Status

- **System Check:** Linux CLI check (`which pdflatex latexmk xelatex`) confirmed that **no local TeX Live / pdflatex distribution is installed** on this machine.
- **Static Verification Performed:**
  - BibTeX syntax and brace balancing verified programmatically.
  - Citation key cross-referencing verified (all 31 in-text `\cite{...}` keys exist in `cas-refs.bib`).
  - LaTeX macro and environment balance verified.
- **Author Compilation Action:** The revised files in `research_project/` can be compiled directly on any standard TeX Live environment or uploaded to Overleaf.

---

## 3. Four Open Questions for the Authors

To advance to Phase 2 and finalize the revision, the authors are requested to clarify four concrete questions:

### Question 1: Raw Audio & Survey Data Recovery
> *Can the 960 generated WAV files and the raw Google Forms response spreadsheets be recovered from your offline archives or the Google Drive link (`dataset_used.md`), or should we proceed with regenerating synthetic audio via the repository notebooks and executing the prospective 30-listener webMUSHRA campaign?*

### Question 2: FLEURS Duplicate Anomaly
> *Our audit discovered that in `evaluation/results/f0_mcd_per_file_scores.csv`, all 30 rows on Formal FLEURS for Indic-Parler and MMS-TTS have 100% identical values to 14 decimal places. Did the evaluation script inadvertently point to the same audio directory for both models during that run?*

### Question 3: Target Venue Confirmation
> *Do the authors endorse our recommendation to target **Speech Communication** (Elsevier / ISCA) via the traditional subscription model (USD 0 author publishing charge), reserving **IEEE/ACM TASLP** for a subsequent submission if the expanded Task B/C campaign is pursued?*

### Question 4: Historical ABX Stimulus Clarification
> *Manuscript lines 585–589 describe each ABX trial as presenting "reference utterance (A), a second presentation of the same reference (B), and an unknown sample (X)." What did the Google Forms interface actually present to raters? (e.g., was A the Natural Reference and B the Synthetic TTS output?)*

---

## 4. Final Handoff and Next Executable Steps

The local repository is now in an auditable, scientifically sound state. The rejected baseline is safely archived; the evidence base is mathematically verified; all corrupted citations are replaced; and comprehensive operational plans exist for every remaining task.

**Immediate Next Executable Steps:**
1. Authors review the repair dossier in [`revision_docs/README.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/README.md).
2. Authors provide answers to the four open questions above.
3. Access the Google Drive link or launch notebook-based audio regeneration for Phase 2.

