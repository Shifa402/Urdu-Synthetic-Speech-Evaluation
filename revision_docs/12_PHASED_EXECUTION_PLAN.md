# 12: Phased Execution Plan

## Execution Principles and Realistic Timeline Boundaries

To transition from a rejected manuscript to an evidence-backed, publication-ready revision, work must proceed in structured, verifiable phases. 

> [!WARNING] Realistic Timeline Disclaimer
> The estimated duration of **4 to 6 weeks** is an initial conditional engineering estimate contingent upon author responsiveness, participant recruitment velocity, and institutional review turnaround. It is **not a promise or guaranteed deadline**. Scientific readiness and evidence validity strictly supersede arbitrary calendar targets.

---

## 1. Phased Roadmap Overview

```
+----------------------------------------------------------------------------------------------------+
|                                    REVISION ROADMAP PHASES                                         |
+-------------------+-------------------+--------------------+-------------------+-------------------+
| Phase 1           | Phase 2           | Phase 3            | Phase 4           | Phase 5 & 6       |
| Local Integrity   | Missing Asset     | Objective ASR &    | Subjective Web    | Modeling, Writing |
| & Bib Repair      | Recovery          | VoiceMOS Campaign  | Listening Study   | & Submission Gate |
| (Current Session) | (Weeks 1--2)      | (Weeks 2--3)       | (Weeks 3--4)      | (Weeks 5--6)      |
+-------------------+-------------------+--------------------+-------------------+-------------------+
        |                   |                    |                   |                   |
        v                   v                    v                   v                   v
   [Gate 1 Passed]     [Gate 2 Check]       [Gate 3 Check]      [Gate 4 Check]      [Final Signoff]
   Pristine baseline   Raw data & audio     WER, CER & Auto-MOS 30-rater MUSHRA     Complete draft,
   & verified bib.     located/regenerated. recomputed.         data collected.     verified tables.
```

---

## 2. Phase-by-Phase Task Specifications

### Phase 1: Local Evidence Audit & Integrity Repairs (COMPLETED THIS SESSION)
- **Objective:** Freeze baseline, isolate working copy, audit data artifacts, eliminate corrupted citations, and create complete repair dossier.
- **Completed Deliverables:**
  - Git branch `revision-repair` established.
  - Active revision directory `manuscript_revision/` populated.
  - Reproducible audit script [`scripts/audit_evaluation_results.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/audit_evaluation_results.py) executed; output artifacts generated in `evaluation_audit_outputs/`.
  - Master Issue Register (`01_MASTER_ISSUE_REGISTER.md`) with 25 tracked issues.
  - All 28 bibliography entries audited; 6 corrupted entries repaired, 1 hallucination removed (`03_REFERENCE_AND_CLAIM_AUDIT.md`).
  - Table 7 bolding error corrected in `manuscript_revision/cas-sc-template.tex`.
  - Full 17-document dossier established in `revision_docs/`.
- **Go/No-Go Checkpoint 1 (PASSED):** Baseline provenance secured; zero unverified citations remaining in working bibliography.

---

### Phase 2: Missing Data Recovery & Corpus Verification (Target: Weeks 1–2)
- **Objective:** Locate or regenerate original audio waveforms and recover raw Google Forms response data.
- **Tasks:**
  1. *Action 2.1:* Authors access Google Drive archive (`dataset_used.md` link) or offline storage to retrieve 960 synthetic WAVs + 240 reference WAVs (`BLK-02`).
  2. *Action 2.2:* If audio files are unrecoverable, execute the 21 repository notebooks to regenerate synthetic audio, pinning seeds and logging software versions (`BLK-02 fallback`).
  3. *Action 2.3:* Authors log into Google account to export raw Google Forms survey responses for the 20 historical listeners (`BLK-01`).
  4. *Action 2.4:* Commit acoustic scoring script or implement modular reimplementation in `scripts/evaluate_audio_corpus.py` (`BLK-03`).
- **Suggested Author Roles:** Ali Jafar (data archive retrieval, scoring script); Shifa Yousaf (Google Forms export, demographic verification).
- **Deliverables:** `audio_corpus/` populated with verified 16 kHz WAVs; `data_recovery/raw_listening_responses.csv`.
- **Go/No-Go Checkpoint 2:** If raw human listening data cannot be recovered, the authors must commit to the prospective listening study (Phase 4) rather than attempting to publish unreproducible numbers.

---

### Phase 3: Objective Evaluation Expansion (Target: Weeks 2–3)
- **Objective:** Implement modern speech recognition and automated quality prediction pipelines.
- **Tasks:**
  1. *Action 3.1:* Implement Urdu text normalizer module ([`scripts/urdu_text_normalizer.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/urdu_text_normalizer.py)) covering Unicode NFC, Yeh/Kaf unification, and diacritic stripping (`R1-006`).
  2. *Action 3.2:* Run Whisper-large-v3 and MMS-ASR-Urdu on both reference audio ($WER_{\text{ref}}$) and synthetic audio ($WER_{\text{syn}}$) across all 960 utterances (`R1-006`).
  3. *Action 3.3:* Recompute standardized 16 kHz MCD and register-adjusted F0 RMSE, resolving the FLEURS Indic/MMS duplicate anomaly (`AUD-001`, `R1-009`).
  4. *Action 3.4:* Screen audio corpus through pre-trained UTMOS and NISQA v2.0 estimators (`R2-004`).
- **Suggested Author Roles:** Amal Sarmad (ASR pipeline implementation); Ali Jafar (acoustic scoring & normalizer).
- **Deliverables:** `evaluation_results_modern/asr_wer_cer_summary.csv`; `evaluation_results_modern/acoustic_mcd_f0_standardized.csv`.
- **Go/No-Go Checkpoint 3:** ASR baseline on natural speech established; automated metrics complete without missing denominators.

---

### Phase 4: Subjective Listening Study Campaign (Target: Weeks 3–4)
- **Objective:** Conduct a standardized, screened listening evaluation resolving all MUSHRA and construct validity criticisms.
- **Tasks:**
  1. *Action 4.1:* Deploy webMUSHRA interface or standardized Multi-Attribute Rating test with verified Urdu verbatim instructions (`R1-011`, `R2-006`).
  2. *Action 4.2:* Recruit $N = 30$ native Urdu raters with mandatory headphone screening and language background checks (`AUD-011`).
  3. *Action 4.3:* Collect continuous naturalness, intelligibility, and domain appropriateness ratings across balanced randomized blocks (`R2-006`).
  4. *Action 4.4:* Execute automated post-screening exclusion ($<90$ hidden reference rating gate).
- **Suggested Author Roles:** Shifa Yousaf (participant recruitment, session coordination); Maryam Bashir (ethical compliance, institutional review).
- **Deliverables:** `data_collection/subjective_ratings_screened_tidy.csv`.
- **Go/No-Go Checkpoint 4:** Minimum 25 screened listeners complete full randomized blocks; hidden reference post-screening successfully executed.

---

### Phase 5: Statistical Modeling & Data Synthesis (Target: Weeks 4–5)
- **Objective:** Estimate hierarchical mixed-effects models and test formal experimental hypotheses.
- **Tasks:**
  1. *Action 5.1:* Fit Linear Mixed-Effects Models (LMM) with listener and item random intercepts on subjective ratings (`09_EXPERIMENT_AND_STATISTICS_PLAN.md`).
  2. *Action 5.2:* Compute Tukey HSD post-hoc pairwise contrasts and 95% confidence intervals across systems and domains.
  3. *Action 5.3:* Evaluate cross-lingual rank correlation ($\rho$) between VoiceMOS predictions and native Urdu listener scores.
  4. *Action 5.4:* Generate publication-quality figures: forest plots with confidence intervals, ASR error distributions, and correlation scatter plots.
- **Suggested Author Roles:** Ali Jafar (mixed-effects modeling, figure generation); Maryam Bashir (statistical review).
- **Deliverables:** `analysis_outputs/lmm_regression_table.tex`; `analysis_outputs/figures/`.
- **Go/No-Go Checkpoint 5:** All reported effect sizes supported by confidence intervals; no claims asserted on overlapping intervals.

---

### Phase 6: Manuscript Drafting, Internal Review & Submission (Target: Weeks 5–6)
- **Objective:** Finalize LaTeX manuscript, conduct blinded internal review, and prepare submission package for *Speech Communication*.
- **Tasks:**
  1. *Action 6.1:* Update `manuscript_revision/cas-sc-template.tex` with newly verified tables, figures, and bounded discussion.
  2. *Action 6.2:* Conduct comprehensive audit against `14_SUBMISSION_READINESS_CHECKLIST.md`.
  3. *Action 6.3:* Circulate draft among all co-authors for formal approval and authorship confirmation.
  4. *Action 6.4:* Prepare cover letter detailing the comprehensive revision following the CSL rejection.
- **Suggested Author Roles:** All co-authors (review, approval, sign-off).
- **Deliverables:** Final compiled submission PDF; clean source archive; signed author checklist.
- **Final Submission Gate:** 100% of readiness checklist gates passed; corresponding author submits to *Speech Communication*.

