# 01: Master Issue Register

This register catalogs every issue raised by the Handling Editor, Reviewer #1, Reviewer #2, as well as critical data and methodological findings uncovered during our comprehensive local repository and statistical audit.

Each issue is assigned a permanent identifier, severity rating, file/section/line location, verified consequence, concrete corrective action, dependency, current session status, and verifiable acceptance criterion.

---

## Issue Severity Definitions

- **Critical Blocker:** Integrity, fabrication, or severe validity defect that justifies immediate desk rejection or retraction if uncorrected. Must be fully resolved before any journal submission.
- **Blocker:** Major scientific, data, or experimental gap that prevents defensible peer review. Requires new data, re-computation, or substantial structural rewrites.
- **Major:** Significant methodological, bibliographic, or numerical flaw that weakens conclusions or violates standard reporting rigor.
- **Minor:** Editorial, terminological, or presentation inconsistency that causes reader confusion.

---

## Master Table of Issues

| Issue ID | Category | Severity | Summary | Source Location | Status | Target Phase |
|---|---|---|---|---|---|---|
| **ED-001** | Editor | Critical Blocker | Fundamental methodological flaws & non-sequitur conclusions | Editorial Letter | IN PROGRESS | Phase 1–5 |
| **ED-002** | Editor | Critical Blocker | Non-existing / hallucinated references undermining research integrity | Editorial Letter | REPAIRED (Audit & Bib) | Phase 1 |
| **R1-001** | Rev 1 | Major | Related work overly narrow; Le Maguer (2024) isolated | Rev 1, Comment 1 | REPAIRED (Prose) | Phase 1 & 4 |
| **R1-002** | Rev 1 | Major | Domain control mechanism unclear; why not Parler descriptions? | Rev 1, Comment 2 | FORMULATED / PLAN | Phase 2 & 4 |
| **R1-003** | Rev 1 | Major | Ambiguous speech corpora usage and prompt pairing | Rev 1, Comment 3 | AUDITED / CLARIFIED | Phase 1 & 4 |
| **R1-004** | Rev 1 | Major | Resemblyzer training mismatch on Urdu speakers | Rev 1, Comment 4 | REPAIRED (Scope narrowed) | Phase 1 & 3 |
| **R1-005** | Rev 1 | Major | MCD and F0 RMSE invalid as quality metrics across speakers/ALMs | Rev 1, Comment 5 | REPAIRED (Reframed as acoustic diagnostics) | Phase 1 & 3 |
| **R1-006** | Rev 1 | Major | Lack of modern objective metrics (Auto MOS, WER/CER) | Rev 1, Comment 6 | SPECIFIED | Phase 3 |
| **R1-007** | Rev 1 | Major | Inaccurate claim that past 5 years of TTS used only MOS | Rev 1, Comment 7 | REPAIRED (Prose) | Phase 1 |
| **R1-008** | Rev 1 | Major | Missing exact links, versions, and checkpoints for TTS engines | Rev 1, Comment 8 | REPAIRED (Documented) | Phase 1 |
| **R1-009** | Rev 1 | Major | Upsampling spectral artifact in MCD (16 kHz vs 22.05 kHz) | Rev 1, Comment 9 | AUDITED / CLARIFIED | Phase 1 & 3 |
| **R1-010** | Rev 1 | Major | Insufficient operational detail on domain manipulation | Rev 1, Comment 10 | REPAIRED (Confound acknowledged) | Phase 1 & 4 |
| **R1-011** | Rev 1 | Major | MUSHRA 5-point scale defeats purpose; collapses to MOS | Rev 1, Comment 11 | REPAIRED (Relabeled & Protocol Planned) | Phase 1 & 2 |
| **R1-012** | Rev 1 | Major | Unjustified restriction to male-only speech data | Rev 1, Comment 12 | REPAIRED (Limitations documented) | Phase 1 & 2 |
| **R1-013** | Rev 1 | Minor | Google Forms interface vs dedicated web listening platform | Rev 1, Comment 13 | PLANNED (Web platform spec) | Phase 2 |
| **R1-014** | Rev 1 | Critical Blocker | Implication that 960 pairs were evaluated in human listening | Rev 1, Comment 14 | REPAIRED (Prose corrected to 24 samples) | Phase 1 |
| **R1-015** | Rev 1 | Major | Low perceptual ratings of commercial systems unexplained | Rev 1, Comment 15 | REPAIRED (Contextualized) | Phase 1 & 4 |
| **R2-001** | Rev 2 | Critical Blocker | Corrupted citation: `jain2023indicTTS` (Gokul Karthik Kumar et al.) | Rev 2, Weakness I.1 | REPAIRED (Bib & In-text) | Phase 1 |
| **R2-002** | Rev 2 | Critical Blocker | Hallucinated citation: `wang2023gzstvZS` (Non-existent paper) | Rev 2, Weakness I.2 | REPAIRED (Removed from bib/text) | Phase 1 |
| **R2-003** | Rev 2 | Critical Blocker | Corrupted metadata: `pashto2025bench` (Hanif Rahman, May 2026) | Rev 2, Weakness I.3 | REPAIRED (Bib & In-text) | Phase 1 |
| **R2-004** | Rev 2 | Major | Outdated objective evaluation; lack of VoiceMOS / modern predictors | Rev 2, Weakness II | SPECIFIED (VoiceMOS roadmap) | Phase 3 |
| **R2-005** | Rev 2 | Minor | Confusing terminology: "metrics" vs perceptual constructs | Rev 2, Weakness III.1 | REPAIRED (Prose terminology) | Phase 1 |
| **R2-006** | Rev 2 | Major | Ambiguous "naturalness"; missing Urdu translation & SSW literature | Rev 2, Weakness III.2 | REPAIRED (Cited & Protocol designed) | Phase 1 & 2 |
| **R2-007** | Rev 2 | Major | False citation of Kominek & Black (2008) for "cents" and 5-cent JND | Rev 2, Weakness III.3 | REPAIRED (Attribution corrected) | Phase 1 |
| **R2-008** | Rev 2 | Major | Conflating metric divergence with system superiority ("clear winner") | Rev 2, Recommendation | REPAIRED (Prose rewritten) | Phase 1 & 4 |
| **AUD-001**| Audit | Critical Blocker | Exact duplicate MCD & F0 scores for Indic-Parler & MMS on FLEURS | CSV / Table 10 & 12 | AUDITED & FLAGGED | Phase 1 & 3 |
| **AUD-002**| Audit | Major | Table 7 Speaker Similarity Bolding Error (bolds 0.6312 over 0.6329) | Table 7, Line 1021 | REPAIRED (LaTeX bolding) | Phase 1 |
| **AUD-003**| Audit | Major | Tables 10 & 12 Overall Mean double-weights Formal speech (unweighted 5-row mean) | Tables 10 & 12 | AUDITED & EXPLAINED | Phase 1 & 4 |
| **AUD-004**| Audit | Major | Missing F0 scores (rows 86 & 169) concealed by `ok=True` & `n_ok=960` | JSON / CSV scores | AUDITED & CORRECTED | Phase 1 |
| **AUD-005**| Audit | Major | Tables 11 & 12 report `f0_rmse_cents_raw` without documentation | Table 11 & 12 | AUDITED & RECONCILED | Phase 1 |
| **AUD-006**| Audit | Major | Mismatch between text (22.05 kHz) and JSON config (16 kHz) for MCD | Line 661 vs JSON | REPAIRED (Text aligned to evidence) | Phase 1 |
| **AUD-007**| Audit | Major | Nonsensical ABX protocol ("reference A and same reference B" matching) | Lines 585–589 | REPAIRED (Acknowledged as broken prose) | Phase 1 & 2 |
| **AUD-008**| Audit | Major | Inconsistent ABX counts (10 vs 9 listeners) and model names | Lines 603, 921, 925 | REPAIRED (Prose reconciled) | Phase 1 |
| **AUD-009**| Audit | Major | False claim of deterministic synthesis (`do_sample=True, temp=0.8`) | Notebooks vs Line 756 | REPAIRED (Claim removed) | Phase 1 |
| **AUD-010**| Audit | Major | Confounded domain design (corpora, recording quality, acoustic mismatch) | Corpus setup | REPAIRED (Framed as limitation) | Phase 1 & 4 |
| **AUD-011**| Audit | Major | Baseless sociolinguistic assumption of native Urdu from Lahore residence | Line 541–543 | REPAIRED (Removed false claim) | Phase 1 & 2 |
| **AUD-012**| Audit | Critical Blocker | Incomplete / unverified Generative AI disclosure | Line 1504 | REPAIRED (Transparent audit trail) | Phase 1 |
| **AUD-013**| Audit | Blocker | Missing raw generated audio, listener forms, and pipeline scripts | Repo inventory | INVENTORY & RECOVERY PLAN | Phase 1 & 2 |
| **AUD-014**| Audit | Minor | Unused reference included only via `\nocite{*}` (`conneau2022fleurs`) | Line 1511 / Bib | REPAIRED (`\nocite{*}` removed) | Phase 1 |
| **AUD-015**| Audit | Critical Blocker | Misattributed author: `chiang2024mushra` (Varadhan et al.) & `chiang2024mushraevaluate` | Bib entries 16 & 20 | REPAIRED (Bib corrected) | Phase 1 |
| **AUD-016**| Audit | Critical Blocker | Misattributed authors: `naseem2025urdu` (Fatima Naseem) & `arshad2022transfer` (Sahar Jamal) | Bib entries 11 & 12 | REPAIRED (Bib corrected) | Phase 1 |

---

## Detailed Issue Specifications

### ED-001: Methodological Flaws & Non-Sequitur Conclusions
- **Quotation:** *"Both reviewers agree that even though the overall research question is of interest, the manuscript has significant methodological flaws, does not take into account the current state of the art, and draws conclusions that do not follow from the reported study."*
- **Severity:** Critical Blocker.
- **Evidence:** Subjective test presented as standard MUSHRA despite 1–5 discrete scale and unrated references; objective metrics (MCD, F0, speaker similarity) computed across mismatched speakers and unaligned speech; causal claims made about domain difficulty despite severe corpus confounding.
- **Action:** Systematically re-scope the manuscript: relabel listening test, reframe signal metrics as descriptive acoustic diagnostics, qualify all causal domain claims, design clean protocol for new experiments.
- **Dependency:** R1-005, R1-011, R2-004, AUD-010.
- **Acceptance Criterion:** All claims in abstract, results, and discussion strictly bounded by reported experimental conditions without overgeneralization.

### ED-002: Hallucinated / Fabricated References
- **Quotation:** *"More gravely, one reviewer remarks that the manuscript contains non-existing, most likely hallucinated references. This point alone throws a serious doubt on the scientific rigour and overall integrity of the conducted research and writing process."*
- **Severity:** Critical Blocker.
- **Evidence:** Bibliographic audit confirmed 5 corrupted or fabricated entries (`wang2023gzstvZS`, `jain2023indicTTS`, `pashto2025bench`, `chiang2024mushra`, `naseem2025urdu`, `arshad2022transfer`).
- **Action:** Audit all 28 entries in `cas-refs.bib`, eliminate non-existent papers, correct all author lists, DOIs, years, and venues from primary authoritative sources; remove `\nocite{*}`.
- **Dependency:** R2-001, R2-002, R2-003, AUD-015, AUD-016.
- **Acceptance Criterion:** 100% of bibliography entries correspond to verified, existing, peer-reviewed or authoritative preprints with verified metadata and DOIs/URLs.

### R1-001: Inadequate Related Work on Evaluation Flaws
- **Quotation:** *"The related work section clearly needs improvement, as LeMaguer's paper is not the only one looking into the flaws of TTS evaluation"*
- **Severity:** Major.
- **Evidence:** Section 2 relied almost exclusively on Le Maguer et al. (2024), overlooking foundational critique literature (Kirkland et al. 2023, SSW 2023/2025, VoiceMOS challenge series).
- **Action:** Expand Section 2 with comprehensive synthesis of evaluation challenges, including Kirkland et al. (2023 "Stuck in the MOS pit"), Shirali-Shahreza & Penn (2023), Pandey et al. (2025), and Cooper et al. (2024).
- **Dependency:** R2-006, R1-006.
- **Acceptance Criterion:** Related work contextualizes TTS evaluation limitations through multi-faceted literature rather than a single citation.

### R1-002 & R1-010: Domain Control & Parler Prompting Mechanism
- **Quotation:** *"The domain selection is appropriate, however, it is not clear how you control for the domains. Is it just the input text? Why not use the description for ParlerTTS to control the output? ... Please add more details on how you control for the 4 domains."*
- **Severity:** Major.
- **Evidence:** Notebook `Conversational/ipynb_files/humair__indic_parler.ipynb` proves that Indic-Parler used a static, unvarying male prompt ("Rohit's voice is clear and natural...") across ALL domains. Edge used fixed `ur-PK-AsadNeural`; Gemini used fixed `charon`. Domains were solely manipulated by selecting text prompts from different corpora.
- **Action:** Explicitly disclose that domain variation was introduced solely via input text prompts and source corpora; explicitly state that system voice profiles and Parler descriptions were held constant as neutral baselines; formulate style-conditioned prompting as a concrete planned experiment.
- **Dependency:** AUD-009, AUD-010.
- **Acceptance Criterion:** Manuscript transparently distinguishes text-domain robustness from voice style-conditioning, eliminating reader confusion.

### R1-003: Speech Corpora Usage and Transcript Pairing
- **Quotation:** *"It is not clear how you truly use the selected speech corpora? Do you use each utterance to control the output of the TTS? Do you use the same input text as in the original utterance?"*
- **Severity:** Major.
- **Evidence:** Manuscript lines 493–497 state reference recordings were paired with synthetic outputs at utterance level. Inspection of notebooks confirms reference text was fed to TTS engines to synthesize corresponding audio.
- **Action:** Clarify the exact prompt-synthesis-reference pipeline: reference transcripts were extracted from corpora, fed as verbatim text prompts to TTS engines, and resulting synthetic audio was paired with the source speaker's audio for acoustic and perceptual comparison.
- **Dependency:** None.
- **Acceptance Criterion:** Clear, unambiguous pipeline diagram and text explanation in Section 4 and Section 5.

### R1-004: Resemblyzer Urdu Acoustic Mismatch
- **Quotation:** *"Was the Resemblyzer model trained on Urdu speakers? If not, there might be a mismatch between the training and test data, hence unreliable similarity measures."*
- **Severity:** Major.
- **Evidence:** Resemblyzer uses Wan et al. (2018) GE2E encoder trained on English LibriSpeech and VoxCeleb. It was never trained or fine-tuned on Urdu phonology or South Asian acoustic distributions.
- **Action:** Document the English pretraining of Resemblyzer as an explicit threat to construct validity; explain out-of-domain embedding limitations; reframe Resemblyzer scores not as true speaker identity preservation, but as generic deep acoustic feature distance.
- **Dependency:** None.
- **Acceptance Criterion:** Section 5.3 and Section 8 candidly state encoder pre-training language and domain mismatch limitations.

### R1-005: MCD and F0 RMSE Validity Across Systems & Different Speakers
- **Quotation:** *"MCD and F0 RMSE are not realiable measures of quality. They were used in previous TTS technologies, when the alignment between input and output was easier to perform. Nowadays, especially for ALMs, I do not believe that DTW alone can perform such measure. Also, if there are different speakers, as in the MMS systems, this would clearly generate a random value, and not a true measure of quality."*
- **Severity:** Major.
- **Evidence:** The reference speech was produced by different human speakers (e.g. Humair Awan, FLEURS speakers, Mendeley actors), whereas TTS systems generated speech in arbitrary fixed voices (e.g. Asad, Charon, Rohit). Comparing pitch and spectral envelope across different human and synthetic vocal tracts reflects speaker anatomy and recording channels, not synthesis quality.
- **Action:** Remove claims that MCD and F0 RMSE measure synthesis "quality" or "accuracy". Reframe them strictly as acoustic similarity/distance to the reference recordings, noting that register offsets and DTW path distortions across differing speaker identities confound the metric.
- **Dependency:** R2-007, AUD-005, AUD-006.
- **Acceptance Criterion:** Terminology throughout results and discussion updated from "quality" to "reference-relative acoustic divergence".

### R1-006 & R2-004: Modern Objective Metrics (VoiceMOS, WER/CER)
- **Quotation:** *"What about using automatic MOS ratings? And what about WER? Both measures are common in today's literature."* / *"The authors are encouraged to follow the work of Cooper et al., particularly originating in the VoiceMOS challenge."*
- **Severity:** Major.
- **Evidence:** The manuscript evaluated zero intelligibility metrics (WER/CER) and zero machine-learned MOS predictors, relying exclusively on 1990s/2000s signal metrics.
- **Action:** Formulate an exhaustive objective evaluation plan (`08_OBJECTIVE_EVALUATION_PLAN.md`) incorporating Whisper/MMS ASR for normalized Urdu WER/CER, natural speech baselines, and a concrete roadmap for SSL-based VoiceMOS automatic MOS predictors validated on held-out Urdu listener ratings.
- **Dependency:** AUD-013 (requires audio recovery or regenerated synthesis).
- **Acceptance Criterion:** Full operational specification and software pipeline designed for Urdu WER/CER and automated MOS estimation.

### R1-007: Inaccurate Claim Regarding 5 Years of MOS-Only TTS Evaluation
- **Quotation:** *"You mention that previous evaluations of TTS systems was performed using only MOS ratings. That is not true for the past 5 years of scientific publications at least."*
- **Severity:** Major.
- **Evidence:** Manuscript line 121 claimed: *"traditional speech evaluation methodologies have remained overwhelmingly reliant on Mean Opinion Score (MOS) listening tests..."* and implied contemporary literature rarely uses multi-metric benchmarks.
- **Action:** Rewrite Introduction and Related Work to acknowledge that Blizzard Challenges, VoiceMOS Challenges, and modern TTS literature have widely utilized multi-metric evaluation (ASR-WER, UTMOS, SECS, MUSHRA, BWS) for years.
- **Dependency:** None.
- **Acceptance Criterion:** Overbroad historical assertions replaced with nuanced literature contextualization.

### R1-008: Missing Links and System Checkpoint Details
- **Quotation:** *"You need to add the exact links to the TTS systems that you used"*
- **Severity:** Major.
- **Evidence:** Section 3 and Table 1 provided high-level descriptions but omitted exact Hugging Face checkpoint IDs, model card URLs, API engine endpoints, and release tags.
- **Action:** Update Table 1 and system descriptions with exact repository links:
  - Indic-Parler-TTS: `ai4bharat/indic-parler-tts` (`https://huggingface.co/ai4bharat/indic-parler-tts`)
  - MMS-TTS: `facebook/mms-tts-urd-script_arabic` (`https://huggingface.co/facebook/mms-tts-urd-script_arabic`)
  - Microsoft Edge TTS: `ur-PK-AsadNeural` via `edge-tts` Python library (API engine: Microsoft Cognitive Services)
  - Google Gemini TTS: `gemini-2.5-flash-preview-tts` (voice: `charon`, Google Generative AI API)
- **Dependency:** None.
- **Acceptance Criterion:** Table 1 and text contain exact actionable links and reproducible checkpoint names.

### R1-009 & AUD-006: Upsampling Spectral Artifact & Resampling Discrepancy
- **Quotation:** *"DId you upsample the data for MCD? If so, then there is no information in the 8k-11k frequency band for the original samples."*
- **Severity:** Major.
- **Evidence:** Line 348 and line 661 stated that audio was resampled to 22.05 kHz for MCD. However, `evaluation/results/f0_mcd_global_summary.json` shows the evaluation config was `sr: 16000`! If audio was 16 kHz native (MMS), upsampling to 22.05 kHz creates an empty Nyquist band (8–11 kHz).
- **Action:** Clarify the actual sampling rate used in evaluation (16 kHz in data artifact); eliminate misleading 22.05 kHz claims; document the high-frequency spectral limitation in the limitations section.
- **Dependency:** None.
- **Acceptance Criterion:** Manuscript text matches `global_summary.json` execution parameters exactly.

### R1-011: MUSHRA Protocol Degradation to MOS
- **Quotation:** *"You used a 5-point scale for the MUSHRA evaluation. This defeats its purpose, and you somehow fell back to MOS ratings, rather than exploit the MUSHRA advantages."*
- **Severity:** Major.
- **Evidence:** Section 5.1 described the protocol as MUSHRA, yet used a 1–5 discrete rating scale, did not rate the hidden reference or anchor, and administered via Google Forms without continuous sliders or instant comparative switching.
- **Action:** Acknowledge this protocol deviation candidly. Re-classify the historical study as a "Reference-Anchored Discrete Perceptual Rating" (or multi-stimulus MOS variant). Formulate a true ITU-R BS.1534-compliant web MUSHRA redesign in `07_SUBJECTIVE_STUDY_REDESIGN.md`.
- **Dependency:** None.
- **Acceptance Criterion:** All sections stop misrepresenting the test as standard MUSHRA; deviations are rigorously documented.

### R1-012: Male-Only Data Without Justification
- **Quotation:** *"Why did you use only male data?"*
- **Severity:** Major.
- **Evidence:** All four datasets and synthesis presets were restricted to male speakers to avoid cross-gender acoustic mismatch. However, this severely limits generalizability to female voices and diverse vocal registers.
- **Action:** Document the scientific rationale (controlling for gender-induced F0 variance across systems given limited available multi-speaker Urdu corpora); explicitly add the lack of female speakers as a major threat to external validity in Section 8.
- **Dependency:** None.
- **Acceptance Criterion:** Rationale and severe generalizability limitation explicitly stated in Methodology and Limitations sections.

### R1-014: Listening Test Scale Ambiguity (960 Pairs vs 24 Samples)
- **Quotation:** *"I commend the time you spent on setting up Google Forms for the listening test. If indeed you evaluated that many utterances and domain pairs, that would have taken quite a lot of effort."*
- **Severity:** Critical Blocker.
- **Evidence:** Manuscript lines 495–498 stated: *"yielding 960 audio pairs in total... Each pair is then passed through four evaluation modules: a subjective MUSHRA-style listening test..."* In contrast, repository documentation (`dataset_used.md`) explicitly confirms that perceptual listening tests only evaluated **6 samples per domain** (24 samples total).
- **Action:** Correct the manuscript pipeline description immediately. State clearly that automated embedding and acoustic metrics evaluated all 960 pairs (240 per system), whereas the subjective listening evaluation evaluated a representative subset of 6 source utterances per domain (24 source utterances x 4 systems = 96 system stimuli).
- **Dependency:** None.
- **Acceptance Criterion:** Manuscript accurately distinguishes the 960-pair objective evaluation corpus from the 24-utterance subjective evaluation subset.

### R1-015: Low Perceptual Ratings for Commercial Systems
- **Quotation:** *"I am a bit surprised by the low ratings in the MUSHRA results. I would imagine that commercial Urdu systems are quite close to natural speech."*
- **Severity:** Major.
- **Evidence:** Table 4 reported overall mean scores of 2.947 for Edge TTS and 3.040 for Gemini TTS on a 1–5 scale.
- **Action:** Contextualize these findings: (1) raters evaluated domain-specific prompts (especially emotional speech where Gemini scored 2.167 and Edge scored 1.963, dragging down the overall mean); (2) raters compared synthetic speech directly against high-quality human studio references, preventing artificial ceiling effects seen in isolated ACR tests; (3) commercial engines often suffer in low-resource languages compared to English benchmarks.
- **Dependency:** None.
- **Acceptance Criterion:** Section 7.1 and Discussion explain the rater dynamics and domain drag underlying the scores.

### R2-001: Corrupted Citation `jain2023indicTTS`
- **Quotation:** *"Jain, P., et al., 2022. 'Towards building text-to-speech systems for the next billion users', arXiv:2211.09536 -- does not exist. The title is listed under another author, Kumar et al., 2022."*
- **Severity:** Critical Blocker.
- **Evidence:** Author list in `cas-refs.bib` was `Jain, Praveen and others`. Authoritative arXiv and ICASSP 2023 record proves authors are: Gokul Karthik Kumar, Praveen S V, Pratyush Kumar, Mitesh M. Khapra, and Karthik Nandakumar.
- **Action:** Replace `jain2023indicTTS` in `cas-refs.bib` with verified ICASSP 2023 entry (`kumar2023indic`); update citation in manuscript text.
- **Dependency:** None.
- **Acceptance Criterion:** Correct citation key and metadata verified in bibliography and text.

### R2-002: Hallucinated Citation `wang2023gzstvZS`
- **Quotation:** *"Wang, H. 2023b InterSpeech Generalised zero-shot text-to-speech via voice embedding. -- does not exist"*
- **Severity:** Critical Blocker.
- **Evidence:** `cas-refs.bib` line 67 lists `wang2023gzstvZS`. No such paper exists in Interspeech or any academic database.
- **Action:** Remove `wang2023gzstvZS` completely from `cas-refs.bib` and remove in-text citations from line 149 and elsewhere.
- **Dependency:** None.
- **Acceptance Criterion:** Zero occurrences of `wang2023gzstvZS` in `.bib` or `.tex`.

### R2-003: Corrupted Citation `pashto2025bench`
- **Quotation:** *"Anonymous, 2025. PashtoTTS-bench: Automated screening for lowresource non-Latin-script text-to-speech. arXiv:2605.26978. -- is not anonymous."*
- **Severity:** Critical Blocker.
- **Evidence:** `cas-refs.bib` line 154 lists `author={Anonymous}, year={2025}` for `arXiv:2605.26978`. The actual paper is authored by Hanif Rahman, submitted May 26, 2026 (`arXiv:2605.26978`).
- **Action:** Update bib entry to `rahman2026pashto` with correct author `Rahman, Hanif`, year `2026`, and verified title. Update in-text citations.
- **Dependency:** None.
- **Acceptance Criterion:** Valid metadata matching arXiv:2605.26978.

### R2-005: Conceptual Confusion Over "Metrics"
- **Quotation:** *"The authors' use of the term 'metrics' is confusing. Metrics are those attributes over which opinion is collected (e.g, naturalness, human-likeness, quality). Why does this set of authors use the word 'metrics' when they actually mean an evaluation technique."*
- **Severity:** Minor.
- **Evidence:** The manuscript indiscriminately called MUSHRA, ABX, Resemblyzer, and MCD "evaluation metrics".
- **Action:** Adopt psychometric terminology: distinguish *evaluation protocols / methods* (MUSHRA-style rating, ABX test, acoustic signal analysis) from *measured constructs / attributes* (intelligibility, clarity, appropriateness, acoustic distance, pitch deviation).
- **Dependency:** None.
- **Acceptance Criterion:** Terminology cleaned and standardized across title, abstract, methodology, and tables.

### R2-006: Definition of "Naturalness" and Urdu Instructions
- **Quotation:** *"Additionally, the use of the term 'naturalness' is slightly worrisome in multilingual contexts. Please consider these references: - S. Shirali-Shahreza and G. Penn, 'Better replacement for tts naturalness evaluation,' SSW2023... - Pandey, A., Le Maguer, S., & Harte, N., 'What is naturalness?,' SSW2025... But how did you translate the word naturalness into Urdu?"*
- **Severity:** Major.
- **Evidence:** Manuscript lines 531–535 defined Naturalness, Clarity, and Quality in English, but omitted the Urdu phrasing given to native raters.
- **Action:** Integrate Shirali-Shahreza & Penn (2023) and Pandey et al. (2025) into Section 2 and Section 5; detail the exact Urdu instructions and linguistic phrasing required for native-speaker evaluation in `07_SUBJECTIVE_STUDY_REDESIGN.md`.
- **Dependency:** None.
- **Acceptance Criterion:** Literature cited, construct unpacked, and standardized Urdu rating prompt provided.

### R2-007: False Citation of Kominek & Black (2008) for Cents and F0 RMSE
- **Quotation:** *"Finally - I cannot find sufficient citations to use 'cents' as the unit for log F0 RMSE. The Kominek and Black, 2008 paper cited as its source is the origin for MCD, not for RMSE. And it does not have the word cents at all."*
- **Severity:** Major.
- **Evidence:** Lines 149, 501, 654, 669, and 682 attached `\citep{kominek2008mcd}` to F0 RMSE, the logarithmic cent formula, and the assertion that "5 cents is a JND". Kominek & Black (2008) only discusses MCD.
- **Action:** Remove `kominek2008mcd` from all F0 RMSE citations. Retain Kominek & Black strictly for MCD calculation conventions. Provide proper psychoacoustic citations for pitch representation (e.g. Ellis 1885 / Fastl & Zwicker 2007) and qualify the 5-cent pure-tone JND vs speech pitch perception.
- **Dependency:** None.
- **Acceptance Criterion:** Kominek & Black cited exclusively for MCD; F0 RMSE formula correctly cited.

### R2-008: Conflating Metric Disagreements with Model Optimization Objectives
- **Quotation:** *"This is especially important because the paper's aim is to also find a clear winner among the TTS evaluated - and divergence in evaluation techniques confounds this problem."*
- **Severity:** Major.
- **Evidence:** Discussion in Section 8 made sweeping claims that metric divergence revealed "hidden architectural trade-offs" or that systems were "specifically optimized for MCD rather than human perception".
- **Action:** Re-frame discussion: acknowledge that different evaluation paradigms measure distinct, non-congruent constructs (perceived fluency vs spectral distance to an arbitrary reference speaker). Divergence is a measurement artifact, not evidence of proprietary model optimization.
- **Dependency:** None.
- **Acceptance Criterion:** Discussion removed speculative reverse-engineering claims; focuses on construct divergence.

### AUD-001: Identical Duplicate Data on FLEURS (Indic-Parler vs MMS)
- **Severity:** Critical Blocker.
- **Evidence:** In `f0_mcd_per_file_scores.csv`, all 30 rows for `formal_subset == 'fleurs'` have 100% identical values for `mcd_db` (10.367457...), `f0_rmse_cents` (450.6066...), and `f0_rmse_cents_raw` (470.6585...) between `indic_parler` and `mmstts`. Table 10 and Table 12 printed 10.37 and 470.66 for both models.
- **Action:** Document this duplication in the audit dossier; flag as an unverified artifact requiring rerun of FLEURS synthesis; add prominent caveat in revised manuscript.
- **Dependency:** Audio recovery / new generation.
- **Acceptance Criterion:** Duplicate rows isolated, documented, and prevented from masquerading as independent system performance.

### AUD-002: Table 7 Speaker Similarity Bolding Error
- **Severity:** Major Formatting / Integrity.
- **Evidence:** In Table 7 (Line 1021), Overall Mean for Edge TTS is 0.6329, while Indic-Parler-TTS is 0.6312. The manuscript text bolds `\textbf{0.6312}`.
- **Action:** Correct bolding in LaTeX source: `\textbf{0.6329}` on Edge TTS, unbold Indic-Parler-TTS.
- **Dependency:** None.
- **Acceptance Criterion:** Correct maximum value bolded in Table 7.

### AUD-003: Double-Weighting of Formal Speech in Tables 10 & 12 Overall Means
- **Severity:** Major Numerical.
- **Evidence:** Overall means in Table 10 (Edge 7.91, Gemini 9.79, Indic 8.41, MMS 9.93) and Table 12 (Edge 565.00, Gemini 646.10, Indic 614.11, MMS 573.17) represent an unweighted arithmetic average of 5 table rows (Conv, Lit, Formal FLEURS, Formal UrduSpeech, Emotional) rather than a pooled average of 240 samples. This assigned a 40% weight to Formal speech instead of 25%.
- **Action:** Document exact formula used in manuscript table; provide recalculated pooled sample means alongside row averages in audit reports; add clear explanatory footnote in revised tables.
- **Dependency:** None.
- **Acceptance Criterion:** Denominators and weighting explicitly documented in revised tables.

### AUD-004: Missing F0 Rows (86 & 169) Concealed by `ok=True`
- **Severity:** Major Data Reporting.
- **Evidence:** In `f0_mcd_per_file_scores.csv`, row 86 (Conversational, Gemini, sample_32) and row 169 (Conversational, Indic-Parler, sample_53) have NaN for F0 RMSE columns due to `n_f0_frames_used = 0`. Yet `ok=True` and `global_summary.json` claims `n_ok: 960, n_fail: 0`.
- **Action:** Document valid denominators: n=240 for Edge and MMS; n=239 for Gemini and Indic-Parler. Update text from "all 960 pairs evaluated without failure" to exact reporting of voiced-frame alignment failures.
- **Dependency:** None.
- **Acceptance Criterion:** Denominators reported accurately (958 valid F0 pairs).

### AUD-005: Reporting of `f0_rmse_cents_raw` Without Disclosure
- **Severity:** Major Numerical.
- **Evidence:** Recalculation confirmed that Table 11 and Table 12 reported numbers from the `f0_rmse_cents_raw` column (e.g. Emotional 888.54 cents), while `f0_rmse_cents` (standard) had a mean of 620.24 cents. The manuscript text never distinguished the two columns.
- **Action:** Reconcile column definitions in the audit dossier; clarify the difference between raw pitch contour comparison and register-normalized contour alignment.
- **Dependency:** None.
- **Acceptance Criterion:** Complete explanation of raw vs transformed F0 columns provided in methods audit.

### AUD-007: Nonsensical ABX Stimulus Presentation Description
- **Severity:** Major Methodological.
- **Evidence:** Lines 585–589 state: *"In each ABX trial, listeners were presented with three stimuli: a reference utterance (A), a second presentation of the same reference (B), and an unknown sample (X)... Listeners indicated whether X was perceptually more similar to A or to B."* If A and B are identical, the comparison is impossible.
- **Action:** Label this as an unresolved protocol description error in the working draft; formulate a defensible ABX protocol (A = Natural Reference, B = Synthetic Output, X = Unknown token) in `07_SUBJECTIVE_STUDY_REDESIGN.md`.
- **Dependency:** Author clarification on what Google Forms actually presented.
- **Acceptance Criterion:** Flawed text removed or flagged with conspicuous author TODO.

### AUD-008: ABX Reporting Inconsistencies
- **Severity:** Major Consistency.
- **Evidence:** Line 574 names Edge TTS and Gemini TTS. Line 603 says 10 listeners per domain pair. Line 921 says *"MMS-TTS and Gemini-TTS"*. Line 924 caption says *"Edge-TTS vs. Gemini-TTS... 9 listeners x 6 samples"*.
- **Action:** Reconcile system names (Edge vs Gemini) and sample counts (9 vs 10 listeners) across all ABX sections.
- **Dependency:** Author confirmation of raw survey records.
- **Acceptance Criterion:** All ABX sections report identical systems and sample counts.

### AUD-009: False Claim of Deterministic Synthesis
- **Severity:** Major Validity.
- **Evidence:** Line 756 and line 791 claim synthesis was deterministic. Notebook `humair__indic_parler.ipynb` proves Parler-TTS was run with `do_sample=True, temperature=0.8` without random seed pinning. Edge and Gemini are closed cloud APIs subject to server-side updates.
- **Action:** Remove false claims of deterministic synthesis; document sampling parameters and API execution dates as reproducibility constraints.
- **Dependency:** None.
- **Acceptance Criterion:** Synthesis stochasticity and provider version volatility truthfully acknowledged.

### AUD-010: Severe Corpus Confounding Across Domains
- **Severity:** Major Methodological.
- **Evidence:** Emotional domain used Mendeley corpus (actors); Formal domain mixed FLEURS and Wikipedia read speech; Conversational used Humair Awan. Differences in acoustic recording quality, room acoustics, speaker identity, and sentence length are heavily entangled with domain labels.
- **Action:** Demote claims that domain alone caused acoustic performance differences; thoroughly document corpus confounding as a primary limitation.
- **Dependency:** None.
- **Acceptance Criterion:** Discussion explicitly presents domain findings as corpus-entangled associations rather than isolated causal effects.

### AUD-011: Sociolinguistic Fallacy Regarding Lahore Residence
- **Severity:** Major Validity.
- **Evidence:** Lines 541–543 argued that because participants lived in Lahore, native Urdu proficiency screening was unnecessary.
- **Action:** Remove this assertion; replace with an honest statement of recruitment limitations and specify formal language screening for future studies.
- **Dependency:** None.
- **Acceptance Criterion:** Unsupported demographic inferences removed.

### AUD-012: Generative AI Writing Disclosure Integrity
- **Severity:** Critical Blocker.
- **Evidence:** Line 1504 declares Claude was used for writing. Editorial letter flagged non-existing citations as a possible consequence of unverified AI assistance.
- **Action:** Maintain a fully transparent, verifiable declaration of generative AI tool use; ensure every citation and factual claim is hand-verified against authoritative primary sources.
- **Dependency:** None.
- **Acceptance Criterion:** Disclosure is truthful, complete, and supported by a 100% verified citation registry.

### AUD-013: Absence of Audio, Survey Data, and Scripts in Repository
- **Severity:** Blocker for Resubmission.
- **Evidence:** Repository contains no audio files, no raw Google Forms CSV exports, and no execution script that produced `evaluation/results/`.
- **Action:** Create `06_DATA_RECOVERY_AND_REQUIRED_INPUTS.md` with explicit file-by-file inventory and recovery protocol for the authors.
- **Dependency:** Author response and external recovery.
- **Acceptance Criterion:** Clear classification of publication blockers vs secondary assets.

### AUD-014: Uncited Bibliography Entry (`conneau2022fleurs`)
- **Severity:** Minor Bibliographic.
- **Evidence:** `cas-refs.bib` contained `conneau2022fleurs`, which was never cited in text and only appeared in the bibliography due to `\nocite{*}`.
- **Action:** Remove `\nocite{*}` from LaTeX; add explicit citation `\citep{conneau2022fleurs}` in Section 4.1 where FLEURS is introduced.
- **Dependency:** None.
- **Acceptance Criterion:** No uncited references; `\nocite{*}` eliminated.

### AUD-015 & AUD-016: Additional Corrupted Bibliography Metadata
- **Severity:** Critical Blocker.
- **Evidence:**
  - `chiang2024mushra`: arXiv:2411.12719 was authored by Praveen Srinivasa Varadhan et al., not Christoph Chiang!
  - `chiang2024mushraevaluate`: Interspeech 2024 authors are Cheng-Han Chiang, Wei-Ping Huang, Hung-yi Lee (not Chia-Yu Chiang).
  - `naseem2025urdu`: Real paper is Fatima Naseem et al., Interspeech 2024, not "Shahid Naseem 2025".
  - `arshad2022transfer`: Real paper is Sahar Jamal, Sadaf Abdul Rauf, Quratulain Majid (LREC 2022 EurALI), not "Hafsa Arshad".
  - `pratap2023mms`: Published in JMLR 2024, not an inproceedings.
- **Action:** Correct all 5 entries in `cas-refs.bib` with authoritative author lists, titles, venues, and identifiers.
- **Dependency:** None.
- **Acceptance Criterion:** All entries match primary bibliographic records.

---

## Reviewer & Editor Coverage Checklist

- [x] **Editor:** Methodological flaws and non-sequitur conclusions -> Covered by `ED-001`, `R1-005`, `R1-011`, `R2-008`
- [x] **Editor:** Hallucinated references and scientific integrity -> Covered by `ED-002`, `R2-001`, `R2-002`, `R2-003`, `AUD-012`, `AUD-015`, `AUD-016`
- [x] **R1-Bullet 1:** Related work needs improvement beyond Le Maguer -> Covered by `R1-001`
- [x] **R1-Bullet 2:** Domain control unclear; Parler description control -> Covered by `R1-002`, `R1-010`
- [x] **R1-Bullet 3:** Corpora usage, prompts, and utterance pairing -> Covered by `R1-003`
- [x] **R1-Bullet 4:** Resemblyzer Urdu training mismatch -> Covered by `R1-004`
- [x] **R1-Bullet 5:** MCD and F0 RMSE invalid across different speakers & ALMs -> Covered by `R1-005`
- [x] **R1-Bullet 6:** Need automatic MOS and WER -> Covered by `R1-006`, `R2-004`
- [x] **R1-Bullet 7:** Erroneous claim of 5 years of MOS-only evaluation -> Covered by `R1-007`
- [x] **R1-Bullet 8:** Missing exact links to TTS systems -> Covered by `R1-008`
- [x] **R1-Bullet 9:** Upsampling spectral artifact in MCD (8k-11k band) -> Covered by `R1-009`, `AUD-006`
- [x] **R1-Bullet 10:** Operational details on domain control -> Covered by `R1-010`, `R1-002`
- [x] **R1-Bullet 11:** 5-point scale defeats MUSHRA purpose -> Covered by `R1-011`
- [x] **R1-Bullet 12:** Why only male data? -> Covered by `R1-012`
- [x] **R1-Bullet 13:** Setup on webpage vs Google Forms -> Covered by `R1-013`
- [x] **R1-Bullet 14:** Skepticism regarding evaluating so many pairs in Forms -> Covered by `R1-014`
- [x] **R1-Bullet 15:** Low ratings for commercial systems -> Covered by `R1-015`
- [x] **R2-Weakness I.1:** Fake citation Jain et al. (Kumar et al.) -> Covered by `R2-001`
- [x] **R2-Weakness I.2:** Fake citation Wang H. 2023b -> Covered by `R2-002`
- [x] **R2-Weakness I.3:** Corrupted citation PashtoTTS-bench Anonymous -> Covered by `R2-003`
- [x] **R2-Weakness II:** Outdated objective evaluation; VoiceMOS challenge -> Covered by `R2-004`, `R1-006`
- [x] **R2-Weakness III.1:** Confusing use of term "metrics" -> Covered by `R2-005`
- [x] **R2-Weakness III.2:** Construct of "naturalness" & Urdu translation; SSW papers -> Covered by `R2-006`
- [x] **R2-Weakness III.3:** Kominek & Black (2008) false attribution for cents & F0 -> Covered by `R2-007`
- [x] **R2-Conclusion:** Avoid declaring a "clear winner" when metrics diverge -> Covered by `R2-008`
- [x] **Audit Findings:** FLEURS duplicate data -> Covered by `AUD-001`
- [x] **Audit Findings:** Table 7 bolding error -> Covered by `AUD-002`
- [x] **Audit Findings:** Table 10/12 unweighted mean flaw -> Covered by `AUD-003`
- [x] **Audit Findings:** Missing F0 rows concealed -> Covered by `AUD-004`
- [x] **Audit Findings:** Reporting raw F0 column -> Covered by `AUD-005`
- [x] **Audit Findings:** 22.05 kHz text vs 16 kHz code mismatch -> Covered by `AUD-006`
- [x] **Audit Findings:** Broken ABX prose -> Covered by `AUD-007`
- [x] **Audit Findings:** ABX listener & system count inconsistencies -> Covered by `AUD-008`
- [x] **Audit Findings:** Non-deterministic generation -> Covered by `AUD-009`
- [x] **Audit Findings:** Corpus confounding -> Covered by `AUD-010`
- [x] **Audit Findings:** Lahore residence demographic fallacy -> Covered by `AUD-011`
- [x] **Audit Findings:** Generative AI disclosure integrity -> Covered by `AUD-012`
- [x] **Audit Findings:** Missing repo assets -> Covered by `AUD-013`
- [x] **Audit Findings:** Uncited bib entry pulled by nocite -> Covered by `AUD-014`
- [x] **Audit Findings:** Corrupted metadata in Chiang, Naseem, Arshad, Pratap -> Covered by `AUD-015`, `AUD-016`

