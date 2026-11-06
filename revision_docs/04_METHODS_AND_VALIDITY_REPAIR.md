# 04: Methods and Validity Repair

## Methodological Diagnosis

The editorial and reviewer rejection letters identified core validity threats:
1. **Construct Conflation:** Signal-level distance metrics (MCD, F0 RMSE) and speaker embedding similarity (Resemblyzer) were presented as direct measures of "synthesis quality" or "identity preservation," despite being computed against different human speakers.
2. **Severe Corpus Confounding:** Domains (Formal, Conversational, Literary, Emotional) were drawn from disparate corpora with different speakers, recording setups, and text lengths, making causal attributions of domain difficulty scientifically invalid.
3. **Protocol Misrepresentation:** A discrete 1–5 rating questionnaire on Google Forms with unrated anchors and references was termed a "MUSHRA" test, and a broken stimulus design was reported for ABX.
4. **False Synthesis Generalization:** Presets with static descriptions were evaluated across domains without style conditioning, while results were framed as testing the systems' intrinsic domain-handling abilities.

---

## 1. Formal Disentanglement of Synthesis Tasks

To restore scientific validity, the revised study explicitly distinguishes three fundamentally distinct synthesis tasks that were previously conflated:

```
+--------------------------------------------------------------------------------------------------+
|                                    SYNTHESIS PARADIGMS                                           |
+------------------------------------+------------------------------------+------------------------+
| Task A: Default Text-to-Speech     | Task B: Style-Conditioned TTS      | Task C: Voice Cloning  |
| (Evaluated in Manuscript)          | (Planned Experimental Extension)   | (Explicitly Separated) |
+------------------------------------+------------------------------------+------------------------+
| - Fixed native voice presets       | - Dynamic natural language prompts | - Few-shot / zero-shot |
|   (AsadNeural, Charon, MMS,        |   in Parler-TTS (e.g. "whispering, |   cloning conditioned  |
|   Rohit-neutral).                  |   excited, formal newsreader").    |   on reference audio.  |
| - Text-only genre variation across | - Expressive SSML rate/pitch tags  | - Objective: replicate |
|   four domains.                    |   in Edge/Gemini.                  |   target identity.     |
| - Objective: measure baseline      | - Objective: measure stylistic     | - Requires speaker     |
|   genre robustness.                |   responsiveness to conditioning.  |   similarity metrics.  |
+------------------------------------+------------------------------------+------------------------+
```

### Critical Consequence for Current Manuscript:
The existing experimental results represent **Task A exclusively**. Systems were never instructed or conditioned to match the reference speaker's identity or speaking style. Consequently:
- **Resemblyzer similarity is NOT a speaker preservation score.** It is merely a metric of acoustic distance between a TTS preset voice and a human speaker.
- **MCD and F0 RMSE are NOT quality scores.** They reflect vocal tract differences, fundamental frequency register offsets, and channel variations between two distinct voices.

---

## 2. Reframing Research Questions and Defensible Claims

### Original (Flawed) Formulation:
- *Original RQ:* Which Urdu TTS system achieves superior quality and human indistinguishability across four domains, and how does domain difficulty rank?
- *Defect:* Assumes a single winner exists; claims "emotional speech is inherently the most difficult"; treats metric divergence as model optimization tradeoffs.

### Revised (Defensible) Formulation:

> **Primary RQ1 (Text-Domain Robustness):**  
> How robust are contemporary Urdu TTS systems to linguistic and lexical variation across distinct text genres (Formal, Conversational, Literary, and Emotional) when operating under standard neutral default voice configurations?

> **Primary RQ2 (Metric and Construct Divergence):**  
> How do signal-level reference-distance measures (MCD, F0 RMSE), acoustic embedding distances, and subjective human listening ratings diverge, and what are the specific construct boundaries of each evaluation method in low-resource TTS assessment?

> **Secondary RQ3 (Style Conditioning Potential - Planned Extension):**  
> To what extent does natural-language prompt conditioning (e.g., in Indic-Parler-TTS) or acoustic style tagging improve perceived domain appropriateness compared to default neutral presets?

---

## 3. Comprehensive Threat-to-Validity Matrix

| Validity Dimension | Specific Flaw Identified | Source of Confound | Scientific Impact | Corrective Repair Session Action |
|---|---|---|---|---|
| **Construct Validity** | Resemblyzer used for "speaker similarity" | Pretrained on English VoxCeleb; TTS systems not tasked with voice cloning | Measures arbitrary vocal timbre distance between two distinct male voices | Reframe as descriptive acoustic feature distance; eliminate "voice cloning" and "speaker preservation" claims. |
| **Construct Validity** | MCD & F0 RMSE framed as "synthesis quality" | Compared against different speakers; DTW distorts across non-identical prosodic phrasing | Conflates speaker anatomy, pitch register, and recording acoustics with synthesis errors | Retitle metrics as "Reference-Relative Spectral & Prosodic Divergence"; add explicit vocal tract caveat. |
| **Internal Validity** | Domain manipulation confounded with corpus properties | Conv/Lit from Humair Awan; Formal from FLEURS + Wikipedia; Emotional from Mendeley actors | Domain differences are entangled with SNR, microphone, room acoustics, and sentence length | Demote causal domain difficulty claims; frame domain differences as corpus-entangled observations. |
| **Internal Validity** | Exact duplicate data on FLEURS for Indic and MMS | Artifact in `f0_mcd_per_file_scores.csv` (all 30 rows identical) | Corrupts comparative validity between Indic-Parler and MMS on Formal speech | Isolate and disclose duplicate rows in audit report; flag for rerun with regenerated audio. |
| **Statistical Validity** | Unweighted row averaging in Tables 10 & 12 | Formal split into 2 rows of 30 samples, each weighted equally to 60-sample domains | Formal speech received 40% effective weight instead of 25% | Disclose exact table aggregation formula; report recalculated sample-weighted pooled means. |
| **Statistical Validity** | Concealed missing F0 values | 2 rows had NaN F0 RMSE due to zero voiced DTW frames, while `ok=True` was reported | Distorts sample denominator ($n=958$ vs $n=960$) | Report exact valid denominators per system ($n=240$ vs $n=239$). |
| **Construct Validity** | "MUSHRA" label applied to discrete 1–5 test | Unrated reference and anchor; discrete 5-point scale; no instant A/B switching | Defeats MUSHRA's continuous sensitivity; functions as a multi-stimulus MOS | Retitle test as "Reference-Anchored Discrete Perceptual Rating"; design true MUSHRA redesign in Doc 07. |
| **Internal Validity** | Uninterpretable ABX description | Text stated A and B were both the reference sample | Matching task is mathematically and perceptual uninterpretable as written | Flag prose error with author TODO; specify standard A=Human, B=TTS, X=Token protocol in Doc 07. |
| **External Validity** | Male-only speech restriction | Only male reference audio and male voice presets evaluated | Findings do not generalize to female speech, high-register voices, or children | Formally document male-only limitation in Methodology and Discussion. |
| **External Validity** | Demographic assumption on Lahore residence | Assumed native Urdu competence without language screening | Lahore has large native Punjabi-speaking demographics | Remove false claim; mandate standardized language screening for future tests. |

---

## 4. Measurement Disposition: Remove, Demote, Recompute, or Recollect

### A. Measurements to REMOVE
1. **"Perceptual Indistinguishability / Parity" Claims:** The claim that Edge and Gemini approach human indistinguishability based on the reported ABX test must be removed. The ABX description is broken, tested only 2 domains, and near-chance performance was not statistically demonstrated.
2. **"Universal Domain Difficulty Hierarchy":** The claim that "emotional speech is inherently the most challenging domain for TTS architectures" must be removed as a universal claim. In this study, emotional text was synthesized using a static *neutral* voice description ("Rohit") and compared against exaggerated actor recordings from a separate corpus.
3. **5-Cent Universal JND Claim:** The assertion that 5 cents is a perceptual threshold in running speech must be removed.
4. **Resemblyzer "Speaker Identity Preservation" Classification:** Removed from Table 2 and Section 5.2.

### B. Measurements to DEMOTE
1. **Mel-Cepstral Distortion (MCD):** Demoted from a "primary objective speech quality metric" to an "exploratory acoustic spectral envelope divergence measure relative to an unaligned external reference speaker."
2. **Fundamental Frequency RMSE (F0 RMSE):** Demoted to a "prosodic pitch-contour register and trajectory difference measure."
3. **Resemblyzer Embedding Cosine Similarity:** Demoted to a "high-level acoustic representation distance metric via an out-of-domain neural encoder."

### C. Measurements to RECOMPUTE / RECONCILE
1. **Speaker Similarity Bolding (Table 7):** Recomputed and bolding transferred from Indic-Parler (0.6312) to Edge TTS (0.6329).
2. **System Overall Means (Tables 10 & 12):** Supplement unweighted table row means with pooled sample-weighted means.
3. **Valid F0 Sample Counts:** Correct valid sample count from 960 to 958 ($n=239$ for Gemini and Indic-Parler).
4. **F0 Column Attribution:** Explicitly document that reported Table 11 & 12 values reflect `f0_rmse_cents_raw`.

### D. Measurements to RECOLLECT (Specification for Future Experiments)
1. **Normalized Urdu Word Error Rate (WER) and Character Error Rate (CER):** Using dual ASR models (Whisper-large-v3 and MMS-ASR-Urdu) with a documented Urdu text normalizer.
2. **True ITU-R BS.1534 MUSHRA Listening Test:** Using an interactive web interface (webMUSHRA), continuous 0–100 sliders, rated hidden reference, rated anchor, and post-screening.
3. **VoiceMOS SSL Quality Estimator Scores:** Using wav2vec 2.0 / MMS representations calibrated on held-out Urdu human ratings.

