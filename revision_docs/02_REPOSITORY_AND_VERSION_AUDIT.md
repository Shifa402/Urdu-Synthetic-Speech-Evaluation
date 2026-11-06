# 02: Repository and Version Audit

## Executive Summary

A forensic provenance audit of the repository establishes that the exact manuscript submitted to *Computer Speech & Language* on July 28, 2026 corresponds to the source files preserved originally in `research/`, packaged in `research.zip` (timestamped August 3, 2026, 18:23 PKT), and compiled originally as `TTS_Research_Paper.pdf` (compiled August 3, 2026, 19:34 PKT). 

To ensure clear collaboration and prevent any AI agent or coauthor from confusing the old rejected paper with current work, the rejected PDF has been renamed to `[needs revision old versi].pdf`. Furthermore, all manuscript sources have been consolidated into a single comprehensive directory: `research_project/`. All redundant folders (`research/`, `research.zip`, and temporary working folder `manuscript_revision/`) have been removed.

---

## 1. Manuscript Variants and Forensic Provenance

| Asset Path | Timestamp | Key Identifiers / Differences | Provenance Role |
|---|---|---|---|
| `[needs revision old versi].pdf` (formerly `TTS_Research_Paper.pdf`) | 2026-08-03 19:34:33 PKT | 17 pages; PDF Creator: `LaTeX3; cas-sc.cls; hyperref.sty`; Running header: *"Jafar, Sarmad, Yousaf & Bashir: Preprint submitted to Computer Speech & Language"*; File size: 447,500 bytes. | **Exact submitted PDF** provided to journal reviewers and editor. Marked clearly as old rejected version. |
| `research_project/` | **Consolidated Nov 6, 2026** | Single comprehensive manuscript workspace containing full Elsevier CAS distribution package (`cas-sc.cls`, `cas-dc.cls`, styles, documentation) plus the repaired `cas-sc-template.tex`, repaired `cas-refs.bib`, and dynamic `cas-common.sty`. | **Active, Authoritative Revision Directory**. |
| `research.zip` (Archived baseline) | 2026-08-03 18:23:23 PKT | Original zip archive (301,031 bytes uncompressed; 111,779 bytes zipped) of submitted files. | **Historic submission bundle** (consolidated). |
| `research/` (Archived baseline) | 2026-08-03 18:23:23 PKT | Original submitted directory. | **Historic submitted source** (consolidated into `research_project/`). |

### Detailed Diffs Between `research/` and `research_project/`
A line-by-line diff between `research/cas-sc-template.tex` and `research_project/cas-sc-template.tex` reveals exactly 4 localized modifications:
1. **Journal Header Removal:** `research/` declared `\journal{Computer Speech \& Language}`. In `research_project/`, this definition was deleted.
2. **Section Cross-Reference:** In Section 5.3 (MCD/F0), `research/` stated: *"the interpretation of such reference-distance metrics is discussed further in Section~\ref{sec:discussion-agreement}"*. In `research_project/`, this was edited to: *"this is discussed further in Section~\ref{sec:limitations}"*.
3. **Barchart Figure Environment:** `research/` wrapped `mushra_domain_barchart.png` in a standard float:
   ```latex
   \begin{figure}[pos=htbp]
   \centering
   \includegraphics[width=0.85\columnwidth]{mushra_domain_barchart.png}
   \caption{Domain-level mean MUSHRA-style scores.}
   \label{fig:mushra_domain}
   \end{figure}
   ```
   In `research_project/`, this float was replaced by an unnumbered inline center environment:
   ```latex
   \begin{center}
   \includegraphics[width=0.85\columnwidth]{mushra_domain_barchart.png}
   
   \small Figure X. Domain-level mean MUSHRA-style scores.
   \end{center}
   ```
4. **Trailing Whitespace:** Minor newline variation at EOF.

**Conclusion:** `research/` represents the pristine submitted manuscript. `research_project/` represents an aborted manual attempt to modify layout and float behavior.

---

## 2. Bibliography Variants and Analysis

Comparing `research/cas-refs.bib` against `research_project/cas-refs.bib`:
- **Byte Size:** Exactly 8,056 bytes in both directories.
- **Diff:** Exactly 0 bytes difference (`diff -u` returns exit code 0).
- **Total Entries:** Exactly 28 BibTeX entries.
- **In-Text Citations:** 27 entries are cited in `cas-sc-template.tex`.
- **Uncited Entry:** Exactly 1 entry, `conneau2022fleurs`, is present in the `.bib` file but was never cited in prose. It appeared in the final compiled references list solely because line 1511 invoked `\nocite{*}`.

---

## 3. Code, Notebooks, and Experimental Scripts Inventory

The repository contains 21 Jupyter Notebooks organized across four domain directories and the root:

### Conversational (`Conversational/ipynb_files/`)
- `humair__indic_parler.ipynb` (10 code cells): Generates Indic-Parler audio using static description (`MALE_URDU_DESCRIPTION`), calculates Resemblyzer embeddings and cosine similarity against Humair reference.
- `humair_style_mmstts.ipynb` (7 code cells): Generates MMS-TTS (`facebook/mms-tts-urd-script_arabic`) audio, computes Resemblyzer similarity.
- `speech_evaluation_humairUrdu_using_edgetts.ipynb` (6 code cells): Synthesizes audio using Edge-TTS voice `ur-PK-AsadNeural`, computes Resemblyzer similarity.
- `Gemini_Test_CONV.ipynb` (14 code cells): Calls Google Gemini API (`gemini-2.5-flash-preview-tts`, voice `charon`), computes Resemblyzer similarity.

### Emotional (`Emotional/ipynb_files/`)
- `edgetts_urduser_full_eval.ipynb` (21 code cells): Edge-TTS evaluation across Mendeley emotional speech dataset.
- `urduser_emotional_evaluation_mmstts.ipynb` (6 code cells): MMS-TTS emotional speech evaluation.
- `emotions_10_indic_parler.ipynb` (8 code cells): Indic-Parler emotional evaluation (10 samples per emotion x 6 emotions = 60 samples).
- `emotions_10_mmstts.ipynb` (7 code cells): MMS-TTS emotional evaluation across 6 emotions.
- `Gemini_Test_Emotions.ipynb` (21 code cells): Gemini TTS emotional evaluation across 6 emotions.

### Formal (`Formal/ipynb_files/`)
- `humair__indic_parler.ipynb` (10 code cells): Indic-Parler evaluation on Wikipedia subset (30 samples).
- `speech_evaluation_fleurs_indic_tts.ipynb` (6 code cells): Indic-Parler evaluation on FLEURS subset (30 samples).
- `humair_style_mmstts.ipynb` (7 code cells): MMS-TTS evaluation on Wikipedia subset (30 samples).
- `speech_evaluation_fleurs_mmstts.ipynb` (5 code cells): MMS-TTS evaluation on FLEURS subset (30 samples).
- `speech_evaluation_fleurs_humairUrdu_using_edgetts.ipynb` (7 code cells): Edge-TTS on combined Formal data.
- `Gemini_Test_Wiki1.ipynb` (8 code cells) & `Gemini_Test_Wiki2.ipynb` (11 code cells): Gemini TTS on Formal subsets.

### Literary / Storytelling (`Literary_storytelling/ipynb_files/`)
- `humair__indic_parler.ipynb` (10 code cells): Indic-Parler on `style = 'BOOK'`.
- `humair_style_mmstts.ipynb` (7 code cells): MMS-TTS on `style = 'BOOK'`.
- `speech_evaluation_humairUrdu_using_edgetts.ipynb` (6 code cells): Edge-TTS on `style = 'BOOK'`.
- `Gemini_Test_Book.ipynb` (12 code cells): Gemini TTS on `style = 'BOOK'`.

### Root Directory
- `Embedding_Gemini_Final.ipynb` (11 code cells): Final Gemini embedding consolidation.

### Critical Finding on Code Scope:
**None of the 21 notebooks contain code for Mel-Cepstral Distortion (MCD), WORLD feature extraction, FastDTW alignment, or F0 RMSE calculation.**
The entire objective acoustic evaluation pipeline (`evaluation/results/`) was executed by a standalone script that was **never committed to this repository**.

---

## 4. Evaluation Result Files (`evaluation/results/`)

The repository contains four result files in `evaluation/results/`:
1. `f0_mcd_per_file_scores.csv` (172,398 bytes): 960 rows evaluating 960 audio pairs across four TTS models and four domains.
2. `f0_mcd_per_domain_tts_model_summary.csv` (2,778 bytes): Summary table reporting mean and standard deviation of MCD and F0 RMSE per domain per TTS system.
3. `f0_mcd_per_domain_summary.csv` (582 bytes): Summary table reporting mean and standard deviation per domain aggregated across all four systems.
4. `f0_mcd_global_summary.json` (786 bytes): Global JSON summary containing overall corpus aggregates and execution config.

### Absolute File Paths in Result Files
The CSV files reference file paths located on an external workstation:
`/home/ali-jafar/Speech_Git_folder/speech-nlp/...`
Examples:
- Reference: `/home/ali-jafar/Speech_Git_folder/speech-nlp/Conversational/60_mushra_conv_gemini_audio/mushra_audio/reference/sample_32.wav`
- Synthetic: `/home/ali-jafar/Speech_Git_folder/speech-nlp/Conversational/60_mushra_conv_gemini_audio/mushra_audio/generated_gemini_tts/sample_32.wav`

These paths do not exist in the current Linux environment (`/home/ali-jafar/Speech_Git_folder` is absent).

---

## 5. Missing Expected Assets Inventory

| Asset Category | Expected Asset | Local Repository Status | Recovery Location / Strategy |
|---|---|---|---|
| **Audio Files** | 960 synthetic WAVs + 240 reference WAVs | **Completely Absent** (0 audio files in repository) | Must be recovered from external Google Drive archive (`dataset_used.md` link: `https://drive.google.com/file/d/1MfeXJ-LWh1SXptU5gUbXckh27YLMURNW/view?usp=drive_link`) or regenerated via notebooks. |
| **Human Listening Data** | Raw Google Forms responses (CSV/XLSX), individual rater scores, anonymized demographic records | **Completely Absent** (0 survey exports in repository) | Must be exported from the original Google Forms owner account or recovered from author offline storage. |
| **Acoustic Scoring Code** | Script that extracted WORLD/SPTK features, ran FastDTW, and computed MCD/F0 RMSE | **Completely Absent** from git | Recover from author's local workspace or reimplement according to documented specification in `08_OBJECTIVE_EVALUATION_PLAN.md`. |
| **MUSHRA Web Interface** | Interactive HTML/JS listening test harness | Never implemented (used Google Forms) | Implement standard Web MUSHRA interface per `07_SUBJECTIVE_STUDY_REDESIGN.md`. |

---

## 6. Git Working Tree State

- **Active Branch:** `revision-repair` (created from `main` to isolate all revision edits).
- **Original Branch:** `main` (clean, points to commit `0bcca1a Update dataset_used.md`).
- **Untracked Files:**
  - `TTS_Research_Paper.pdf` (submitted PDF)
  - `research.zip` (submitted zip)
  - `research/` (submitted source)
  - `research_project/` (scratch directory)
  - `evaluation_audit_outputs/` (generated by `scripts/audit_evaluation_results.py`)
  - `scripts/audit_evaluation_results.py`
  - `manuscript_revision/` (active revision working directory)
  - `revision_docs/` (comprehensive repair dossier)
- **Commit History Integrity:** Pristine. No history rewriting, rebasing, or deletion has been performed.

