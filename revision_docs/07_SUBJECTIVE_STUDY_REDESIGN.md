# 07: Subjective Study Redesign

## Forensic Audit of Historical Protocol vs. Standardized Redesign

The Handling Editor and both reviewers severely criticized the manuscript's subjective evaluation:
- **Reviewer #1:** The 5-point discrete scale defeated the purpose of MUSHRA and collapsed the protocol to MOS; Google Forms introduced friction and rater variance; the pipeline description implied 960 pairs were rated when only 24 items were evaluated.
- **Reviewer #2:** The construct of "naturalness" is ambiguous in multilingual contexts; the manuscript failed to provide the Urdu translation and instructions shown to participants.
- **Audit Findings (`AUD-007`, `AUD-008`, `AUD-011`):** The ABX test description was broken ("A and B are the same reference"); participant screening relied on the sociolinguistically flawed assumption that Lahore residents are automatically native Urdu speakers; no formal institutional ethics approval was established.

This document specifies a scientifically defensible, prospective listening study protocol that completely replaces the rejected design.

---

## 1. What the Historical Study Actually Did (Forensic Audit)

| Design Dimension | Historical Implementation (Submitted Paper) | Standard ITU-R BS.1534 / ITU-T P.800 Compliance | Scientific Defect |
|---|---|---|---|
| **Platform** | Google Forms | Dedicated interactive interface (e.g. webMUSHRA, beaqleJS) | Lack of simultaneous switching; uncontrolled playback volume; listener fatigue. |
| **Rating Scale** | Discrete 1–5 integer radio buttons | Continuous 0–100 interval slider (MUSHRA) or 1–5 ACR scale | Defeats MUSHRA's fine-grained differential sensitivity; artificially compresses ratings. |
| **Reference Stimulus** | Presented as an explicit orientation clip; **NOT rated** | **Hidden Reference** included among test stimuli and rated blindly | Inability to perform listener post-screening based on hidden reference identification ($<90$ exclusion). |
| **Anchor Stimulus** | Presented for orientation; **NOT rated** | **Hidden Low Anchor** (3.5 kHz low-pass filtered audio) rated blindly | Inability to anchor the bottom of the scale or test listener diligence. |
| **Evaluated Items** | 6 source utterances per domain (24 items total across 4 domains) | Recommended 12–20 items per domain | Severely underpowered item sampling; manuscript text erroneously implied 960 pairs were rated. |
| **Listener Cohort** | 20 listeners; split into pairs of domains ($n=10$ per domain) | Recommended 20–30 listeners evaluating all conditions in randomized blocks | Underpowered; cell comparisons vulnerable to small individual rater outliers. |
| **ABX Paradigm** | "A=Ref, B=Ref, X=Unknown" (lines 585–589) | Standard forced-choice A=Human, B=TTS, X=Token | Reported description is mathematically uninterpretable; testing was restricted to only 2 domains. |
| **Participant Screening**| Assumed native proficiency based on living in Lahore | Standardized L1 language questionnaire + Headphone screening test | Unscreened listeners; sociolinguistic invalidity. |
| **Ethics & Consent** | Informal recruitment via team social network | Prospective Institutional Review Board (IRB) / Ethics clearance | Absence of documented institutional oversight. |

---

## 2. Definitive Protocol Redesign: Dual Pathway

The authors may choose between two standardized subjective designs for the new experimental campaign:

### Pathway A: True Web-Based MUSHRA (ITU-R BS.1534-3 Compliant)
- **Harness:** Open-source `webMUSHRA` framework running in modern web browsers (no participant installation required).
- **Interface:** Instantaneous, gapless switching between Reference, Hidden Reference, Hidden 3.5 kHz Anchor, and the four TTS systems (Edge, Gemini, Indic-Parler, MMS).
- **Scale:** Continuous 0–100 slider with standardized ITU interval anchors: *Bad (0–20)*, *Poor (20–40)*, *Fair (40–60)*, *Good (60–80)*, *Excellent (80–100)*.
- **Post-Screening Gate:** Any listener who rates the hidden reference $<90$ on more than 15% of trials, or rates the low anchor $>30$, is automatically disqualified and excluded prior to unblinding.

### Pathway B: Multi-Attribute Comparison Mean Opinion Score (CMOS / DCR)
- If webMUSHRA cannot be hosted, implement a standardized Degradation Category Rating (DCR, ITU-T P.800) test.
- Raters listen to Reference (A) followed by System (B) and rate quality on a balanced 1–5 scale.
- **CRITICAL RULE:** Do NOT call this test "MUSHRA". Label it truthfully as a *Reference-Anchored Multi-Attribute Subjective Rating Test*.

---

## 3. Perceptual Constructs and Standardized Urdu Instructions

To resolve Reviewer #2's critique regarding construct validity in multilingual contexts (citing Shirali-Shahreza & Penn 2023; Pandey et al. 2025), the evaluation deconstructs "overall quality" into three explicit, psychometrically validated dimensions with verified Urdu phrasing:

```
+----------------------------------------------------------------------------------------------------+
|                                    PERCEPTUAL CONSTRUCTS                                           |
+------------------------------+------------------------------+--------------------------------------+
| 1. Naturalness               | 2. Intelligibility / Clarity | 3. Domain Appropriateness            |
|    (قُدرتی پن اور روانی)      |    (وضاحت اور فہم)           |    (موزونیت اور لب و لہجہ)           |
+------------------------------+------------------------------+--------------------------------------+
| "Does the speech flow with   | "Can you clearly understand  | "Does the vocal delivery match the   |
| natural human prosody,       | every single word without    | specific context (news reading,      |
| rhythm, and pause patterns,  | effort, free of slur, buzz,  | casual chat, expressive storytelling,|
| or does it sound robotic?"   | or muffled acoustic noise?"  | or dramatic emotional dialogue)?"    |
+------------------------------+------------------------------+--------------------------------------+
```

### Exact Urdu Verbatim Instructions for Participants:

#### 1. عام ہدایات (General Instructions)
> "اس تحقیقی مطالعے میں آپ کو اردو زبان کے مختلف آڈیو نمونے سنوائے جائیں گے۔ کچھ نمونے اصل انسانی آواز پر مشتمل ہیں جبکہ کچھ جدید کمپیوٹر ماڈلز (Text-to-Speech) کے ذریعے تیار کیے گئے ہیں۔ براہ کرم معیاری ہیڈ فونز (Headphones) کا استعمال کریں اور پرسکون ماحول میں سن کر اپنی غیر جانبدارانہ رائے دیں۔"

#### 2. قدرتی پن کی تعریف (Naturalness Dimension - Shirali-Shahreza & Penn, 2023)
> **سوال:** یہ آواز بولنے کے انداز میں کتنی قدرتی معلوم ہوتی ہے؟  
> **رہنمائی:** "اس بات پر توجہ دیں کہ کیا جملے کے اتار چڑھاؤ (Prosody)، لفظوں کا تسلسل اور سانس کا وقفہ ایک عام انسان جیسا ہے، یا پھر یہ مشینی، غیر لچکدار اور مصنوعی لگتی ہے؟"  
> - 1 = انتہائی غیر قدرتی / مشینی (Completely Robotic)  
> - 3 = درمیانہ / جزوی طور پر قدرتی (Moderately Natural)  
> - 5 = مکمل طور پر قدرتی انسانی آواز (Completely Natural Human Voice)

#### 3. وضاحت اور فہم کی تعریف (Clarity / Intelligibility Dimension)
> **سوال:** آواز میں الفاظ کس حد تک صاف اور سمجھنے میں آسان ہیں؟  
> **رہنمائی:** "اس بات پر توجہ دیں کہ کیا تمام الفاظ بغیر کسی الجھن، رکاوٹ، یا صوتی خرابی (Distortion/Muffle) کے واضح سنائی دے رہے ہیں؟"  
> - 1 = ناقابلِ فہم / شدید خرابی (Unintelligible)  
> - 3 = قابلِ فہم لیکن کچھ الفاظ میں ابہام (Understandable with Effort)  
> - 5 = بالکل شفاف اور واضح تلفظ (Crystal Clear Pronunciation)

#### 4. موزونیت کی تعریف (Domain Appropriateness - Pandey et al., 2025)
> **سوال:** کیا بولنے والے کا لب و لہجہ دیے گئے سیاق و سباق (Domain) کے مطابق ہے؟  
> **رہنمائی:**  
> - *رسمی (Formal):* کیا یہ سنجیدہ اور پراعتماد انداز ہے جیسے خبریں یا تعلیمی مواد پڑھا جا رہا ہو؟  
> - *گفتگو (Conversational):* کیا یہ روزمرہ کی بے تکلف اور دوستانہ گفتگو جیسا لگتا ہے؟  
> - *ادبی و داستان گوئی (Literary):* کیا اس میں کہانی سنانے والا تاثر، کشش اور روانی موجود ہے؟  
> - *جذباتی (Emotional):* کیا بولنے والے کی آواز میں مطلوبہ جذبہ (غصہ، خوف، خوشی، اداسی) واضح محسوس ہو رہا ہے؟  
> - 1 = سیاق و سباق کے بالکل برعکس (Completely Inappropriate)  
> - 5 = سیاق و سباق کے لیے مکمل طور پر موزوں (Perfect Fit for Domain)

---

## 4. Participant Screening & Ethical Governance Protocol

### A. Hearing & Audio Screening
1. **Pre-Test Acoustic Check:** All raters must complete an interactive headphone screening test before beginning (e.g. the Woods et al. 2017 antiphasic tone test or Milne et al. 2021 Huggins Pitch test). Raters failing the screening on loudspeakers cannot proceed.
2. **Hearing Self-Report:** Affirmation of no known uncorrected hearing impairment.

### B. Sociolinguistic & Language Screening
1. Explicit verification that **Urdu is the rater's primary mother tongue (L1)** or language of daily home communication.
2. Years of formal education in Urdu / self-reported reading and listening fluency.
3. Residence in Pakistan; eliminating the invalid proxy that residence in Lahore alone guarantees native Urdu status.

### C. Institutional Ethics & Informed Consent
1. Prospective submission of study protocol to the **FAST-NUCES Institutional Review Board (IRB) / Research Ethics Committee**.
2. **Participant Information Sheet & Consent Form:** Informs listeners of audio listening tasks, data anonymization, voluntary withdrawal without penalty, and lack of adverse audio risks (volume normalized to $-23$ LUFS).
3. **NEVER RETROACTIVELY CLAIM ETHICS APPROVAL:** In the manuscript revision, transparently state that the historical pilot had informal institutional oversight, and that the new formal listening campaign was conducted under approved IRB Protocol #XXXX.

---

## 5. Sample Size, Power Analysis, and Balanced Allocation Plan

### Statistical Power & Sample Sizing
- In subjective speech evaluation, ratings are nested within listeners and items. Treating ratings as independent observations inflates Type I error.
- Based on a repeated-measures design targeting a minimum detectable effect size of $\Delta = 0.35$ on a 1–5 scale (or $\Delta = 7.0$ on a 0–100 scale) with power $1 - \beta = 0.85$ at $\alpha = 0.05$:
  - **Source Items per Domain:** 15 items per domain ($15 \times 4 = 60$ source items total).
  - **Systems per Item:** 4 TTS systems + 1 Hidden Reference + 1 Anchor = 6 stimuli per trial.
  - **Listener Panel:** $N = 30$ native Urdu raters.
  - **Design Balance:** Incomplete Latin Square or Balanced Randomized Block Design.
  - **Listener Burden:** Each listener evaluates 30 trials (approx. 25 minutes total, split into two 12-minute sessions with mandatory 3-minute listening break to avoid auditory fatigue).

### Standardized Output Data Schema (`subjective_responses_tidy.csv`)
The new data collection must export raw data in tidy tabular format:
```text
listener_id:       str (e.g. "L001", anonymized)
age_bracket:       str ("18-24", "25-34", etc.)
gender:            str ("M", "F", "Other")
l1_language:       str ("Urdu")
headphone_pass:    bool (True/False)
domain:            str ("Conversational", "Formal", "Literary", "Emotional")
item_id:           str ("conv_sample_012")
system_id:         str ("edgetts", "gemini", "indic_parler", "mmstts", "hidden_ref", "anchor")
presentation_order:int (1 to 6)
block_order:       int (1 to 30)
naturalness_score: float (0.0 to 100.0 or 1.0 to 5.0)
clarity_score:     float (0.0 to 100.0 or 1.0 to 5.0)
appropriateness_score: float (0.0 to 100.0 or 1.0 to 5.0)
playback_count:    int (number of times rater re-played audio)
response_time_ms:  int (time spent on trial page)
```

