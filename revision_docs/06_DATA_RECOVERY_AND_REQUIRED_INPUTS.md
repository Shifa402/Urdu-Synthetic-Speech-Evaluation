# 06: Data Recovery and Required Inputs

## Missing Assets Diagnosis & Criticality Classification

To prepare a scientifically rigorous, defensible manuscript for submission to *Speech Communication* or *IEEE Transactions on Audio, Speech and Language Processing*, all empirical claims must be traceable to primary data assets.

This document provides a forensic inventory of missing assets, categorizing them strictly into **Publication Blockers** (assets without which a revised empirical paper cannot be ethically submitted) versus **Useful Additions** (secondary documentation and artifacts that enhance reproducibility).

---

## 1. Publication Blockers (Mandatory for Resubmission)

| Blocker ID | Missing Asset Description | Why It Is a Hard Blocker | Likely Location Based on Evidence | Recovery Action Required from Authors |
|---|---|---|---|---|
| **BLK-01** | **Raw Human Listening Test Response Data** (Google Forms CSV/Sheets export) | Tables 4 and 5 report listener means, SDs, and ABX percentages ($n=20$ listeners, 108 trials). Zero raw response sheets exist in git. Reviewers flagged low ratings and impossible ABX descriptions. Without raw data, subjective claims cannot be defended or statistically re-analyzed. | Author Google Account associated with the Google Forms questionnaire; personal Google Drive; local downloads folder of study administrator. | Export raw response spreadsheet with timestamp, listener ID (anonymized), domain assignment, stimulus ID, and ratings (Naturalness, Clarity, Quality). |
| **BLK-02** | **Original Synthesized & Reference Audio Corpus** (960 pairs: 240 reference WAVs + 960 generated WAVs) | All acoustic claims, re-computations, and proposed modern metrics (VoiceMOS, Whisper WER/CER, proper MCD bandwidth check) require actual audio waveforms. Zero audio files exist locally. | External Google Drive archive referenced in `dataset_used.md`: [Google Drive Link](https://drive.google.com/file/d/1MfeXJ-LWh1SXptU5gUbXckh27YLMURNW/view?usp=drive_link) or workstation path `/home/ali-jafar/Speech_Git_folder/speech-nlp/`. | Grant access to / download the Google Drive archive into `audio_corpus/` or execute synthesis regeneration pipeline via existing notebooks. |
| **BLK-03** | **Original Acoustic Scoring Script** (Generator of `evaluation/results/`) | `f0_mcd_per_file_scores.csv` contains identical duplicate values on FLEURS between Indic-Parler and MMS-TTS (`AUD-001`). The script that generated this CSV was never committed to git (commit `d449ba81` only committed finalized CSVs). | Original workstation checkout under `/home/ali-jafar/Speech_Git_folder/speech-nlp/` or local Cursor history. | Locate and commit the Python script (`compute_mcd_f0.py` or equivalent) that called `pymcd` and `pyworld`. |

---

## 2. Useful Additions (Enhance Reproducibility & Rigor)

| Item ID | Asset Description | Benefit to Revision | Likely Location / Source |
|---|---|---|---|
| **ADD-01** | **Google Forms Questionnaire Templates / URL** | Verifies exact Urdu and English instructional text shown to listeners, resolving Reviewer #2's question regarding how "naturalness" was translated into Urdu (`R2-006`). | Google Forms administrative account. |
| **ADD-02** | **Full Participant Demographic & Screening Log** | Verifies hearing status self-report, age distribution (18–25), gender split, and native language background, eliminating speculation regarding Lahore demographics (`AUD-011`). | Study administrator offline survey records. |
| **ADD-03** | **Corpus Licensing & Usage Terms** | Verifies redistribution compliance for Mendeley Emotional Speech (CC BY 4.0), FLEURS (CC BY 4.0), and Humair Awan UrduSpeech dataset. | Hugging Face / Mendeley Data terms of use. |
| **ADD-04** | **API Execution Metadata & Version Tags** | Pinned dates and version tags for Microsoft Edge TTS and Google Gemini TTS (`charon` model checkpoint) to document reproducibility constraints for proprietary cloud APIs. | API billing logs, notebook outputs, or Python execution receipts. |
| **ADD-05** | **Exact Python Environment Manifest (`requirements.txt` / lockfile)** | Freezes exact versions of `transformers`, `parler-tts`, `torch`, `resemblyzer`, `pymcd`, `pyworld`, and `scipy` used in generation. | `pip list` export from original execution environment. |

---

## 3. Concrete Action Protocol for Author Inputs

To resolve the publication blockers cleanly without fabricating missing records, the authors should execute the following steps:

### Step 1: Human Evaluation Data Recovery (BLK-01)
1. Log into the Google account used to create and administer the listening evaluation forms.
2. Locate the four domain survey forms:
   - *Conversational Domain Evaluation*
   - *Literary / Storytelling Evaluation*
   - *Formal Speech Evaluation*
   - *Emotional Speech Evaluation*
   - *ABX Discrimination Test*
3. Export responses as `.csv` files into a secure local directory: `data_recovery/raw_listening_responses/`.
4. Run our planned validation script (`scripts/validate_listening_data.py`) to verify rater counts ($N=20$), domain allocations ($n=10$ per pair), and trial totals ($n=24$ items).

### Step 2: Audio Corpus Access (BLK-02)
1. Verify access permissions on the Google Drive link:  
   `https://drive.google.com/file/d/1MfeXJ-LWh1SXptU5gUbXckh27YLMURNW/view?usp=drive_link`
2. Download and unpack the archive into `audio_corpus/` with the following expected directory layout:
   ```text
   audio_corpus/
   ├── Conversational/
   │   ├── reference/ (60 WAVs)
   │   ├── generated_edgetts/ (60 WAVs)
   │   ├── generated_gemini/ (60 WAVs)
   │   ├── generated_indic_parler/ (60 WAVs)
   │   └── generated_mmstts/ (60 WAVs)
   ├── Emotional/ (same structure)
   ├── Formal/ (same structure, 30 FLEURS + 30 UrduSpeech)
   └── Literary_storytelling/ (same structure)
   ```
3. If original audio cannot be recovered from Google Drive, the authors can **regenerate the synthetic audio** using the existing 21 Jupyter notebooks in the repository, pinning seeds and logging exact generation parameters.

### Step 3: Acoustic Pipeline Script Reconciliation (BLK-03)
1. Check the original machine where commit `d449ba81` ("Add organized F0/MCD evaluation result artifacts") was authored.
2. If the original script is unrecoverable, adopt the clean, modular Python reimplementation specified in `08_OBJECTIVE_EVALUATION_PLAN.md` (`scripts/evaluate_audio_corpus.py`).

