# 09: Experiment and Statistics Plan

## Statistical Diagnosis of Original Manuscript

The original manuscript suffered from severe inferential deficiencies:
1. **Pseudoreplication:** Ratings from 20 listeners evaluating multiple items were aggregated as naive sample means and standard deviations, treating repeated ratings as independent observations.
2. **Ignored Clustering:** Nested variance across listeners ($u_l$) and items ($v_i$) was entirely unmodeled.
3. **Absence of Uncertainty Intervals:** No 95% confidence intervals, standard errors, or hypothesis tests (e.g. ANOVA, LMM, or permutation tests) were reported for Table 4 or Table 7.
4. **Uncorrected Multiplicity:** Post-hoc pairwise claims (e.g., "Gemini significantly outperformed Edge") were asserted based on small mean differences (3.040 vs 2.947, $\Delta = 0.093$ on a 1–5 scale) without standard error estimation or family-wise error correction.
5. **Masked Missing Data:** Missing F0 data points were silently omitted while claiming 100% complete coverage.

This document establishes the inferential framework required for a publication-ready revision in *Speech Communication* or *IEEE TASLP*.

---

## 1. Formal Experimental Hypotheses

| Hypothesis ID | Scientific Proposition | Null Hypothesis ($H_0$) | Statistical Outcome & Test |
|---|---|---|---|
| **$H_1$ (Domain Effect)** | Textual genre significantly affects synthetic speech intelligibility (WER) and perceived naturalness across Urdu TTS systems. | System performance does not vary across the 4 text domains ($\beta_{\text{Domain}} = 0$). | Fixed effect of Domain in Linear Mixed-Effects Model (LMM), Type III Wald $F$-test. |
| **$H_2$ (System Effect)** | Proprietary cloud systems (Edge, Gemini) achieve significantly higher naturalness ratings than open-source baselines (Indic-Parler, MMS). | All 4 TTS architectures achieve identical mean ratings ($\beta_{\text{System}} = 0$). | Fixed effect of System in LMM, followed by Tukey HSD post-hoc pairwise contrasts ($\alpha = 0.05$). |
| **$H_3$ (System $\times$ Domain Interaction)** | System ranking varies depending on communicative domain (e.g., one system excels in formal read speech while another leads in conversational). | Interaction between System and Domain is zero ($\beta_{\text{System} \times \text{Domain}} = 0$). | Interaction term in LMM; tests whether a single "winner" exists. |
| **$H_4$ (Metric Divergence)** | Subjective perceptual naturalness does not significantly correlate with unaligned reference acoustic distance (MCD, F0 RMSE). | Correlation between human ratings and MCD/F0 RMSE is non-zero ($\rho \neq 0$). | Spearman rank correlation ($\rho$) and Kendall's $\tau$ with bootstrap 95% confidence intervals. |

---

## 2. Sampling Units and Hierarchical Structure

In subjective speech evaluations, data is organized in a three-level hierarchical structure:

```
[Level 3: Rater Population] --------> [Listener l] (Random Intercept u_l)
                                          |
[Level 2: Item Corpus] -------------> [Source Utterance i] (Random Intercept v_i)
                                          |
[Level 1: System Stimulus] ---------> [Rating Y_lijk] (System k in Domain j)
```

- **Observational Unit:** Individual trial rating $Y_{lijk}$ awarded by Listener $l$ to Item $i$ synthesized by System $k$ in Domain $j$.
- **Sampling Units:** 
  - $N_{\text{listeners}} = 30$ randomly sampled native Urdu speakers.
  - $N_{\text{items}} = 60$ randomly sampled source texts ($15$ per domain).
  - $N_{\text{systems}} = 4$ fixed experimental conditions.

---

## 3. Statistical Modeling Specifications

### A. Primary Outcome: Linear Mixed-Effects Model (LMM)
For continuous MUSHRA scores ($Y \in [0, 100]$):
$$Y_{lijk} = \mu + \text{System}_k + \text{Domain}_j + (\text{System} \times \text{Domain})_{kj} + u_l + v_i + w_{li} + \epsilon_{lijk}$$
Where:
- $\mu$: Grand population intercept.
- $\text{System}_k$: Fixed effect of TTS system ($k \in \{\text{Edge, Gemini, Indic-Parler, MMS}\}$).
- $\text{Domain}_j$: Fixed effect of speech domain ($j \in \{\text{Formal, Conv, Lit, Emot}\}$).
- $(\text{System} \times \text{Domain})_{kj}$: System-by-domain interaction term.
- $u_l \sim \mathcal{N}(0, \sigma_u^2)$: Random intercept for Listener $l$.
- $v_i \sim \mathcal{N}(0, \sigma_v^2)$: Random intercept for Item $i$.
- $w_{li} \sim \mathcal{N}(0, \sigma_w^2)$: Random interaction between listener and item (optional).
- $\epsilon_{lijk} \sim \mathcal{N}(0, \sigma^2)$: Residual Gaussian observation error.

*Implementation:* Executed using Python `statsmodels.regression.mixed_linear_model.MixedLM` or R `lme4::lmer`.

### B. Ordinal Outcome: Cumulative Link Mixed Model (CLMM)
If ratings are collected on a discrete 1–5 Likert scale, linear models violate normality assumptions. A cumulative logit mixed model must be estimated:
$$\text{logit}(P(Y_{lijk} \le c)) = \theta_c - \left( \beta_k^{\text{Sys}} + \beta_j^{\text{Dom}} + (\beta \beta)_{kj} + u_l + v_i \right)$$
for cutpoints $c \in \{1, 2, 3, 4\}$.

### C. Forced-Choice ABX Discrimination: Generalized Linear Mixed Model (GLMM)
For binary ABX accuracy ($Z_{lik} \in \{0, 1\}$, where 1 = correct discrimination from reference, 0 = incorrect):
$$\text{logit}(P(Z_{lik} = 1)) = \beta_0 + \beta_k^{\text{Sys}} + \beta_j^{\text{Dom}} + u_l + v_i$$
- A one-sample test against chance evaluates whether the grand intercept odds $\exp(\beta_0)$ is significantly greater than $1.0$ ($P = 0.50$).
- If confidence intervals for $\beta_0$ include 0, systems are indistinguishable from natural speech.

---

## 4. Multiplicity Correction & Contrast Testing

With 4 systems and 4 domains, unconstrained testing produces 24 pairwise system comparisons and 6 domain comparisons. To prevent inflation of family-wise Type I error:
1. **Omnibus Gate:** Pairwise contrasts are conducted **only if** the omnibus Type III Wald $F$-test for the main effect or interaction is statistically significant at $\alpha = 0.05$.
2. **Post-Hoc Multiplicity Control:**
   - Pairwise contrasts between systems within domains are adjusted using **Tukey’s Honest Significant Difference (HSD)** test.
   - Non-orthogonal exploratory contrasts are adjusted via the **Benjamini-Hochberg False Discovery Rate (FDR)** procedure with $q = 0.05$.
3. **No Winner Declaration on Overlapping CIs:** If two systems have overlapping 95% confidence intervals (e.g. Edge 3.09 [2.85, 3.33] vs Gemini 3.15 [2.90, 3.40]), the manuscript must formally declare them **statistically indistinguishable**, rather than naming a numerical winner.

---

## 5. Missing Data, Denominators, and Leakage Prevention

### A. Missing Data Protocol
- **Acoustic Alignment Failures (F0 RMSE):** Two conversational files failed DTW voiced frame alignment (`n_f0_frames_used = 0`). Imputing zero or global means distorts variance. These rows are treated as **Missing Completely at Random (MCAR)** and excluded on an item-by-metric basis. Valid sample sizes must be reported as $n=240$ for Edge/MMS, and $n=239$ for Gemini/Indic-Parler.
- **Listener Dropouts:** In web-based listening tests, raters who abandon before completing all blocks are excluded completely if $<80\%$ complete; otherwise analyzed via mixed-effects models which natively tolerate unbalanced data without ad-hoc mean imputation.

### B. Machine Learning Leakage Prevention
For automated MOS evaluation and ASR calibration:
- **No Training/Test Overlap:** If an automated model is fine-tuned or calibrated on Urdu human ratings, training and validation splits must be strictly partitioned by **source item and speaker** (Leave-One-Domain-Out or 5-Fold GroupKFold on Item ID).
- Never report correlation on the exact training set or on domain aggregates without item-level cross-validation.

