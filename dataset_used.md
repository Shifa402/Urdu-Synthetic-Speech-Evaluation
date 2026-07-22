# Dataset Description and Evaluation Protocol

## Overview

This study employs a carefully curated multi-domain corpus of Urdu speech recordings to evaluate the naturalness and expressiveness of four Text-to-Speech (TTS) systems. To ensure consistency across evaluations, all reference and generated audio samples utilize **male voice** recordings exclusively. The evaluation framework is structured around four objective and subjective measures, with sample sizes determined by the nature of each metric.

---

## Evaluation Sample Distribution

The evaluation protocol distinguishes between two categories of metrics based on the mode of assessment:

- **Embedding-based Scores** (automated, signal-level): **60 samples per domain** are used to ensure statistical robustness in feature-space comparisons.
- **Perceptual Listening Tests** (human judgment-based): **6 samples per domain** are used across the remaining three evaluation measures, balancing annotation burden with sufficient coverage for reliable inference.

---

## Speech Domains and Corresponding Datasets

The corpus spans four linguistically and pragmatically distinct domains, each sourced from dedicated datasets to maximize ecological validity and domain specificity.

---

### 1. Conversational Domain

**Dataset:** `Humairawan/UrduSpeech`
**Source:** [https://huggingface.co/datasets/humairawan/UrduSpeech](https://huggingface.co/datasets/humairawan/UrduSpeech)

Samples for this domain are drawn from the `Humairawan/UrduSpeech` dataset hosted on Hugging Face. Since the dataset contains recordings in multiple languages including Kashmiri, the corpus is filtered to retain only Urdu-language utterances (`language = 'Urdu'`). Conversational samples are further isolated by applying a style filter (`style = 'CONV'`), and only male-speaker recordings are retained (`gender = 'Male'`) to maintain cross-domain speaker consistency.

---

### 2. Emotional Domain

**Dataset:** Mendeley Data — Urdu Emotional Speech Corpus (Version 4)
**Source:** [https://data.mendeley.com/datasets/jcpfjnk5c2/4](https://data.mendeley.com/datasets/jcpfjnk5c2/4)

Ten samples per emotion category are selected from this corpus, covering a range of affective states representative of expressive speech synthesis challenges. The **Neutral** category is deliberately excluded from evaluation, as it overlaps semantically with the Formal and Conversational Speech domain already included in this study. The following emotion categories are used:
1. Angry     
2. Boredom  
3. Disgust
4. Fear
5. Happy
6. Sad

---

### 3. Literary / Storytelling Domain

**Dataset:** `Humairawan/UrduSpeech`
**Source:** [https://huggingface.co/datasets/humairawan/UrduSpeech](https://huggingface.co/datasets/humairawan/UrduSpeech)

Literary and narrative speech samples are drawn from the same `Humairawan/UrduSpeech` dataset, filtered for Urdu-language utterances (`language = 'Urdu'`), literary/book-style content (`style = 'BOOK'`), and male speakers (`gender = 'Male'`). This domain captures the prosodic richness and stylistic variation characteristic of oral storytelling and literary recitation in Urdu.

---

### 4. Formal / Read Speech Domain

**Datasets:**

- **Google FLEURS**
  **Source:** [https://huggingface.co/datasets/google/fleurs](https://huggingface.co/datasets/google/fleurs)
  Male-speaker audio samples are filtered from the Urdu subset of the FLEURS dataset, which consists of read-aloud, standardized speech prompts.

- **`Humairawan/UrduSpeech`**
  **Source:** [https://huggingface.co/datasets/humairawan/UrduSpeech](https://huggingface.co/datasets/humairawan/UrduSpeech)
  Additionally, encyclopedic/formal samples are sourced from `Humairawan/UrduSpeech` by filtering for Urdu language (`language = 'Urdu'`), Wikipedia-style read speech (`style = 'WIKI'`), and male speakers (`gender = 'Male'`).

The combination of these two sources ensures broad coverage of formal, read-style Urdu speech across different recording conditions and prompt styles.

---

## Summary Table

| Domain              | Dataset(s)                             | Style Filter | Gender | Embedding Eval (n) | Listening Eval (n) |
|---------------------|----------------------------------------|--------------|--------|--------------------|--------------------|
| Conversational      | Humairawan/UrduSpeech                  | `CONV`       | Male   | 60                 | 30                 |
| Emotional           | Mendeley Urdu Emotional Speech (v4)    | Per emotion  | Male   | 60                 | 30                 |
| Literary/Storytelling | Humairawan/UrduSpeech               | `BOOK`       | Male   | 60                 | 30                 |
| Formal/Read Speech  | Google FLEURS + Humairawan/UrduSpeech  | `WIKI`       | Male   | 60                 | 30                 |
