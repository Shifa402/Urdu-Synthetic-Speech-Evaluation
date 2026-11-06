# 00: Decision and Reviews (Verbatim)

## Manuscript Metadata and Provenance

- **Journal:** *Computer Speech & Language* (Elsevier)
- **Manuscript Reference Number:** `YCSLA-D-26-00760`
- **Article Title:** *Domain-Specific Evaluation of Text-to-Speech Systems: A Multi-Metric Benchmarking Study*
- **Authors:** Ali Jafar, Amal Sarmad, Shifa Yousaf, Maryam Bashir
- **Author Affiliation:** FAST School of Computing, National University of Computer and Emerging Sciences (FAST-NUCES), Lahore, Punjab, Pakistan
- **Submission Date:** July 28, 2026
- **Decision Date:** November 5, 2026
- **Decision:** Reject
- **Handling Editor:** Confidential / Anonymous Editorial Board Member, *Computer Speech & Language*
- **Revision Branch / Local Working Directory:** Branch `revision-repair`, Working directory `/home/ali-jafar/Urdu-Synthetic-Speech-Evaluation`
- **Submitted File Baseline:** `research/cas-sc-template.tex`, `research/cas-refs.bib`, `research.zip` (timestamped 2026-08-03 18:23:23 PKT; compiled PDF: `TTS_Research_Paper.pdf`, 2026-08-03 19:34:33 PKT)

---

## Verbatim Decision Letter and Reviewer Comments

```text
Handling Editor: Both reviewers agree that even though the overall research question is of interest, the manuscript has significant methodological flaws, does not take into account the current state of the art, and draws conclusions that do not follow from the reported study. More gravely, one reviewer remarks that the manuscript contains non-existing, most likely hallucinated references. This point alone throws a serious doubt on the scientific rigour and overall integrity of the conducted research and writing process.

We have therefore decided to reject the manuscript. We hope the authors find the reviewer feedback helpful, and encourage them to reconsider some of their methodological choices in the future.

Reviewer #1: The paper introduces an analysis of several available TTS systems for Urdu across 4 generation domains. The selected topic is of interest to the research community and does indeed touch on the generalisation ability of commercial and open source TTS systems.
However, the methodology does not clearly support the stated scope of the paper, some necessary details are omitted, and the selection of evaluation criteria is not up-to-date.
I encourage the authors to extend the selection of systems, as well as the objective and subjective evaluation methods and resubmit a more thorough review of their work.

Specific comments and suggestions:
- The related work section clearly needs improvement, as LeMaguer's paper is not the only one looking into the flaws of TTS evaluation
- The domain selection is appropriate, however, it is not clear how you control for the domains. Is it just the input text? Why not use the description for ParlerTTS to control the output?
- It is not clear how you truly use the selected speech corpora? Do you use each utterance to control the output of the TTS? Do you use the same input text as in the original utterance?
- Was the Resemblyzer model trained on Urdu speakers? If not, there might be a mismatch between the training and test data, hence unreliable similarity measures.
- MCD and F0 RMSE are not realiable measures of quality. They were used in previous TTS technologies, when the alignment between input and output was easier to perform. Nowadays, especially for ALMs, I do not believe that DTW alone can perform such measure. Also, if there are different speakers, as in the MMS systems, this would clearly generate a random value, and not a true measure of quality.
- What about using automatic MOS ratings? And what about WER? Both measures are common in today's literature.
- You mention that previous evaluations of TTS systems was performed using only MOS ratings. That is not true for the past 5 years of scientific publications at least.
- You need to add the exact links to the TTS systems that you used
- DId you upsample the data for MCD? If so, then there is no information in the 8k-11k frequency band for the original samples.
- Please add more details on how you control for the 4 domains.
- You used a 5-point scale for the MUSHRA evaluation. This defeats its purpose, and you somehow fell back to MOS ratings, rather than exploit the MUSHRA advantages.
- Why did you use only male data?
- The setup of the MUSHRA listening test could have been performed in a webpage, and no installation would have been required on the listener's side
- I commend the time you spent on setting up Google Forms for the listening test. If indeed you evaluated that many utterances and domain pairs, that would have taken quite a lot of effort.
- I am a bit surprised by the low ratings in the MUSHRA results. I would imagine that commercial Urdu systems are quite close to natural speech.

In conclusion, I believe that the selected topic is very important, especially for low resource languages. But for it to reveal definite statements for the community, it needs a better and more extended evaluation methodology.


Reviewer #2: This paper evaluates 4 Urdu TTS synthesisers (Indic-Parler-TTS, MMS-TTS, Microsoft Edge TTS, and Google Gemini TTS) using subjective and objective evaluation paradigms. The main contributions of this paper is to produce a cross-domain evaluation, across Formal, Conversational, Literary/Storytelling, and Emotional domains and to critically assess the performance of the TTS synthesiser from a user and task centric perspective. Results of this investigation show variable performance of TTS models across domains. An important, generalisable finding is that conversational speech consistently yields the highest overall acoustic fidelity, whereas emotional speech poses the primary synthesis challenge addresses a crucial gap in speech synthesis literature by presenting a domain-stratified evaluation of Text-to-Speech (TTS) systems for Urdu.

Strengths: The main strengths of this paper are as follows: First, a cross-domain benchmark is an important contribution across any language, and particularly so for a low-resource one. Sustained efforts in this direction are encouraged, and must continue. Secondly, the organisation of the paper makes it simple and readable. Finally, the authors situate their experimental choices within the previously published literature - the use of MUSHRA and ABX against MOS is well motivated, citing ceiling effects.

Weaknesses:
I. There are fake citations: 1. Jain, P., et al., 2022. "Towards building text-to-speech systems for the next billion users", arXiv:2211.09536 -- does not exist. The title is listed under another author, Kumar et al., 2022.
2. Wang, H. 2023b InterSpeech Generalised zero-shot text-to-speech via voice embedding. -- does not exist 3. Anonymous, 2025. PashtoTTS-bench: Automated screening for lowresource non-Latin-script text-to-speech. arXiv:2605.26978. -- is not anonymous. There may be more such references, but these spot checks were enough to tell me that the literature survey was not verified before submission. Reporting hallucinated citations is pretty serious, as it puts other conclusions made by the authors into perspective.

II. Objective evaluation: better architectures already exist
The authors' use of MCD, F0 RMSE and acoustic similarity between target and reference speaker are relatively outdated. Several methods for objective evaluation exist. The authors are encouraged to follow the work of Cooper et al., particularly originating in the VoiceMOS challenge. Much higher alignment rates can be expected with human subjective ratings, but in the context of Urdu improvements are definitely worth exploring.

III. Confusing conceptual terminologies Beginning with the minor - The authors' use of the term "metrics" is confusing. Metrics are those attributes over which opinion is collected (e.g, naturalness, human-likeness, quality). Why does this set of authors use the word "metrics" when they actually mean an evaluation technique. Additionally, the use of the term "naturalness" is slightly worrisome in multilingual contexts. Please consider these references: - S. Shirali-Shahreza and G. Penn, "Better replacement for tts naturalness evaluation," in 12th ISCA Speech Synthesis Workshop (SSW2023). ISCA, Aug. 2023, p. 197-203. [Online]. Available: http://dx.doi.org/10.21437/ssw.2023-31 - Pandey, A., Le Maguer, S., & Harte, N. (2025, August). What is naturalness?. In Proceedings of the 13th edition of the Speech Synthesis Workshop (pp. 215-221). ISCA-International Speech Communication Association 10.21437/SSW.2025-33 It is good to provide a definition, like the authors have. But how did you translate the word naturalness into Urdu?

Finally - I cannot find sufficient citations to use "cents" as the unit for log F0 RMSE. The Kominek and Black, 2008 paper cited as its source is the origin for MCD, not for RMSE. And it does not have the word cents at all.


My overall recommendation is that the paper needs to be revised well, as the authenticity of the draft is circumspect. It is really clear to read, but not technically solid. Secondly, experimental details can be substantiated with newer objective evaluation techniques. This is especially important because the paper's aim is to also find a clear winner among the TTS evaluated - and divergence in evaluation techniques confounds this problem. So I strongly encourage the direction and motivation of this paper - but a battery of modern experiments on the objective side, and a serious, hand-verified redrafting will be required before publication.
```

---

## Editorial Transfer Offer and Context (November 5, 2026)

Following rejection from *Computer Speech & Language*, the Elsevier editorial handling system provided an automated transfer invitation offering expedited submission to five alternative Elsevier journals. 

### User-Supplied Transfer Offer Figures (Raw Display Data, Unverified)

| Journal | Displayed IF | Displayed CiteScore | Displayed First Decision | Displayed Acceptance to Publication | Displayed Open Access APC (excl. tax) | Displayed Subscription / Publishing Charge |
|---|---:|---:|---:|---:|---:|---|
| **Speech Communication** | 2.9 | 7.4 | 49 days | 7 days | USD 3,280 | **No publishing charge (Subscription model)** |
| **Natural Language Processing Journal** | Not shown | 9.1 | 10 days | 5 days | USD 915 promotional; USD 1,830 standard | None shown (OA only) |
| **Array** | 5.3 | 10.1 | 9 days | 6 days | USD 2,770 | None shown (OA only) |
| **Computers in Human Behavior Reports** | 5.5 | 7.7 | 7 days | 5 days | USD 2,980 | None shown (OA only) |
| **Expert Systems with Applications** | 9.4 | 17.0 | 5 days | 7 days | USD 3,630 | **No publishing charge (Subscription model)** |

### Critical Context and Warnings Regarding Transfer
1. **Promotional Deadline Warning:** The transfer offer noted a 50% discount on *Natural Language Processing Journal* APC (USD 915 vs USD 1,830) valid until December 31, 2026. **This discount deadline must NOT cause a rushed, unverified resubmission.** Scientific rigor and evidence validity strictly supersede promotional fee deadlines.
2. **Review Guarantee vs Acceptance:** The transfer notice states that *Array* and *Computers in Human Behavior Reports* guarantee peer review of the transferred manuscript. This is **not a guarantee of acceptance**.
3. **Statistical Acceptance Claims:** The service notes that manuscripts transferred via the service have an aggregate 66% higher relative acceptance rate than direct submissions across Elsevier's entire portfolio. This is a general publisher statistic, **not an individual probability of acceptance** for this specific manuscript.
4. **Institutional Agreement / Waiver Status:** The notice suggested potential open-access agreement benefits for corresponding authors affiliated with FAST-NUCES (described in the Elsevier system as Islamabad, Pakistan). The manuscript affiliation is FAST-NUCES Lahore. Eligibility under Pakistani national consortium agreements or institutional waivers must be verified directly through official university and library channels. **The affiliation must remain truthful (Lahore) and never altered to seek commercial benefits.**
5. **No Resubmission without Authorization:** The authors retain full ownership of the submission decision. No transfer link or decline button will be clicked by automated agents.

