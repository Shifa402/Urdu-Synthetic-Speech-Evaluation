# 08: Objective Evaluation Plan

## Executive Overview

Both reviewers criticized the manuscript's objective evaluation framework for relying exclusively on outdated signal-matching metrics (MCD, F0 RMSE) and out-of-domain neural embeddings (Resemblyzer), while omitting standard modern evaluators:
- **Reviewer #1:** *"MCD and F0 RMSE are not reliable measures of quality... What about using automatic MOS ratings? And what about WER? Both measures are common in today's literature."*
- **Reviewer #2:** *"Objective evaluation: better architectures already exist... The authors are encouraged to follow the work of Cooper et al., particularly originating in the VoiceMOS challenge."*

This document defines a modernized, psychometrically grounded objective evaluation architecture for Urdu TTS synthesis. It integrates:
1. **Intelligibility & Pronunciation Fidelity:** Normalized Word Error Rate (WER) and Character Error Rate (CER) via dual ASR engines, benchmarked against natural human speech.
2. **Learned Quality Predictors:** Automated Speech Quality / MOS estimation following the VoiceMOS Challenge framework (`cooper2024voicemos`), with rigorous cross-lingual calibration.
3. **Diagnostic Acoustic Measures:** Reframed, standardized 16 kHz MCD and pitch contour diagnostics with transparent failure reporting.

---

## 1. Intelligibility Evaluation: Urdu ASR-Based WER & CER

### A. Dual Recognizer Architecture
To avoid recognizer-specific bias (where a single ASR model favors speech that matches its pre-training tokenizer), intelligibility is assessed across two diverse speech recognition architectures:
1. **Model A (Transformer Encoder-Decoder):** `openai/whisper-large-v3` conditioned on `<|ur|>` (Urdu) language token and `<|transcribe|>` task token.
2. **Model B (Massively Multilingual Connectionist Temporal Classification):** `facebook/mms-1b-all` (fine-tuned on Urdu script: `facebook/mms-asr-urd-script_arabic`).

```
+--------------------------------------------------------------------------------------------------+
|                                  URDU ASR EVALUATION PIPELINE                                    |
+---------------------+    +-------------------------+    +----------------------------------------+
| Synthetic Audio     | -> | Dual ASR Models         | -> | Standardized Urdu Text Normalizer      |
| & Human Reference   |    | (Whisper v3 & MMS-1B)   |    | (Diacritic strip, unicode unify, etc.) |
+---------------------+    +-------------------------+    +----------------------------------------+
                                                                             |
                                                                             v
                                                                  +---------------------+
                                                                  | WER & CER Evaluation|
                                                                  | against Ground Truth|
                                                                  +---------------------+
```

### B. Standardized Urdu Text Normalization Protocol
Raw ASR hypotheses in Urdu can deviate from reference transcripts due to non-phonetic orthographic variations (e.g. Unicode representation of Yeh variants, diacritics, or zero-width spaces). Evaluating unnormalized text inflates WER and misrepresents intelligibility.

**Pre-Evaluation Normalization Rules (Frozen a priori):**
1. **Unicode Canonical Decomposition & Composition (NFC):** Normalize all Urdu characters to standard NFC.
2. **Yeh Unification:** Unify all Arabic/Urdu Yeh variants (`\u064A` Arabic Yeh, `\u0649` Alif Maqsurah, `\u06D2` Urdu Bari Yeh, `\u06CC` Farsi Yeh) according to standard contextual word-final orthography.
3. **Kaf / Gaf Unification:** Map Arabic Keheh (`\u0643`) to Urdu Kaf (`\u06A9`).
4. **Diacritic Stripping:** Strip all short vowels and pronunciation diacritics (*A'raab*: Zabar `\u064E`, Zer `\u0650`, Pesh `\u064F`, Do Zabar `\u064B`, Tashdeed `\u0651`, Jazm/Sukun `\u0652`, Khari Zabar `\u0670`).
5. **Punctuation & Whitespace:** Remove all Urdu and Latin punctuation marks (Urdu full stop Khatma `\u06D4`, question mark `\u061F`, comma `\u060C`, quotation marks); collapse multiple whitespace characters and strip zero-width joiners (`\u200C`, `\u200D`).

### C. Natural Human Speech Baselines
**Mandatory Methodological Requirement:** The identical normalization and ASR pipeline must be run on the natural human reference recordings to compute $WER_{\text{ref}}$ and $CER_{\text{ref}}$.
- Synthetic error rates must be reported as both absolute figures ($WER_{\text{syn}}$) and relative degradation figures:
  $$\Delta WER = WER_{\text{syn}} - WER_{\text{ref}}$$
- If human speech achieves a 14% WER on the emotional corpus due to actor shouting and background resonance, an 18% WER on synthetic speech reflects a modest +4% degradation, rather than an 18% synthesis failure.

### D. Native-Speaker Phonetic Spot-Checks
A random 10% sample of high-error sentences ($WER > 30\%$) must be manually inspected by native Urdu linguists to verify whether errors represent:
- *True Synthesis Errors:* Missing phonemes, syllable truncation, stutter, or phonetic hallucinations.
- *ASR Recognition Errors:* Valid Urdu TTS audio misrecognized due to ASR acoustic model limitations.

---

## 2. Automated Quality Predictors (VoiceMOS Challenge Framework)

### A. Context & Limitations of Automated MOS in Multilingual Settings
Modern self-supervised learning (SSL) speech quality estimators (e.g. UTMOS, LDNet, WavLM-MOS) predict human perceptual ratings with high accuracy in English and Japanese (`cooper2024voicemos`). However, **they cannot be assumed valid for Urdu without empirical verification**. 

Acoustic models trained on English listeners often over-penalize Urdu retroflex consonants ($/ʈ/, /ɖ/, /ɽ/$) or aspirated plosives ($/pʰ/, /bʱ/, /t̪ʰ/$) as acoustic roughness or clipping distortion.

### B. Two-Stage Automated Quality Assessment Strategy

#### Stage 1: Zero-Shot SSL Estimator Screening
- Run pre-trained open-source quality models:
  - **UTMOS** (Wav2Vec2-based mean opinion score estimator).
  - **NISQA v2.0** (Speech quality and naturalness predictor for communication channels).
- Record raw predictions across all 960 audio samples.

#### Stage 2: Cross-Lingual Validation Against Held-Out Urdu Human Ratings
- Compute Pearson correlation coefficient ($r$), Spearman rank correlation ($\rho$), and Root Mean Square Error (RMSE) between automated predictions and our empirical subjective listening ratings:
  $$r = \frac{\sum (y_i - \bar{y})(\hat{y}_i - \bar{\hat{y}})}{\sqrt{\sum (y_i - \bar{y})^2 \sum (\hat{y}_i - \bar{\hat{y}})^2}}$$
- **Leakage Prevention:** To avoid overfitting, validation must be performed across held-out listeners and items (10-fold cross-validation or leave-one-domain-out validation).
- **Reporting Rule:** Automated MOS predictions are reported alongside their empirical prediction error and confidence intervals. If a model exhibits low correlation with Urdu raters ($\rho < 0.60$), it is documented as a failure of cross-lingual generalization, providing a valuable scientific contribution to the community.

---

## 3. Standardized Diagnostic Acoustic Measures (MCD & F0)

To resolve Reviewer #1's remarks on upsampling and DTW validity, and Reviewer #2's critique on Kominek & Black, the acoustic measurement pipeline is strictly standardized:

### A. Unified 16 kHz Bandwidth (Eliminating Upsampling Artifacts)
- **Problem in Old Paper:** Text claimed audio was upsampled to 22.05 kHz, which introduces an empty 8–11 kHz Nyquist band for 16 kHz models like MMS (`R1-009`).
- **Standardized Repair:** All audio signals (reference and synthetic) are standardized to **16 kHz mono, 16-bit PCM** using band-limited Kaiser-windowed sinc interpolation (`torchaudio.transforms.Resample`).
- No high-frequency zero-padding or artificial spectral expansion is performed.

### B. Mel-Cepstral Distortion (MCD) Specification
- **Feature Extraction:** 13th-order mel-cepstral coefficients ($C_0$–$C_{12}$) extracted from WORLD spectral envelope with warping coefficient $\alpha = 0.58$ (standard for 16 kHz speech, replacing $\alpha = 0.65$ which was used for 22.05 kHz).
- **DTW Alignment:** FastDTW computed strictly on $C_1$–$C_{12}$ (excluding energy coefficient $C_0$ to prevent volume bias).
- **Metric Formulation:**
  $$\text{MCD} = \frac{10\sqrt{2}}{\ln 10} \frac{1}{T} \sum_{t=1}^{T} \sqrt{\sum_{k=1}^{12} (c_{k,t}^{\text{ref}} - c_{k,t}^{\text{syn}})^2}$$
- **Interpretation Boundary:** Explicitly framed as *spectral envelope divergence from an unaligned reference recording*, confounded by speaker vocal tract morphology.

### C. Fundamental Frequency (F0) Contour Diagnostics
- **F0 Extraction:** PyWorld `harvest` algorithm with `stonemask` refinement (F0 range: 50–500 Hz for male voices).
- **Disentangling Register from Trajectory:**
  - **Metric 1: Standard F0 RMSE (Register-Adjusted):** Mean F0 offset between speakers subtracted prior to RMSE calculation:
    $$\text{F0 RMSE}_{\text{adj}} = \sqrt{ \frac{1}{N} \sum_{i=1}^{N} \left( 1200 \log_2 \frac{F0_i^{\text{syn}}}{F0_i^{\text{ref}}} - \overline{\Delta \text{cents}} \right)^2 }$$
  - **Metric 2: Mean Pitch Register Offset ($\overline{\Delta \text{cents}}$):** Measures whether the TTS voice has an inherently higher or lower baseline pitch than the reference speaker.
  - **Metric 3: Voicing Error Rates:** Gross Pitch Error (GPE, $>20\%$ deviation) and Voicing Decision Error (VDE, unvoiced-to-voiced misalignments).

### D. Transparent Failure Reporting
- Any audio pair where DTW finds zero mutually voiced frames ($N_{\text{voiced}} = 0$) must be explicitly flagged in results tables with the exact failure count and reason, eliminating deceptive claims of "100% complete coverage without failure."

