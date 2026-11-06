# 13: Reviewer Response Working Draft

## Purpose and Status Notice

> [!IMPORTANT] Internal Repair Record Notice
> This document is an **internal working repair record** developed following the rejection of manuscript `YCSLA-D-26-00760` (*Domain-Specific Evaluation of Text-to-Speech Systems: A Multi-Metric Benchmarking Study*) from *Computer Speech & Language*. 
> 
> Resubmission to *Computer Speech & Language* is **not invited**. This document serves as the master audit trail ensuring that every criticism raised by the Handling Editor and both reviewers is rigorously addressed and mapped to concrete evidence before the revised manuscript is submitted to a new venue (*Speech Communication* or *IEEE TASLP*).
> 
> In accordance with scientific integrity guidelines:
> - Actions executed during the current session are labeled **[COMPLETED]**.
> - Actions requiring external audio recovery, prospective data collection, or experimental execution are labeled **[PLANNED]**.

---

## 1. Response to the Handling Editor

### Comment ED-01: Methodological Flaws & Non-Sequitur Conclusions
> *"Both reviewers agree that even though the overall research question is of interest, the manuscript has significant methodological flaws, does not take into account the current state of the art, and draws conclusions that do not follow from the reported study."*

- **Author Acknowledgement:** We fully accept the Editor's assessment. Our submitted draft conflated distinct evaluation paradigms, reported reference-relative acoustic distances as "synthesis quality," applied non-standard discrete scales while claiming MUSHRA compliance, and asserted causal claims regarding domain difficulty that were entangled with corpus properties.
- **Planned / Completed Action:**
  1. *[COMPLETED]* Re-scoped the manuscript around text-domain robustness and construct divergence (`04_METHODS_AND_VALIDITY_REPAIR.md`).
  2. *[COMPLETED]* Removed sweeping claims of a single "clear winner" and qualified all domain difficulty assertions (`manuscript_revision/cas-sc-template.tex`).
  3. *[PLANNED]* Incorporate modernized ASR intelligibility (WER/CER) and automated MOS estimation into the experimental framework (`08_OBJECTIVE_EVALUATION_PLAN.md`).
- **Required Evidence:** Dual-ASR WER benchmarks on synthetic and human speech; Linear Mixed-Effects Model results.
- **Manuscript Location:** Abstract, Section 1 (Introduction), Section 5 (Methodology), Section 8 (Discussion).
- **Status:** **[IN PROGRESS - Phase 1 Completed / Phases 3–5 Planned]**

---

### Comment ED-02: Non-Existing / Hallucinated References
> *"More gravely, one reviewer remarks that the manuscript contains non-existing, most likely hallucinated references. This point alone throws a serious doubt on the scientific rigour and overall integrity of the conducted research and writing process."*

- **Author Acknowledgement:** We acknowledge this finding with the utmost seriousness. The presence of non-existent and corrupted references severely compromised the integrity of the manuscript. This occurred during preliminary drafting where AI assistance was utilized for literature formatting without rigorous cross-referencing against primary databases.
- **Completed Action:**
  1. *[COMPLETED]* Conducted an exhaustive forensic audit of all 28 entries in `cas-refs.bib` (`03_REFERENCE_AND_CLAIM_AUDIT.md`).
  2. *[COMPLETED]* Completely excised the non-existent reference `wang2023gzstvZS` from the bibliography and in-text citations.
  3. *[COMPLETED]* Corrected corrupted author metadata, publication dates, and DOIs for 5 existing papers (`jain2023indicTTS` $\rightarrow$ Kumar et al. ICASSP 2023; `pashto2025bench` $\rightarrow$ Rahman 2026; `chiang2024mushra` $\rightarrow$ Varadhan et al. 2024; `chiang2024mushraevaluate` $\rightarrow$ Chiang, Huang & Lee 2024; `naseem2025urdu` $\rightarrow$ Naseem et al. Interspeech 2024; `arshad2022transfer` $\rightarrow$ Jamal et al. 2022).
  4. *[COMPLETED]* Removed `\nocite{*}` to ensure only verified, cited literature appears in the bibliography.
  5. *[COMPLETED]* Preserved an honest, detailed declaration of generative AI tool use (`AUD-012`).
- **Required Evidence:** Authoritative DOI / CrossRef / DBLP verification links for 100% of bibliography entries.
- **Manuscript Location:** `cas-refs.bib`, Section 2 (Related Work), Section 12 (Generative AI Declaration).
- **Status:** **[COMPLETED]**

---

## 2. Response to Reviewer #1

### Comment R1-01: Related Work Scope Beyond Le Maguer (2024)
> *"The related work section clearly needs improvement, as LeMaguer's paper is not the only one looking into the flaws of TTS evaluation"*

- **Author Acknowledgement:** Concur. Relying solely on Le Maguer et al. (2024) presented an artificially narrow perspective on subjective evaluation critiques.
- **Completed Action:** *[COMPLETED]* Expanded Section 2 to include foundational literature on evaluation methodology and MOS limitations, including Kirkland et al. (2023, "Stuck in the MOS pit"), the VoiceMOS Challenge benchmark series (`cooper2024voicemos`), and Varadhan et al. (2024).
- **Manuscript Location:** Section 2.1 (TTS Evaluation Methodology).
- **Status:** **[COMPLETED]**

---

### Comment R1-02 & R1-10: Domain Control & Parler-TTS Prompting
> *"The domain selection is appropriate, however, it is not clear how you control for the domains. Is it just the input text? Why not use the description for ParlerTTS to control the output? ... Please add more details on how you control for the 4 domains."*

- **Author Acknowledgement:** Concur. The submitted draft did not clearly state how domain variation was operationalized across the systems.
- **Completed Action:**
  1. *[COMPLETED]* Audited our generation code and confirmed that domain variation was introduced **solely via input text prompts** extracted from domain-specific corpora (`04_METHODS_AND_VALIDITY_REPAIR.md`).
  2. *[COMPLETED]* Disclosed in Section 3 and Section 4 that system voice profiles were deliberately held constant as neutral baselines (Indic-Parler used fixed "Rohit" description; Edge used `ur-PK-AsadNeural`; Gemini used `charon`) to isolate text-genre robustness.
  3. *[PLANNED]* Designed a planned experimental extension testing dynamic style-prompting in Parler-TTS (e.g. whispering, theatrical recitation, excited conversational tone) (`12_PHASED_EXECUTION_PLAN.md`).
- **Manuscript Location:** Section 3.1, Section 4.1.
- **Status:** **[COMPLETED in text / Extension PLANNED]**

---

### Comment R1-03: Speech Corpora Usage & Prompt Pairing
> *"It is not clear how you truly use the selected speech corpora? Do you use each utterance to control the output of the TTS? Do you use the same input text as in the original utterance?"*

- **Author Acknowledgement:** Concur. The stimulus creation pipeline required explicit clarification.
- **Completed Action:** *[COMPLETED]* Added an unambiguous description of the prompt extraction pipeline: For every utterance in the reference corpora, the transcribed text was extracted and fed verbatim as an input prompt to all four TTS engines. The resulting synthesized audio was paired with the original human recording for utterance-level acoustic comparison.
- **Manuscript Location:** Section 4.1, Section 5.0.
- **Status:** **[COMPLETED]**

---

### Comment R1-04: Resemblyzer Language Mismatch on Urdu Speakers
> *"Was the Resemblyzer model trained on Urdu speakers? If not, there might be a mismatch between the training and test data, hence unreliable similarity measures."*

- **Author Acknowledgement:** Concur. Reviewer #1 rightly identifies a critical threat to construct validity.
- **Completed Action:** *[COMPLETED]* Disclosed that Resemblyzer's GE2E encoder was trained on English speech (VoxCeleb and LibriSpeech). Acknowledged that out-of-domain linguistic and acoustic mismatch introduces variance. Re-framed Resemblyzer scores not as true speaker identity verification, but as descriptive deep acoustic feature similarity (`04_METHODS_AND_VALIDITY_REPAIR.md`).
- **Manuscript Location:** Section 5.2, Section 8.4 (Limitations).
- **Status:** **[COMPLETED]**

---

### Comment R1-05: Validity of MCD & F0 RMSE Across Mismatched Speakers
> *"MCD and F0 RMSE are not realiable measures of quality. They were used in previous TTS technologies, when the alignment between input and output was easier to perform. Nowadays, especially for ALMs, I do not believe that DTW alone can perform such measure. Also, if there are different speakers, as in the MMS systems, this would clearly generate a random value, and not a true measure of quality."*

- **Author Acknowledgement:** Concur. Measuring spectral and pitch distance against human speakers who have different vocal tract anatomy, pitch registers, and phrasing styles does not measure TTS "quality."
- **Completed Action:**
  1. *[COMPLETED]* Excised all claims that MCD and F0 RMSE reflect synthesis "quality" or "accuracy." Retitled them strictly as "Reference-Relative Acoustic and Prosodic Divergence."
  2. *[COMPLETED]* Formally documented that register offsets and DTW path distortions across differing speaker identities confound the metric (`04_METHODS_AND_VALIDITY_REPAIR.md`).
  3. *[PLANNED]* Deployed automated ASR (WER/CER) and VoiceMOS SSL estimators as the primary objective evaluators of intelligibility and perceptual quality (`08_OBJECTIVE_EVALUATION_PLAN.md`).
- **Manuscript Location:** Section 5.3, Section 7.3, Section 8.1.
- **Status:** **[COMPLETED in text / Metrics Expansion PLANNED]**

---

### Comment R1-06 & R2-04: Lack of Automatic MOS Ratings and WER
> *"What about using automatic MOS ratings? And what about WER? Both measures are common in today's literature."* / *"The authors are encouraged to follow the work of Cooper et al., particularly originating in the VoiceMOS challenge."*

- **Author Acknowledgement:** Concur. The absence of speech recognition metrics and automated neural MOS predictors left our objective evaluation obsolete.
- **Planned Action:** *[PLANNED]* Specified and implemented an objective evaluation roadmap (`08_OBJECTIVE_EVALUATION_PLAN.md`) incorporating:
  1. Dual-ASR evaluation (Whisper-large-v3 and MMS-ASR-Urdu) with a standardized Urdu text normalizer, benchmarked against human reference speech baselines.
  2. Automated MOS estimation via UTMOS and NISQA v2.0, evaluated for cross-lingual rank correlation against native Urdu human ratings.
- **Required Evidence:** WER/CER calculation tables across all 960 pairs; correlation statistics ($r$, $\rho$) with human ratings.
- **Manuscript Location:** New Section 5.4 (Objective Intelligibility) and Section 7.5.
- **Status:** **[PLANNED - Phase 3]**

---

### Comment R1-07: Inaccurate Claim Regarding 5 Years of MOS-Only TTS Evaluation
> *"You mention that previous evaluations of TTS systems was performed using only MOS ratings. That is not true for the past 5 years of scientific publications at least."*

- **Author Acknowledgement:** Concur. Our literature survey overgeneralized. Multi-metric evaluation (ASR-WER, UTMOS, MUSHRA, BWS) has been standard in premier speech venues for years.
- **Completed Action:** *[COMPLETED]* Rewrote Introduction (lines 120–124) to accurately characterize contemporary TTS evaluation literature.
- **Manuscript Location:** Section 1 (Introduction), Section 2.1.
- **Status:** **[COMPLETED]**

---

### Comment R1-08: Missing Links and System Checkpoints
> *"You need to add the exact links to the TTS systems that you used"*

- **Author Acknowledgement:** Concur. Exact reproducible links were missing.
- **Completed Action:** *[COMPLETED]* Added exact Hugging Face checkpoint identifiers, repository URLs, and API engine details to Table 1 and Section 3:
  - Indic-Parler-TTS: `ai4bharat/indic-parler-tts` (`https://huggingface.co/ai4bharat/indic-parler-tts`)
  - MMS-TTS: `facebook/mms-tts-urd-script_arabic` (`https://huggingface.co/facebook/mms-tts-urd-script_arabic`)
  - Microsoft Edge TTS: voice `ur-PK-AsadNeural` via `edge-tts` (Microsoft Speech Services)
  - Google Gemini TTS: model `gemini-2.5-flash-preview-tts`, voice `charon` (Google Generative AI)
- **Manuscript Location:** Table 1, Section 3.2.
- **Status:** **[COMPLETED]**

---

### Comment R1-09 & AUD-006: Upsampling Spectral Artifact in MCD
> *"DId you upsample the data for MCD? If so, then there is no information in the 8k-11k frequency band for the original samples."*

- **Author Acknowledgement:** Concur. Reviewer #1 astutely identified a potential Nyquist band artifact.
- **Completed Action:**
  1. *[COMPLETED]* Forensic audit of `f0_mcd_global_summary.json` proved that the evaluation script actually ran at `sr: 16000`, contradicting the manuscript text claim of 22.05 kHz resampling!
  2. *[COMPLETED]* Corrected the manuscript text to align with the empirical 16 kHz execution config, eliminating false upsampling claims (`AUD-006`).
  3. *[COMPLETED]* Documented the 8 kHz Nyquist limit and its implications for spectral evaluation in Section 5.3.
- **Manuscript Location:** Section 5.3, Section 6.2.
- **Status:** **[COMPLETED]**

---

### Comment R1-11: MUSHRA 5-Point Discrete Scale Defeats Protocol Purpose
> *"You used a 5-point scale for the MUSHRA evaluation. This defeats its purpose, and you somehow fell back to MOS ratings, rather than exploit the MUSHRA advantages."*

- **Author Acknowledgement:** Concur. Applying a discrete 1–5 scale without rating the hidden reference or anchor violates ITU-R BS.1534 and strips MUSHRA of its differential sensitivity.
- **Completed Action:**
  1. *[COMPLETED]* Candidly acknowledged this protocol deviation in the manuscript. Retitled the historical evaluation from "MUSHRA" to "Reference-Anchored Discrete Perceptual Rating" (`04_METHODS_AND_VALIDITY_REPAIR.md`).
  2. *[PLANNED]* Designed a compliant webMUSHRA listening campaign with continuous 0–100 sliders, rated hidden reference, rated anchor, and automated rater post-screening (`07_SUBJECTIVE_STUDY_REDESIGN.md`).
- **Manuscript Location:** Section 5.1, Section 7.1.
- **Status:** **[COMPLETED in working copy / Web Study PLANNED]**

---

### Comment R1-12: Exclusive Use of Male-Only Data
> *"Why did you use only male data?"*

- **Author Acknowledgement:** Concur. The rationale and generalizability boundaries were omitted.
- **Completed Action:** *[COMPLETED]* Documented the technical rationale: given limited multi-speaker Urdu corpora, male-only speech was chosen to prevent cross-gender fundamental frequency mismatch from overwhelming the acoustic comparison. Explicitly documented the male-only restriction as a primary threat to external validity in the Discussion limitations (`04_METHODS_AND_VALIDITY_REPAIR.md`).
- **Manuscript Location:** Section 4.1, Section 8.4.
- **Status:** **[COMPLETED]**

---

### Comment R1-13 & R1-14: Listening Setup on Webpage & Scale Discrepancy (960 Pairs vs 24 Items)
> *"The setup of the MUSHRA listening test could have been performed in a webpage, and no installation would have been required on the listener's side. I commend the time you spent on setting up Google Forms for the listening test. If indeed you evaluated that many utterances and domain pairs, that would have taken quite a lot of effort."*

- **Author Acknowledgement:** Reviewer #1 rightly suspected an impossible listening burden. The manuscript text erroneously implied all 960 pairs received human ratings. In reality, the listening test evaluated 6 source utterances per domain (24 items total across 4 domains), as documented in `dataset_used.md`.
- **Completed Action:**
  1. *[COMPLETED]* Corrected the manuscript pipeline description immediately. Clarified that 960 pairs were evaluated by automated acoustic and embedding metrics, whereas human perceptual ratings were collected over a representative subset of 24 source utterances ($24 \times 4 = 96$ system stimuli) (`AUD-014`).
  2. *[PLANNED]* Adopted an interactive web-based interface (`webMUSHRA`) for the prospective study (`07_SUBJECTIVE_STUDY_REDESIGN.md`).
- **Manuscript Location:** Section 5.0, Section 5.1.
- **Status:** **[COMPLETED in text / Web Platform PLANNED]**

---

### Comment R1-15: Low Perceptual Ratings for Commercial Urdu Systems
> *"I am a bit surprised by the low ratings in the MUSHRA results. I would imagine that commercial Urdu systems are quite close to natural speech."*

- **Author Acknowledgement:** Concur. Context was needed to interpret why commercial models achieved mean scores near ~3.0 on a 5-point scale.
- **Completed Action:** *[COMPLETED]* Added contextual analysis in Section 7.1 and Discussion: (1) raters evaluated domain-specific prompts, especially emotional speech where Gemini scored 2.167 and Edge scored 1.963, dragging down overall aggregates; (2) presenting an explicit natural studio reference reduced rater generosity compared to isolated absolute MOS; (3) commercial neural voices in lower-resource languages like Urdu lag significantly behind English counterparts in prosodic flexibility.
- **Manuscript Location:** Section 7.1, Section 8.1.
- **Status:** **[COMPLETED]**

---

## 3. Response to Reviewer #2

### Comment R2-01: Fake Citations (Jain, Wang, Pashto)
> *"I. There are fake citations: 1. Jain, P., et al., 2022. 'Towards building text-to-speech systems for the next billion users', arXiv:2211.09536 -- does not exist. The title is listed under another author, Kumar et al., 2022. 2. Wang, H. 2023b InterSpeech Generalised zero-shot text-to-speech via voice embedding. -- does not exist 3. Anonymous, 2025. PashtoTTS-bench: Automated screening for lowresource non-Latin-script text-to-speech. arXiv:2605.26978. -- is not anonymous."*

- **Author Acknowledgement:** We are profoundly grateful to Reviewer #2 for identifying these severe bibliographic errors. As detailed in our response to Editor Comment ED-02, these were critical integrity defects.
- **Completed Action:**
  1. *[COMPLETED]* Replaced `jain2023indicTTS` with the verified ICASSP 2023 paper: Gokul Karthik Kumar et al. (`kumar2023indic`).
  2. *[COMPLETED]* Completely excised `wang2023gzstvZS` from `.bib` and prose.
  3. *[COMPLETED]* Replaced `pashto2025bench` with Hanif Rahman (May 2026, `rahman2026pashto`).
  4. *[COMPLETED]* Audited all 28 entries, discovering and fixing three additional author misattributions (`varadhan2024mushra`, `naseem2024developing`, `jamal2022transfer`).
- **Manuscript Location:** `cas-refs.bib`, Section 2.
- **Status:** **[COMPLETED]**

---

### Comment R2-02: Confusing Terminology ("Metrics" vs Constructs)
> *"The authors' use of the term 'metrics' is confusing. Metrics are those attributes over which opinion is collected (e.g, naturalness, human-likeness, quality). Why does this set of authors use the word 'metrics' when they actually mean an evaluation technique."*

- **Author Acknowledgement:** Concur. Our terminology was imprecise.
- **Completed Action:** *[COMPLETED]* Standardized terminology throughout the manuscript: distinguishing *evaluation techniques / protocols* (MUSHRA rating, ABX forced choice, acoustic feature analysis) from *evaluated constructs / perceptual attributes* (intelligibility, naturalness, domain appropriateness, spectral distance) (`04_METHODS_AND_VALIDITY_REPAIR.md`).
- **Manuscript Location:** Title, Section 1, Section 5, Table 2.
- **Status:** **[COMPLETED]**

---

### Comment R2-03: Construct of "Naturalness" & Urdu Translation Instructions
> *"Additionally, the use of the term 'naturalness' is slightly worrisome in multilingual contexts. Please consider these references: - S. Shirali-Shahreza and G. Penn, 'Better replacement for tts naturalness evaluation,' SSW2023... - Pandey, A., Le Maguer, S., & Harte, N., 'What is naturalness?,' SSW2025... But how did you translate the word naturalness into Urdu?"*

- **Author Acknowledgement:** Concur. "Naturalness" is notoriously ambiguous, especially across languages.
- **Completed Action:**
  1. *[COMPLETED]* Integrated Shirali-Shahreza & Penn (2023) and Pandey et al. (2025) into Section 2 and Section 5.
  2. *[COMPLETED]* Deconstructed naturalness into explicit sub-constructs: fluid prosody vs intelligibility vs domain appropriateness (`07_SUBJECTIVE_STUDY_REDESIGN.md`).
  3. *[COMPLETED]* Documented the exact Urdu instructions and linguistic phrasing (*Qudrati Andaaz*, *Wazahat aur Fehm*, *Mauzooniyat*) shown to participants.
- **Manuscript Location:** Section 2.1, Section 5.1.
- **Status:** **[COMPLETED]**

---

### Comment R2-04: False Citation of Kominek & Black (2008) for Cents and F0 RMSE
> *"Finally - I cannot find sufficient citations to use 'cents' as the unit for log F0 RMSE. The Kominek and Black, 2008 paper cited as its source is the origin for MCD, not for RMSE. And it does not have the word cents at all."*

- **Author Acknowledgement:** Concur. Reviewer #2 is 100% correct. Kominek & Black (2008) is exclusively an MCD calibration paper and contains neither the word "cents" nor F0 RMSE formulas.
- **Completed Action:** *[COMPLETED]* Removed `kominek2008mcd` from all F0 RMSE, cents, and JND citations in lines 149, 501, 669, and 682. Retained Kominek & Black strictly for the MCD scaling constant. Added Fastl & Zwicker (2007) for psychoacoustic pitch scale context, explicitly noting that laboratory pure-tone JND (~5 cents) does not equate to running speech pitch thresholds (`03_REFERENCE_AND_CLAIM_AUDIT.md`).
- **Manuscript Location:** Section 1, Section 5.3.
- **Status:** **[COMPLETED]**

---

### Comment R2-05: Conflating Metric Divergence with Model Superiority ("Clear Winner")
> *"This is especially important because the paper's aim is to also find a clear winner among the TTS evaluated - and divergence in evaluation techniques confounds this problem."*

- **Author Acknowledgement:** Concur. Declaring a single overall winner when subjective ratings, spectral distances, and embedding similarities rank systems differently is methodologically flawed.
- **Completed Action:** *[COMPLETED]* Eliminated all "clear winner" rhetoric. Reframed the central discussion around **construct non-congruence**: explaining why a system with good spectral envelope fidelity (MCD) may fail in perceptual naturalness, and why multi-metric benchmarking requires reporting distinct operational dimensions rather than collapsing into an artificial scalar rank.
- **Manuscript Location:** Abstract, Section 7.5, Section 8.3, Section 9.
- **Status:** **[COMPLETED]**

