# 03: Reference and Claim Audit

## Audit Overview & Verification Protocol

- **Audit Date:** November 6, 2026
- **Total Entries Audited in `cas-refs.bib`:** 28 entries
- **Verification Status Categories:**
  - **VERIFIED CORRECT:** Paper exists, primary metadata is accurate, claim is supported.
  - **CORRECTED METADATA:** Paper exists and claim is valid, but author list, year, venue, or DOI was inaccurate or incomplete in the original `.bib`.
  - **CORRUPTED ATTRIBUTION:** Paper exists, but was attributed to the wrong lead author or listed as anonymous.
  - **FABRICATED / NONEXISTENT:** Paper does not exist in any authoritative index (CrossRef, DBLP, arXiv, Google Scholar, IEEE Xplore, ISCA).
  - **MISAPPLIED CLAIM / INVALID ATTRIBUTION:** Paper exists, but does not support the specific factual claim made in the manuscript.
  - **UNCITED RESIDUAL:** Entry present in bibliography but never cited in prose (pulled exclusively by `\nocite{*}`).

---

## Master Reference Audit Register (All 28 Entries)

| # | BibTeX Key | Existence Status | Metadata Status | Claim Support | Authoritative URL / DOI | Action Taken |
|---|---|---|---|---|---|---|
| 1 | `pratap2023mms` | Verified | Incomplete (listed as inproceedings arXiv) | Supported | [10.5555/3648699.3648796](https://jmlr.org/papers/v25/23-0853.html) | Upgraded to JMLR 2024 publication record. |
| 2 | `lyth2024natural` | Verified | Correct | Supported | [arXiv:2402.01912](https://arxiv.org/abs/2402.01912) | Retained. |
| 3 | `lacombe2024parlertts` | Verified | Correct (GitHub repository) | Supported | `https://github.com/huggingface/parler-tts` | Retained; added release commit/tag. |
| 4 | `kim2021vits` | Verified | Correct (ICML 2021) | Supported | `https://proceedings.mlr.press/v139/kim21f.html` | Retained. |
| 5 | `itu2015mushra` | Verified | Correct (ITU-R Recommendation) | Misrepresented in text | [ITU-R BS.1534-3](https://www.itu.int/rec/R-REC-BS.1534-3-201510-I/en) | Retained recommendation; corrected text to admit study deviated from MUSHRA. |
| 6 | `kirkland2023mos` | Verified | Correct (Proc. SSW 2023) | Supported | [10.21437/SSW.2023-14](https://doi.org/10.21437/SSW.2023-14) | Retained; added full pages and DOI. |
| 7 | `lemaguer2024limits` | Verified | Incomplete (missing article number & DOI) | Supported | [10.1016/j.csl.2023.101577](https://doi.org/10.1016/j.csl.2023.101577) | Corrected metadata (Volume 84, Article 101577; full authors Le Maguer, King, Harte). |
| 8 | `wang2023gzstvZS` | **NONEXISTENT** | **FABRICATED** | **UNSUPPORTED** | None (Unindexed) | **DELETED FROM BIBLIOGRAPHY AND TEXT.** |
| 9 | `wan2018ge2e` | Verified | Correct (Proc. ICASSP 2018) | Qualified support | [10.1109/ICASSP.2018.8462665](https://doi.org/10.1109/ICASSP.2018.8462665) | Retained; added caveat that GE2E was English-trained. |
| 10 | `conneau2022fleurs` | Verified | Correct (IEEE SLT 2022) | **Uncited in text** | [10.1109/SLT54897.2023.10022378](https://doi.org/10.1109/SLT54897.2023.10022378) | Added explicit in-text citation in Section 4.1; removed `\nocite{*}`. |
| 11 | `naseem2025urdu` | Verified (Real paper) | **CORRUPTED AUTHORS & YEAR** | Supported | [10.21437/Interspeech.2024-114](https://doi.org/10.21437/Interspeech.2024-114) | Corrected to Fatima Naseem et al., Interspeech 2024. |
| 12 | `arshad2022transfer` | Verified (Real paper) | **CORRUPTED LEAD AUTHOR** | Supported | [ACL Anthology: 2022.eurali-1.3](https://aclanthology.org/2022.eurali-1.3/) | Corrected to Sahar Jamal, Sadaf Abdul Rauf, Quratulain Majid (LREC EurALI 2022). |
| 13 | `jain2023indicTTS` | Verified (Real paper) | **CORRUPTED LEAD AUTHOR** | Supported | [10.1109/ICASSP49357.2023.10095819](https://doi.org/10.1109/ICASSP49357.2023.10095819) | Replaced with Gokul Karthik Kumar et al., ICASSP 2023 (`kumar2023indic`). |
| 14 | `chung2022flan` | Verified | Incomplete (arXiv preprint) | Contextual | [arXiv:2210.11416](https://arxiv.org/abs/2210.11416) | Retained. |
| 15 | `bailly2025hot` | Verified | Incomplete (listed as arXiv) | Supported | [10.21437/SSW.2025-34](https://doi.org/10.21437/SSW.2025-34) | Updated to SSW 2025 Proceedings record. |
| 16 | `chiang2024mushra` | Verified (Real paper) | **CORRUPTED AUTHORS** | Supported | [arXiv:2411.12719](https://arxiv.org/abs/2411.12719) | Corrected to Praveen Srinivasa Varadhan et al. (`varadhan2024mushra`). |
| 17 | `kubichek1993mcd` | Verified | Type mismatch (`@article` with `booktitle`) | Supported | [10.1109/PACRIM.1993.407206](https://doi.org/10.1109/PACRIM.1993.407206) | Fixed entry type to `@inproceedings`, PACRIM 1993. |
| 18 | `kominek2008mcd` | Verified | Correct metadata (SLTU 2008) | **MISAPPLIED CLAIM** | [ISCA SLTU 2008](https://www.isca-speech.org/archive_open/sltu_2008/papers/sltu_078.pdf) | Removed from all F0 RMSE / cents claims. Retained strictly for MCD. |
| 19 | `pashto2025bench` | Verified (Real paper) | **CORRUPTED AUTHOR & YEAR** | Supported | [arXiv:2605.26978](https://arxiv.org/abs/2605.26978) | Corrected to Hanif Rahman (May 2026) (`rahman2026pashto`). |
| 20 | `chiang2024mushraevaluate` | Verified | **INCORRECT AUTHORS & OMISSION** | Supported | [10.21437/Interspeech.2024-1354](https://doi.org/10.21437/Interspeech.2024-1354) | Corrected authors to Cheng-Han Chiang, Wei-Ping Huang, and Hung-yi Lee. |
| 21 | `schatz2013abx` | Verified | Correct (Interspeech 2013) | Supported | [10.21437/Interspeech.2013-564](https://doi.org/10.21437/Interspeech.2013-564) | Retained. |
| 22 | `wang2023gzstv` | Verified | Correct (VALL-E, ICML 2023) | Supported | `https://proceedings.mlr.press/v202/wang23ad.html` | Retained (Wang et al., ICML 2023). |
| 23 | `ai4bharat2024indic` | Verified | Model card URL | Supported | `https://huggingface.co/ai4bharat/indic-parler-tts` | Retained; pinned version/date. |
| 24 | `microsoft2023azure` | Verified | Online documentation | Supported | `https://learn.microsoft.com/en-us/azure/ai-services/speech-service/text-to-speech` | Retained. |
| 25 | `google2025gemini` | Verified | Technical report | Supported | `https://deepmind.google/technologies/gemini/` | Retained. |
| 26 | `tan2021neuraltts` | Verified | Incomplete (arXiv preprint) | Supported | [arXiv:2106.15561](https://arxiv.org/abs/2106.15561) | Retained. |
| 27 | `kong2020hifigan` | Verified | Correct (NeurIPS 2020) | Supported | `https://proceedings.neurips.cc/paper/2020/hash/c5d736809766d46260d816d8dbc9eb44-Abstract.html` | Retained. |
| 28 | `wang2017tacotron` | Verified | Correct (Interspeech 2017) | Supported | [10.21437/Interspeech.2017-1452](https://doi.org/10.21437/Interspeech.2017-1452) | Retained. |

---

## Mandatory Recommended Additions from Peer Reviews

To directly address the editorial and reviewer critiques regarding modern evaluation frameworks and construct validity, the following verified publications are integrated into the revised bibliography:

| BibTeX Key | Authors | Title | Venue | DOI / URL | Role in Revision |
|---|---|---|---|---|---|
| `shirali2023better` | Sajad Shirali-Shahreza, Gerald Penn | *Better Replacement for TTS Naturalness Evaluation* | 12th ISCA Speech Synthesis Workshop (SSW 2023), pp. 197–203 | [10.21437/SSW.2023-31](https://doi.org/10.21437/SSW.2023-31) | Recommended by Rev 2. Deconstructs vague "naturalness" into granular perceptual constructs. |
| `pandey2025what` | Ayushi Pandey, Sébastien Le Maguer, Naomi Harte | *What is Naturalness?* | 13th ISCA Speech Synthesis Workshop (SSW 2025), pp. 215–221 | [10.21437/SSW.2025-33](https://doi.org/10.21437/SSW.2025-33) | Recommended by Rev 2. Delineates human-likeness from situational appropriateness. |
| `cooper2024voicemos` | Erica Cooper, Wen-Chin Huang, et al. | *The VoiceMOS Challenge 2024: Beyond Speech Quality Prediction* | arXiv:2409.07001 (Proc. Interspeech/VoiceMOS 2024) | [arXiv:2409.07001](https://arxiv.org/abs/2409.07001) | Recommended by Rev 1 & 2. Forms the benchmark foundation for modern automated MOS estimators. |
| `fastl2007psychoacoustics` | Hugo Fastl, Eberhard Zwicker | *Psychoacoustics: Facts and Models (3rd Edition)* | Springer, 2007 | [10.1007/978-3-540-68888-4](https://doi.org/10.1007/978-3-540-68888-4) | Replaces bogus Kominek & Black citation for psychoacoustic pitch JND and cent scale. |

---

## Detailed Investigation of Hallucinated & Corrupted Citations

### 1. `wang2023gzstvZS` — Hallucinated Nonexistent Reference
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @inproceedings{wang2023gzstvZS,
    title={Generalised Zero-Shot Text-to-Speech via Voice Embedding},
    author={Wang, Hanzhao and others},
    booktitle={Proc. Interspeech},
    year={2023}
  }
  ```
- **Reviewer #2 Remark:** *"Wang, H. 2023b InterSpeech Generalised zero-shot text-to-speech via voice embedding. -- does not exist"*
- **Audit Findings:** Exhaustive queries across Interspeech 2023 proceedings, ISCA Archive, DBLP, Google Scholar, and arXiv show **no paper with this title or author exists**. The author key suffix `ZS` indicates a probable LLM generation artifact during manuscript preparation.
- **In-Text Usage:** Cited at line 149 in Section 2.1 to justify zero-shot speaker embedding cosine similarity.
- **Remedy:** **Completely excised.** In-text citation removed; sentence revised to cite verified speaker embedding literature.

### 2. `jain2023indicTTS` — Wrong Attribution
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @article{jain2023indicTTS,
    title={Towards Building Text-To-Speech Systems for the Next Billion Users},
    author={Jain, Praveen and others},
    journal={arXiv preprint arXiv:2211.09536},
    year={2022}
  }
  ```
- **Reviewer #2 Remark:** *"Jain, P., et al., 2022... does not exist. The title is listed under another author, Kumar et al., 2022."*
- **Audit Findings:** The title exists under arXiv:2211.09536, published in IEEE ICASSP 2023. The authors are: **Gokul Karthik Kumar, Praveen S V, Pratyush Kumar, Mitesh M. Khapra, and Karthik Nandakumar**. The surname "Jain" was hallucinated, likely confusing coauthor Praveen S V with a fictitious "Praveen Jain".
- **Remedy:** Replaced entry with authoritative ICASSP 2023 citation `kumar2023indic`; updated text citation key.

### 3. `pashto2025bench` — False Anonymity & Date Error
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @misc{pashto2025bench,
    title={Pashto{TTS}-Bench: Automated Screening for Low-Resource Non-{Latin}-Script Text-to-Speech},
    author={Anonymous},
    year={2025},
    eprint={2605.26978},
    archivePrefix={arXiv}
  }
  ```
- **Reviewer #2 Remark:** *"Anonymous, 2025... is not anonymous."*
- **Audit Findings:** arXiv preprint `2605.26978` exists under the title *PashtoTTS-Bench: Automated screening for low-resource non-Latin-script text-to-speech*. The author is **Hanif Rahman**, submitted May 26, 2026. The paper is not anonymous, and the year is 2026.
- **Remedy:** Updated author to `Rahman, Hanif`, year to `2026`, key to `rahman2026pashto`.

### 4. `chiang2024mushra` — Severe Author Misattribution
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @inproceedings{chiang2024mushra,
    title={Rethinking {MUSHRA}: Addressing Modern Challenges in Text-to-Speech Evaluation},
    author={Chiang, Christoph and others},
    journal={arXiv preprint arXiv:2411.12719},
    year={2024}
  }
  ```
- **Audit Findings:** arXiv:2411.12719 is titled *Rethinking MUSHRA: Addressing Modern Challenges in Text-to-Speech Evaluation*. The actual authors are: **Praveen Srinivasa Varadhan, Amogh Gulati, Ashwin Sankar, Srija Anand, Anirudh Gupta, Anirudh Mukherjee, Shiva Kumar Marepally, and Ankur Bhatia**. "Christoph Chiang" does not exist and was not an author on this paper. (The author "Chiang" was conflated with Cheng-Han Chiang from Interspeech 2024).
- **Remedy:** Updated to `varadhan2024mushra` with verified author list.

### 5. `chiang2024mushraevaluate` — Corrupted Author Names
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @inproceedings{chiang2024mushraevaluate,
    author    = {Chiang, Chia-Yu and Lee, Hung-yi},
    title     = {A Study on the Applicability of MUSHRA to Evaluate Neural Text-to-Speech Systems},
    booktitle = {Proceedings of Interspeech},
    year      = {2024},
    pages     = {2195--2199},
    doi       = {10.21437/Interspeech.2024-1354}
  }
  ```
- **Audit Findings:** The paper and DOI (10.21437/Interspeech.2024-1354) exist, but the authors are **Cheng-Han Chiang, Wei-Ping Huang, and Hung-yi Lee**. The first author was listed as "Chia-Yu" instead of "Cheng-Han", and co-author "Wei-Ping Huang" was omitted.
- **Remedy:** Corrected author field to `Chiang, Cheng-Han and Huang, Wei-Ping and Lee, Hung-yi`.

### 6. `naseem2025urdu` — Corrupted Author and Publication Date
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @inproceedings{naseem2025urdu,
    title={Evaluating and Developing {TTS} Models for {Urdu} and {Punjabi}},
    author={Naseem, Shahid and others},
    booktitle={Proc. Interspeech},
    year={2025}
  }
  ```
- **Audit Findings:** The actual paper is *Developing High-Quality TTS for Punjabi and Urdu: Benchmarking against MMS Models*, authored by **Fatima Naseem, Maham Sajid, Farah Adeeba, Sahar Rauf, Asad Mustafa, Sarmad Hussain, and Faisal Kamiran**, published in **Interspeech 2024** (DOI: 10.21437/Interspeech.2024-114). The name "Shahid Naseem" and year "2025" were corrupted.
- **Remedy:** Replaced title, author list, year, and key (`naseem2024developing`).

### 7. `arshad2022transfer` — Corrupted Lead Author
- **Original Entry in `cas-refs.bib`:**
  ```bibtex
  @inproceedings{arshad2022transfer,
    title={Exploring Transfer Learning for {Urdu} Speech Synthesis},
    author={Arshad, Hafsa and others},
    booktitle={Proc. EurALI},
    year={2022}
  }
  ```
- **Audit Findings:** The paper *Exploring Transfer Learning for Urdu Speech Synthesis* was published at the EurALI workshop at LREC 2022 (ACL Anthology: `2022.eurali-1.3`). The authors are **Sahar Jamal, Sadaf Abdul Rauf, and Quratulain Majid**. "Hafsa Arshad" was not an author.
- **Remedy:** Corrected author list and key (`jamal2022transfer`).

### 8. `kominek2008mcd` — Severe Claim Misattribution
- **Original In-Text Citations:** Attached to F0 RMSE at lines 149, 501, 669, and 682:
  *"Fundamental frequency RMSE (F0~RMSE), expressed in cents on a logarithmic scale (Kominek and Black, 2008), measures pitch accuracy in a perceptually meaningful unit where approximately five cents approximates one just-noticeable difference in pitch..."*
- **Audit Findings:** Kominek & Black (2008) is titled *Synthesizer voice quality of new languages calibrated with mean MCD* (SLTU 2008). It is purely about MCD (Mel-Cepstral Distortion). It does not mention fundamental frequency, F0 RMSE, cents, or pitch JND.
- **Remedy:** Removed `kominek2008mcd` from all F0 and pitch statements. Retained strictly for the Kominek-Black MCD scaling factor ($10\sqrt{2}/\ln 10 \approx 6.142$). Added Fastl & Zwicker (2007) for psychoacoustic pitch JND context, explicitly noting that laboratory pure-tone JND (~5 cents) does not equate to running speech pitch thresholds (~100–200 cents).

---

## Final Clean BibTeX Entries for Corrected Files

The repaired `cas-refs.bib` in `manuscript_revision/` includes exact, validated entries for all corrected works and removes `wang2023gzstvZS` and `\nocite{*}`.

