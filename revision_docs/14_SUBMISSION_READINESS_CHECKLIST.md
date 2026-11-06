# 14: Submission Readiness Checklist

## Hard Gate Verification Protocol

> [!CAUTION] Mandatory Submission Gate Rule
> Under no circumstances should this manuscript be submitted or transferred to *Speech Communication*, *IEEE TASLP*, or any journal until **every single hard gate below is certified as PASS**.
> 
> **No gate passes merely because prose sounds improved or plans look thorough.** A gate passes only when concrete empirical artifacts, verified data files, or validated mathematical proofs exist in the repository.

---

## Master Gate Evaluation Summary

| Gate ID | Hard Evaluation Category | Gate Status | Critical Blocker / Requirement |
|---|---|---|---|
| **GATE-01** | **Bibliographic Integrity & Citation Claims** | **PASS** | 100% of references verified; non-existent papers excised; metadata corrected. |
| **GATE-02** | **Numerical & Aggregate Traceability** | **PASS (Audit Documented)** | Table aggregates traced; bolding fixed; 5-row averaging and raw F0 documented. |
| **GATE-03** | **Methodological & Construct Validity** | **PASS (In Working Copy)** | Re-scoped to text-genre robustness; MCD/F0 reframed as acoustic divergence. |
| **GATE-04** | **Raw Data & Code Asset Traceability** | **BLOCKED (Action Required)** | **Hard Blocker:** Audio waveforms ($N=960$) and raw survey response exports absent locally. |
| **GATE-05** | **Subjective Listening Test Protocol** | **BLOCKED (Action Required)** | **Hard Blocker:** Historical survey lacks raw data; requires recovery or new web campaign. |
| **GATE-06** | **Figures, Formatting & Cross-References** | **PASS** | Bolding error corrected; float numbering and labels verified; LaTeX syntax clean. |
| **GATE-07** | **Ethical Governance & Declarations** | **PASS (Policy Bound)** | Truthful generative AI declaration; no retroactive ethics claims; IRB protocol specified. |
| **GATE-08** | **Author Approval & Consortium Sign-Off** | **PENDING (Author Action)** | Formal co-author review, contribution sign-off, and venue confirmation required. |
| **GATE-09** | **Journal Fit, Formatting & Financial Plan** | **PASS** | *Speech Communication* targeted (hybrid model, USD 0 author publishing charge). |

---

## Detailed Gate Specifications & Verification Criteria

### GATE-01: Bibliographic Integrity & Citation Claims
- [x] **Criterion 1.1:** Zero non-existent, fabricated, or unverified citations in `.bib` file (`wang2023gzstvZS` completely deleted).
- [x] **Criterion 1.2:** All 28 existing references hand-verified against authoritative CrossRef / DOI / DBLP / arXiv primary records (`03_REFERENCE_AND_CLAIM_AUDIT.md`).
- [x] **Criterion 1.3:** Author names and years corrected for all corrupted entries (`kumar2023indic`, `rahman2026pashto`, `varadhan2024mushra`, `chiang2024mushraevaluate`, `naseem2024developing`, `jamal2022transfer`).
- [x] **Criterion 1.4:** Uncited entry `conneau2022fleurs` cited in Section 4.1; `\nocite{*}` eliminated from LaTeX.
- [x] **Criterion 1.5:** Kominek & Black (2008) removed from F0 RMSE, cents, and JND claims.
- **GATE STATUS:** **PASS**

---

### GATE-02: Numerical & Aggregate Traceability
- [x] **Criterion 2.1:** Standalone audit script ([`scripts/audit_evaluation_results.py`](file:///home/ali-jafar/Urdu-Synthetic-Speech-Evaluation/scripts/audit_evaluation_results.py)) executed with machine-readable verification outputs (`evaluation_audit_outputs/`).
- [x] **Criterion 2.2:** Table 7 speaker similarity bolding error corrected in LaTeX (`0.6329` on Edge TTS bolded; Indic-Parler unbolded).
- [x] **Criterion 2.3:** Table 10 & 12 "Overall Means" mathematically proven and documented as unweighted 5-row averages.
- [x] **Criterion 2.4:** F0 column discrepancy resolved: Tables 11 & 12 proven to report `f0_rmse_cents_raw`.
- [x] **Criterion 2.5:** True valid F0 denominator ($n=958$) documented; zero-voiced DTW frame failures (rows 86 and 169) disclosed.
- [x] **Criterion 2.6:** Identical duplicate FLEURS data between Indic-Parler and MMS-TTS documented and flagged.
- **GATE STATUS:** **PASS (Fully Documented & Reconciled)**

---

### GATE-03: Methodological & Construct Validity
- [x] **Criterion 3.1:** Distinct synthesis paradigms (default text-domain robustness vs style prompting vs voice cloning) formally separated.
- [x] **Criterion 3.2:** Resemblyzer GE2E English pre-training and language mismatch documented.
- [x] **Criterion 3.3:** MCD and F0 RMSE demoted from "synthesis quality" to "signal-level acoustic divergence from unaligned reference."
- [x] **Criterion 3.4:** Corpus confounding across domains (speakers, channels, text lengths) explicitly acknowledged as an internal validity threat.
- [x] **Criterion 3.5:** Elimination of claims of a single "clear winner" or speculative reverse-engineering of model loss functions.
- **GATE STATUS:** **PASS (Working Copy Realignment)**

---

### GATE-04: Raw Data & Code Asset Traceability
- [ ] **Criterion 4.1:** The 960 synthetic WAV files and 240 reference WAV files downloaded and placed in `audio_corpus/` (`BLK-02`).
- [ ] **Criterion 4.2:** Raw Google Forms response exports (CSV/XLSX) placed in `data_recovery/raw_listening_responses/` (`BLK-01`).
- [ ] **Criterion 4.3:** Original acoustic scoring script recovered or modular pipeline implemented (`BLK-03`).
- **GATE STATUS:** **BLOCKED — Awaiting Author Inputs per Document 06**

---

### GATE-05: Subjective Listening Test Protocol
- [ ] **Criterion 5.1:** EITHER raw historical listener data is recovered and proven statistically robust via Linear Mixed-Effects Models ($N=20$), OR a prospective webMUSHRA campaign is completed ($N=30$, continuous 0–100 sliders, rated hidden reference, rated anchor).
- [ ] **Criterion 5.2:** Standardized Urdu instructions (*Qudrati Andaaz*, *Wazahat aur Fehm*, *Mauzooniyat*) verified by native linguists.
- [ ] **Criterion 5.3:** Pre-test headphone screening test (e.g. Huggins pitch / antiphasic tones) administered and logged.
- **GATE STATUS:** **BLOCKED — Awaiting Author Decision on Recovery vs. Web MUSHRA Campaign**

---

### GATE-06: Figures, Formatting & Cross-References
- [x] **Criterion 6.1:** Barchart float environment clean and labeled.
- [x] **Criterion 6.2:** All table captions, column headers, units (dB, cents, Likert 1–5), and sample sizes ($n$) explicitly documented.
- [x] **Criterion 6.3:** Figure and table references resolve without broken cross-references.
- [x] **Criterion 6.4:** Software sampling rates unified to 16 kHz in text to eliminate upsampling confusion.
- **GATE STATUS:** **PASS**

---

### GATE-07: Ethical Governance & Declarations
- [x] **Criterion 7.1:** Truthful, transparent Generative AI declaration preserved in Section 12, explicitly disclosing language editing tools without obscuring human scientific accountability.
- [x] **Criterion 7.2:** Zero retroactive claims of ethics committee approval; prospective IRB review protocol defined for new listening campaign.
- [x] **Criterion 7.3:** Sociolinguistic demographic assumptions (native Urdu proficiency inferred from Lahore residence) removed.
- **GATE STATUS:** **PASS**

---

### GATE-08: Author Approval & Sign-Off
- [ ] **Criterion 8.1:** Formal agreement by all four co-authors (Ali Jafar, Amal Sarmad, Shifa Yousaf, Maryam Bashir) on author contributions, revision plan, and target journal.
- [ ] **Criterion 8.2:** Author institutional affiliations verified as FAST-NUCES Lahore.
- **GATE STATUS:** **PENDING — Requires Co-Author Meeting**

---

### GATE-09: Journal Fit, Formatting & Financial Plan
- [x] **Criterion 9.1:** *Speech Communication* (Elsevier / ISCA) selected as primary target venue; hybrid subscription route confirmed (USD 0 publishing charge).
- [x] **Criterion 9.2:** Elsevier CAS format maintained (`cas-dc` / `cas-sc` class compatible).
- [x] **Criterion 9.3:** Transfer promotional deadlines ignored in favor of complete scientific verification.
- **GATE STATUS:** **PASS**

