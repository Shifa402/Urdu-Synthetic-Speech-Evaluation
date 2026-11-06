# 11: Journal and Transfer Strategy

## Strategic Context and Policy Directives

Following rejection from *Computer Speech & Language* (CS&L) on November 5, 2026, the authors received an automated editorial transfer offer proposing five alternative Elsevier titles. Additionally, the authors are evaluating *IEEE/ACM Transactions on Audio, Speech, and Language Processing* (TASLP) as an ambitious aspirational venue.

**Core Policy Directives:**
1. **Scientific Readiness Over Journal Prestige:** No manuscript will be submitted or transferred until all bibliographic errors, data integrity flaws, and reporting gaps are fully resolved.
2. **Transfer Reminders & Authorization:** Transfer is entirely optional and permits full manuscript revision prior to completing the submission. The authors retain sole authority; **no automated agent will click transfer or decline**.
3. **No Fee-Driven Rushing:** The promotional 50% discount on *Natural Language Processing Journal* (USD 915 until December 31, 2026) must not compel a rushed resubmission that compromises scientific integrity.
4. **Distinction of Data Provenance:** Publisher-supplied marketing figures from the rejection letter are explicitly separated from independently verified bibliographic and quartile metrics.
5. **Truthful Affiliation & Funding:** The authors' true institutional affiliation is **FAST-NUCES Lahore**. Affiliations will never be altered to seek open-access waiver eligibility under Islamabad consortium terms.

---

## 1. Comparative Venue Matrix (Supplied vs. Independently Verified Data)

| Journal | Publisher & Model | Displayed Transfer Offer Data (Nov 5, 2026) | Independently Verified Current Metrics | Database, Category & Quartile Status | Topic Fit for Revised Study |
|---|---|---|---|---|---|
| **Speech Communication** | Elsevier (Hybrid / ISCA official) | IF 2.9, CiteScore 7.4; First dec: 49d; APC: \$3,280; Sub: Free | Scopus CiteScore: 7.4; Impact Factor: ~2.9; Official journal of ISCA & EURASIP | **SCImago Q1** (Communication; Linguistics & Language); **Q2** (CS Applications, Software) | **EXCELLENT (Rank #1 Provisional Candidate)**. Dedicated speech community audience. |
| **Natural Language Processing Journal** | Elsevier (Gold OA) | CiteScore 9.1; First dec: 10d; APC: \$915 (promo) / \$1,830 (std) | Scopus CiteScore: 9.1; Launched 2022; Gold Open Access only | Emerging journal; indexing growing; Scopus Q1 CiteScore | **GOOD (Fallback Candidate)**. Fits language technology benchmarks. |
| **Array** | Elsevier (Gold OA) | IF 5.3, CiteScore 10.1; First dec: 9d; APC: \$2,770; Sub: None | Scopus CiteScore: 10.1; IF: ~5.3; Multidisciplinary open access CS | **SCImago Q1/Q2** (General Computer Science) | **MODERATE (Broad Fallback)**. Broad CS audience; lacks speech specialist reviewers. |
| **Computers in Human Behavior Reports** | Elsevier (Gold OA) | IF 5.5, CiteScore 7.7; First dec: 7d; APC: \$2,980; Sub: None | Scopus CiteScore: 7.7; IF: ~5.5; Behavioral & psychological focus | **SCImago Q1** (Psychology, Human-Computer Interaction) | **POOR (Misaligned Scope)**. Requires primary focus on human cognitive behavior. |
| **Expert Systems with Applications** | Elsevier (Hybrid) | IF 9.4, CiteScore 17.0; First dec: 5d; APC: \$3,630; Sub: Free | Scopus CiteScore: 17.0; IF: ~8.5–9.4; Very high submission volume | **SCImago Q1** (Artificial Intelligence, Computer Science Applications) | **POOR (High Desk-Reject Risk)**. Prioritizes novel algorithms over speech benchmarking. |
| **IEEE/ACM Trans. on Audio, Speech & Lang. Processing** | IEEE / ACM (Hybrid) | Not part of Elsevier transfer system | Impact Factor: ~4.1; CiteScore: 8.8; Premier flagship speech journal | **SCImago Q1 across all categories** (Acoustics, Speech & Hearing, Signal Processing) | **AMBITIOUS (Aspirational Target)**. Requires expanded experiments and full modeling. |

---

## 2. Detailed Venue Evaluation and Recommendation

### Candidate 1: *Speech Communication* (Elsevier / ISCA) — **PRIMARY TARGET**
- **Aims and Scope:** Published in association with the European Association for Signal Processing (EURASIP) and the International Speech Communication Association (ISCA). Explicitly covers speech synthesis, evaluation methodologies, acoustic analysis, and multilingual speech corpora.
- **Why It Is the Best Fit:**
  1. *Audience Alignment:* The reviewers will be speech scientists and phoneticians who directly appreciate the value of low-resource benchmark corpora and nuanced evaluation methodology.
  2. *Financial Feasibility:* Operates under a traditional **hybrid model**. Authors can choose the subscription publishing route with **ZERO publishing fees (USD 0 APC)**, eliminating reliance on unverified institutional OA waivers.
  3. *Review Expectations:* Values rigorous experimental design, transparent reporting of limitations, and robust subjective listening protocols over flashy, unverified claims.
- **Required Minimum Enhancements to Submit:** Resolution of all data/citation errors (`ED-002`), clear text-domain reframing (`R1-002`), normalized ASR evaluation (`R1-006`), and either recovered survey data or a 30-listener webMUSHRA collection (`R1-011`).

---

### Candidate 2: *IEEE/ACM Transactions on Audio, Speech, and Language Processing* (TASLP) — **ASPIRATIONAL TARGET**
- **Aims and Scope:** The premier archival journal in speech and audio processing. Publishes original, deep technological and methodological contributions.
- **Fit Assessment:** A purely descriptive benchmarking paper of existing models will likely face desk rejection or harsh review at IEEE TASLP. To be competitive at TASLP, the study must be elevated into an **extensive methodological contribution**:
  1. Full implementation of the multi-task evaluation framework (Task A: default presets; Task B: style prompt conditioning; Task C: voice cloning).
  2. Multi-model ASR intelligibility benchmarking with native speech controls.
  3. Full Linear Mixed-Effects Modeling (LMM) with listener/item random effects.
  4. Cross-lingual validation and failure analysis of SSL-based VoiceMOS estimators on Urdu.
- **Financial Route:** Hybrid journal; traditional publication without author fees up to 10 standard IEEE transaction pages (mandatory page charges apply only for pages $>10$).

---

### Candidate 3: *Natural Language Processing Journal* (Elsevier) — **FALLBACK OPTION**
- **Fit Assessment:** Strong emerging journal for NLP and language-specific benchmarks, particularly for underrepresented languages.
- **Decision Gate Regarding APC Discount:** The transfer letter advertises a promotional APC of USD 915 until December 31, 2026. If the authors choose this venue, the submission must proceed **only if** data recovery and revision are complete and verified. Under no circumstances should an unverified draft be submitted to meet the fee window.

---

### Candidates 4 & 5: *Expert Systems with Applications* & *Computers in Human Behavior Reports* — **NOT RECOMMENDED**
- **ESWA:** High Impact Factor (9.4) is tempting, but ESWA requires complex system architectures and expert decision support systems. A speech evaluation paper faces a very high probability of desk rejection for out-of-scope content.
- **CHBR:** Focuses on psychological outcomes, online behavior, and user technology adoption. Without empirical psychometric measures of listener mental workload or affective response, this venue is misaligned.

---

## 3. Strategic Submission Decision Gates

```
+--------------------------------------------------------------------------------------------------+
|                                    SUBMISSION DECISION TREE                                      |
+--------------------------------------------------------------------------------------------------+
                                                 |
                                                 v
                      [Phase 1 Complete: Local Repairs & Citation Integrity]
                                                 |
                                                 v
                     [Phase 2 Gate: Status of Raw Audio & Listener Data]
                                                 |
                       +-------------------------+-------------------------+
                       |                                                   |
              (Data Recovered /                                (Full New Campaign
               Basic Re-run)                                    Conducted: Tasks A+B+C)
                       |                                                   |
                       v                                                   v
        [Target: Speech Communication]                         [Target: IEEE/ACM TASLP]
        - Subscription model (USD 0)                           - Page-charge free subscription
        - Solid benchmark contribution                         - Deep methodological contribution
        - Transparent limitations                              - LMM statistical modeling
                       |                                                   |
                       v                                                   v
          (If rejected after review)                             (If rejected / transfer)
                       |                                                   |
                       +-------------------------+-------------------------+
                                                 |
                                                 v
                           [Fallback: Natural Language Processing Journal]
                           - Solid language technology venue
                           - Gold Open Access (Verify waiver or funding)
```

