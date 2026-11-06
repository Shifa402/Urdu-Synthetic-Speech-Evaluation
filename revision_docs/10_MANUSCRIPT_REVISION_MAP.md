# 10: Manuscript Revision Map

## Structural Realignment Overview

This revision map translates the 25 editorial, reviewer, and repository audit issues into a concrete, section-by-section execution blueprint for revising `cas-sc-template.tex` and `cas-refs.bib`.

Every modification is categorized as **KEEP**, **REWRITE**, **REMOVE**, or **ADD**, with explicit bidirectional linkages to the Master Issue Register (`01_MASTER_ISSUE_REGISTER.md`).

---

## 1. Title, Abstract, and Metadata Realignment

| Manuscript Element | Current Text / Status | Planned Modification | Action Category | Mapped Issue IDs |
|---|---|---|---|---|
| **Title** | *Domain-Specific Evaluation of Text-to-Speech Systems: A Multi-Metric Benchmarking Study* | Retain core title or adjust to: *Benchmarking Neural Text-to-Speech Systems for Urdu Across Textual Genres: Acoustic, Perceptual, and Methodological Dimensions* | **REWRITE** | `R2-005`, `ED-001` |
| **Running Header** | *Preprint submitted to Computer Speech & Language* | Adjust to neutral submission header: *Preprint under revision* | **REWRITE** | Provenance |
| **Abstract: Listening Scale** | *"All 960 reference--synthetic pairs were evaluated..."* | Explicitly state: Automated acoustic and embedding metrics evaluated 960 pairs; subjective perceptual listening tests evaluated 24 source utterances across 4 systems ($N=96$ system stimuli). | **REWRITE** | `R1-014`, `ED-001` |
| **Abstract: Emotional Domain** | *"emotional speech consistently presents the greatest synthesis challenge (mean MCD 12.03 dB...)"* | Qualify finding: Emotional text prompts yielded the greatest acoustic divergence from actor recordings; note corpus and style-prompt confounding. | **REWRITE** | `R1-002`, `AUD-010` |
| **Abstract: Identity Preservation** | *"jointly assess perceptual quality, speaker similarity, and acoustic fidelity"* | Replace "speaker similarity" with "acoustic feature distance"; remove zero-shot identity preservation claims. | **REWRITE** | `R1-004`, `R1-005` |
| **Abstract: Open Release** | *"All evaluation scripts, result tables, and curated Colab notebooks are publicly released at..."* | Clarify exact availability: Colab notebooks and summary tables released; raw audio and survey responses documented with access guidelines. | **REWRITE** | `AUD-013` |

---

## 2. Section-by-Section Keep / Rewrite / Remove / Add Map

### Section 1: Introduction (`sec:intro`)
- **KEEP:** Motivation regarding low-resource language speech synthesis; inclusion of Urdu as a high-impact underrepresented language; general multi-system comparison concept.
- **REWRITE:**
  - Lines 120–124: Rewrite claim that past 5 years of TTS evaluation relied exclusively on MOS (`R1-007`). Acknowledge multi-metric benchmarking in Blizzard and VoiceMOS challenges.
  - Lines 146–148: Acknowledge that the historical listening test used a discrete 1–5 reference-anchored rating format rather than standard continuous MUSHRA (`R1-011`).
- **REMOVE:**
  - Line 149: Remove citation of `wang2023gzstvZS` (`R2-002`).
  - Lines 149–151: Remove assertion that Resemblyzer measures "identity preservation" for systems generating preset voices (`R1-004`).
  - Line 151: Remove claim that 5 cents is a universal JND for speech pitch perception citing Kominek & Black (`R2-007`).
- **ADD:** Clear formulation of RQ1 (text genre robustness) and RQ2 (metric and construct divergence) (`ED-001`).

---

### Section 2: Related Work (`sec:related`)
- **KEEP:** Discussions of VITS (`kim2021vits`), HiFi-GAN (`kong2020hifigan`), and Parler-TTS architecture (`lacombe2024parlertts`).
- **REWRITE:**
  - Section 2.1 (TTS Evaluation): Expand beyond Le Maguer et al. (2024) (`R1-001`). Synthesize Kirkland et al. (2023 "Stuck in the MOS pit"), VoiceMOS Challenge (`cooper2024voicemos`), and Varadhan et al. (2024 `varadhan2024mushra`).
  - Section 2.2 & 2.3 (Urdu & South Asian TTS): Correct citations:
    - Replace `jain2023indicTTS` with `kumar2023indic` (`R2-001`).
    - Replace `naseem2025urdu` with `naseem2024developing` (`AUD-016`).
    - Replace `arshad2022transfer` with `jamal2022transfer` (`AUD-016`).
    - Replace `pashto2025bench` with `rahman2026pashto` (`R2-003`).
- **REMOVE:**
  - Delete `wang2023gzstvZS` completely (`R2-002`).
- **ADD:** Integrate Shirali-Shahreza & Penn (2023) and Pandey et al. (2025) on deconstructing the construct of "naturalness" in multilingual speech synthesis (`R2-006`).

---

### Section 3: Methodology for TTS System Selection (`sec:systems`)
- **KEEP:** Selection of the four distinct paradigms (Indic-Parler, MMS, Edge, Gemini).
- **REWRITE:**
  - Table 1 and Section 3.2: Add exact model checkpoint links, Hugging Face repository IDs, and release tags (`R1-008`).
  - Section 3.1: Explicitly state that Indic-Parler used a fixed neutral description ("Rohit"), Edge used default `ur-PK-AsadNeural`, and Gemini used fixed `charon`, holding voice profiles constant across all domains (`R1-002`, `R1-010`).
- **REMOVE:**
  - Lines 756 & 791: Remove false claims of deterministic synthesis; disclose that Indic-Parler used stochastic autoregressive sampling (`do_sample=True, temperature=0.8`) and cloud APIs are subject to provider updates (`AUD-009`).

---

### Section 4: Domain-Wise Dataset Setup (`sec:domain-setup`)
- **KEEP:** Corpus breakdown (FLEURS, UrduSpeech, Mendeley Emotional Speech).
- **REWRITE:**
  - Section 4.1: Clarify that domain variation was introduced via text prompts drawn from these corpora (`R1-002`, `R1-003`).
  - Section 4.2–4.5: Explicitly document corpus confounding (different speakers, recording environments, and sentence lengths) as an internal validity limitation (`AUD-010`).
- **ADD:**
  - Add explicit in-text citation `\citep{conneau2022fleurs}` for FLEURS (`AUD-014`).
  - Document the male-only speaker selection rationale and external validity boundary (`R1-012`).

---

### Section 5: Evaluation Methodology (`sec:methodology`)
- **KEEP:** General mathematical definitions of MCD and FastDTW.
- **REWRITE:**
  - Lines 493–498: Correct pipeline summary to state 960 pairs evaluated objectively; 24 source utterances evaluated subjectively (`R1-014`).
  - Section 5.1: Retitle from "MUSHRA-Style Listening Test" to "Reference-Anchored Discrete Perceptual Rating" (`R1-011`). Explicitly document deviations from ITU-R BS.1534 (discrete 1–5 scale, unrated orientation reference/anchor, Google Forms administration).
  - Lines 539–548: Document participant recruitment truthfully; delete false claim that residence in Lahore obviates native language screening (`AUD-011`).
  - Section 5.1.2: Reframe ABX discrimination test: acknowledge reporting ambiguities in historical draft (`AUD-007`, `AUD-008`).
  - Section 5.2: Reframe Resemblyzer: clarify that GE2E was trained on English VoxCeleb (`R1-004`) and measures general acoustic embedding distance, not speaker identity preservation.
  - Section 5.3: Reframe MCD and F0 RMSE: clarify they measure spectral and prosodic divergence against an unaligned external speaker, not synthesis quality (`R1-005`).
- **REMOVE:**
  - Remove all citations of Kominek & Black (2008) for F0 RMSE, cents, and 5-cent JND (`R2-007`).
  - Remove claim of 22.05 kHz resampling; align text with actual 16 kHz execution config (`R1-009`, `AUD-006`).

---

### Section 6: Experimental Setup (`sec:expsetup`)
- **KEEP:** Hardware descriptions (NVIDIA RTX GPUs).
- **REWRITE:**
  - Reconcile Table 3 software versions and sampling rates (16 kHz standardized).

---

### Section 7: Results (`sec:results`)
- **KEEP:** Empirical score tables (with verified corrections).
- **REWRITE:**
  - Section 7.1 (Subjective Ratings): Contextualize low commercial scores as reflection of domain difficulty and reference-anchored rating friction (`R1-015`).
  - Table 5 (ABX Results): Reconcile listener counts (9 vs 10) and system names (`AUD-008`).
  - Table 7 (Speaker Similarity): **Fix bolding error:** unbold Indic-Parler (0.6312) and bold Edge TTS (0.6329) (`AUD-002`).
  - Tables 10 & 12 (MCD and F0 RMSE): Add explanatory notes documenting that Overall Means reflect unweighted averages of the 5 table rows (`AUD-003`); report `f0_rmse_cents_raw` explicitly (`AUD-005`); disclose FLEURS Indic/MMS duplicate scores (`AUD-001`).
  - Section 7.4 (F0 RMSE): Report true denominator ($n=958$ valid pairs; 2 pairs failed voiced frame DTW alignment) (`AUD-004`).

---

### Section 8: Discussion (`sec:discussion`)
- **REWRITE:**
  - Section 8.1 & 8.3: Eliminate speculative claims that metric divergence reflects "internal model optimization objectives" (`R2-008`). Reframe as construct non-congruence.
  - Section 8.2: Demote causal domain claims; discuss text-genre difficulty in the context of corpus confounding (`AUD-010`).
- **ADD:** Comprehensive, transparent **Limitations Subsection** detailing:
  1. Male-only voice restriction (`R1-012`).
  2. Corpus and channel confounding across domains (`AUD-010`).
  3. Pre-trained English acoustic bias in Resemblyzer (`R1-004`).
  4. Non-standard discrete scale in historical listening test (`R1-011`).
  5. Stochastic generation parameters and API version volatility (`AUD-009`).

---

### Section 9 & Back Matter
- **Section 9 (Conclusion):** Rebound conclusions strictly within verified evidence (`ED-001`).
- **Generative AI Declaration:** Preserve honest, transparent disclosure of AI assistance (`AUD-012`).
- **Bibliography:** Remove `\nocite{*}` (`AUD-014`); compile cleaned, verified 31-entry `.bib` file.

