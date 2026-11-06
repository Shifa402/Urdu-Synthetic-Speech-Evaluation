# Urdu TTS Manuscript Repair Dossier

## Starting Point & Executive Overview

This dossier documents the comprehensive forensic audit, evidence verification, and scientific repair of the manuscript:
**"Domain-Specific Evaluation of Text-to-Speech Systems: A Multi-Metric Benchmarking Study"** (Manuscript ID: `YCSLA-D-26-00760`), following its rejection from *Computer Speech & Language* on November 5, 2026.

All work has been conducted locally in `/home/ali-jafar/Urdu-Synthetic-Speech-Evaluation` on git branch `revision-repair`. All repaired, verified manuscript files are consolidated in `research_project/`. The original rejected baseline PDF has been renamed to `[needs revision old versi].pdf` so collaborators and AI tools immediately recognize it as the rejected baseline rather than current work. Redundant temporary directories (`research/`, `research.zip`, `manuscript_revision/`) have been cleaned up.

---

## Current Manuscript Status

- **Status:** **REJECTED** from *Computer Speech & Language* (Not invited for resubmission).
- **Provisional Target Venue:** ***Speech Communication*** (Elsevier / ISCA official journal, Hybrid subscription route = **USD 0 APC**).
- **Aspirational Venue:** ***IEEE/ACM Transactions on Audio, Speech and Language Processing*** (requires full multi-task experimental expansion).
- **Readiness Gate:** **BLOCKED on Hard Data Assets** (Awaiting author recovery of raw audio waveforms and survey response sheets).
- **Integrity Status:** **REPAIRED** (100% of bibliography entries hand-verified; non-existent paper excised; bolding and numerical errors resolved).

---

## Dossier Navigation Index

| Document | Title & Focus | Primary Issues Covered |
|---|---|---|
| [`00_DECISION_AND_REVIEWS_VERBATIM.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/00_DECISION_AND_REVIEWS_VERBATIM.md) | Full editor and reviewer rejection text + Elsevier transfer facts | Baseline reviews |
| [`01_MASTER_ISSUE_REGISTER.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/01_MASTER_ISSUE_REGISTER.md) | Exhaustive catalog of 25 issues with permanent IDs, severity, and acceptance criteria | `ED-001`–`ED-002`, `R1-001`–`R1-015`, `R2-001`–`R2-008`, `AUD-001`–`AUD-016` |
| [`02_REPOSITORY_AND_VERSION_AUDIT.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/02_REPOSITORY_AND_VERSION_AUDIT.md) | Version provenance, diffs between folders, code/notebook inventory, git state | Version control |
| [`03_REFERENCE_AND_CLAIM_AUDIT.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/03_REFERENCE_AND_CLAIM_AUDIT.md) | Line-by-line verification of all 28 references; fake citation excision; corrected DOIs | `R2-001`, `R2-002`, `R2-003`, `R2-007`, `AUD-015`, `AUD-016` |
| [`04_METHODS_AND_VALIDITY_REPAIR.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/04_METHODS_AND_VALIDITY_REPAIR.md) | Disentanglement of default TTS, style prompting, and voice cloning; construct boundaries | `ED-001`, `R1-004`, `R1-005`, `AUD-010` |
| [`05_RESULTS_REPRODUCTION_AUDIT.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/05_RESULTS_REPRODUCTION_AUDIT.md) | Tracing all numbers; FLEURS duplicate discovery; unweighted 5-row mean proof; bolding fix | `AUD-001`, `AUD-002`, `AUD-003`, `AUD-004`, `AUD-005` |
| [`06_DATA_RECOVERY_AND_REQUIRED_INPUTS.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/06_DATA_RECOVERY_AND_REQUIRED_INPUTS.md) | Inventory of missing audio and Google Forms exports; author recovery action protocol | `AUD-013`, `BLK-01`–`BLK-03` |
| [`07_SUBJECTIVE_STUDY_REDESIGN.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/07_SUBJECTIVE_STUDY_REDESIGN.md) | Forensic audit of historical listening test; webMUSHRA redesign; standardized Urdu prompts | `R1-011`, `R1-013`, `R1-014`, `R2-006`, `AUD-011` |
| [`08_OBJECTIVE_EVALUATION_PLAN.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/08_OBJECTIVE_EVALUATION_PLAN.md) | Modernized dual-ASR (Whisper v3 & MMS) WER/CER; VoiceMOS automated MOS; 16 kHz MCD | `R1-006`, `R1-009`, `R2-004`, `AUD-006` |
| [`09_EXPERIMENT_AND_STATISTICS_PLAN.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/09_EXPERIMENT_AND_STATISTICS_PLAN.md) | Linear Mixed-Effects Models (LMM) with listener/item random effects; multiplicity control | Inferential validity |
| [`10_MANUSCRIPT_REVISION_MAP.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/10_MANUSCRIPT_REVISION_MAP.md) | Section-by-section KEEP / REWRITE / REMOVE / ADD mapping linked to issues | Working copy alignment |
| [`11_JOURNAL_AND_TRANSFER_STRATEGY.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/11_JOURNAL_AND_TRANSFER_STRATEGY.md) | Evaluation of 5 Elsevier transfer titles + IEEE TASLP; fee models; decision gates | Publication strategy |
| [`12_PHASED_EXECUTION_PLAN.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/12_PHASED_EXECUTION_PLAN.md) | 6-phase roadmap, dependencies, deliverables, author roles, go/no-go gates | Execution schedule |
| [`13_REVIEWER_RESPONSE_WORKING_DRAFT.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/13_REVIEWER_RESPONSE_WORKING_DRAFT.md) | Item-by-item response draft for every editor and reviewer concern | Reviewer responses |
| [`14_SUBMISSION_READINESS_CHECKLIST.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/14_SUBMISSION_READINESS_CHECKLIST.md) | 9 hard verification gates; criteria for submission clearance | Quality control gates |
| [`15_CHANGELOG_AND_OPEN_QUESTIONS.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/15_CHANGELOG_AND_OPEN_QUESTIONS.md) | Exact edits made, reproducibility logs, 4 open author questions, handoff | Changelog & handoff |

---

## Readiness Blockers for Final Submission

The manuscript **cannot be submitted immediately** due to two hard empirical blockers:
1. **Raw Audio Corpus Absent Locally (`BLK-02`):** Zero WAV files exist in git. Modern objective evaluation (Whisper WER, VoiceMOS) and verification of the FLEURS duplicate anomaly (`AUD-001`) require waveform access.
2. **Raw Listening Test Data Absent Locally (`BLK-01`):** Zero Google Forms response spreadsheets exist in git. Rater variance, demographic distribution, and LMM modeling cannot be performed until the raw response export is provided or a prospective webMUSHRA campaign is completed.

---

## What Was Actually Changed This Session

1. **Git Isolation:** Created branch `revision-repair` without altering commit history.
2. **Consolidated Manuscript Workspace:** Preserved and upgraded `research_project/` as the single authoritative manuscript directory; removed redundant copies (`research/`, `research.zip`, `manuscript_revision/`).
3. **Rejected Baseline Flagging:** Renamed rejected paper PDF to `[needs revision old versi].pdf` to prevent AI agents or coauthors from mistaking it for the active manuscript.
4. **Reproducible Audit Engine:** Created and executed [`scripts/audit_evaluation_results.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/audit_evaluation_results.py), exporting verification data to `evaluation_audit_outputs/`.
5. **Citation Repairs in `research_project/cas-refs.bib`:**
   - Deleted non-existent citation `wang2023gzstvZS`.
   - Corrected metadata and DOIs for Kumar et al. (`kumar2023indic`), Rahman (`rahman2026pashto`), Varadhan et al. (`varadhan2024mushra`), Chiang et al., Naseem et al., Jamal et al., and Pratap et al.
   - Added missing foundational references (Fastl & Zwicker 2007, SSW, VoiceMOS).
   - Removed `\nocite{*}`.
6. **Manuscript Prose & Table Repairs in `research_project/cas-sc-template.tex`:**
   - Retargeted provisional journal header to *Speech Communication*.
   - Corrected 960-pair vs 24-item subjective evaluation distinction in abstract and methodology.
   - Retitled Section 5.1 from MUSHRA to "Reference-Anchored Discrete Perceptual Rating".
   - Corrected Table 7 bolding error (Edge TTS `0.6329` bolded as highest).
   - Removed false citations of Kominek & Black on F0 RMSE and cents; replaced with Fastl & Zwicker (2007).
   - Reconciled sampling rate in text to match the empirical 16 kHz execution config.
   - Replaced all deleted/corrupted citation keys with verified keys (100% bijective match).
7. **Complete 17-Document Repair Dossier:** Created in `revision_docs/`.
8. **Chronological Experiment Log:** Created in `experiment_logs.md`.

---

## Next Five Executable Actions for the Authors

1. **Retrieve Audio Archive (`BLK-02`):** Download the audio corpus from the Google Drive link in `dataset_used.md` or launch notebook regeneration.
2. **Export Raw Survey Responses (`BLK-01`):** Log into the Google Forms account to export raw listener responses for the 20 historical participants.
3. **Resolve 4 Open Questions:** Provide answers to the questions documented in [`15_CHANGELOG_AND_OPEN_QUESTIONS.md`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/revision_docs/15_CHANGELOG_AND_OPEN_QUESTIONS.md).
4. **Execute ASR Intelligibility Benchmark (Phase 3):** Run [`scripts/urdu_text_normalizer.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/urdu_text_normalizer.py) and Whisper/MMS ASR scoring once audio is populated.
5. **Finalize Journal Agreement:** Confirm selection of *Speech Communication* as target venue and execute final author sign-off.

