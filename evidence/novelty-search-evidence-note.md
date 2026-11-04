# Documented Novelty Search — Evidence Note

**Paper:** "Three Philosophies of Artificial Will: How Frontier LLMs Decide When Logic Cannot" (reframed version, target: *Minds and Machines*)
**Purpose:** Replace the manuscript's non-reproducible novelty claims (based on "Perplexity Pro Deep Search", §1/§5 of the original draft, including the claims that four phenomena are "novel", that the novelty distribution is "Novel 4 / Partially Novel 11 / Previously Documented 0", and that "no prior framework" exists) with a real, auditable bibliographic search.
**Access date for all searches:** 2026-11-03
**Rule applied throughout:** No claim of absolute novelty. This note supports, at most, the phrasing **"no direct precedent found in [this search]"**, cluster by cluster, and only where stated below.

---

## 1. Method and reproducibility

Searches were run from the terminal against three public APIs:

1. **Crossref** (`api.crossref.org/works?query.bibliographic=…&rows=10`) — primary search source. Exact query strings, the returned `total-results`, and the relevance-ranked top 10 records for every query were logged.
2. **arXiv API** (`export.arxiv.org/api/query?search_query=…`) — phrase-based searches; `opensearch:totalResults` and the top entries were logged. arXiv matters here because much of the LLM-behaviour literature appears there first.
3. **OpenAlex** (`api.openalex.org`) — **search endpoint could not be used**: every `/works?search=…` request on 2026-11-03 returned the error *"Rate limit exceeded — Insufficient budget. This request has no API key, so it counts against the free daily budget shared by everyone on your network's IP address, and that budget is used up ($0 remaining; resets at midnight UTC)."* No OpenAlex search counts therefore exist in this note, and none are invented. The OpenAlex **single-work DOI endpoint did work** and was used to verify the bibliographic details of every specific candidate record listed in §4 (each verification is a `https://api.openalex.org/works/https://doi.org/<doi>` lookup, 2026-11-03). Crossref DOI/title lookups were used the same way where noted.

**Raw logs (same folder):** `crossref-search-log-2026-11-03.json`, `arxiv-search-log-2026-11-03.json`, `verified-records-2026-11-03.json`.

**Critical caveat on Crossref hit counts:** Crossref `total-results` for `query.bibliographic` counts records matching the query *terms* (any-term, relevance-ranked), so for multi-term queries it returns millions and is **not** a precision count of on-topic papers. The counts are recorded below exactly as returned, for auditability, but all screening judgements rest on (i) the relevance-ranked **top 10 titles** of each Crossref query and (ii) the arXiv phrase-search totals, which are restrictive. Anyone re-running the Crossref strings will get the same ranked lists (counts will drift upward as Crossref grows).

---

## 2. Search log

### 2a. Crossref (`query.bibliographic`, rows=10, 2026-11-03)

| ID | Cluster | Exact query string | Hits (`total-results`, as returned) |
|---|---|---|---|
| A1 | (a) | large language model Buridan's ass | 5,234,025 |
| A2 | (a) | LLM forced choice identical options | 609,082 |
| A3 | (a) | language model arbitrary choice between identical options | 7,317,465 |
| B1 | (b) | large language model choice identical options symmetry indifference | 5,819,314 |
| B2 | (b) | large language model symmetry breaking choice | 5,771,906 |
| C1 | (c) | large language model tie-breaking arbitrary decision | 6,160,318 |
| C2 | (c) | large language model random number selection bias | 6,318,690 |
| C3 | (c) | large language model position bias selection bias multiple choice | 7,134,097 |
| D1 | (d) | large language model confabulated self-report | 8,143,964 |
| D2 | (d) | LLM false self-report hallucination introspection | 3,115,994 |
| D3 | (d/e) | language model unfaithful explanations chain-of-thought | 5,070,910 |
| E1 | (e) | large language models same choice different reasons justification | 4,741,470 |
| E2 | (e) | LLM cross-model consensus choice justification divergence | 4,654,641 |
| K1 | known | Deterministic or probabilistic psychology of LLMs as random number generators | 1,902,466 |
| K2 | known | comparison large language model human performance random number generation tasks | 596,240 |
| V1 | verify | B3Emo Quantifying Affect as a Double-Edged Sword in Strategic LLM Interactions | 1,624,777 (rank-1 hit = the paper itself) |
| V2 | verify | Zhang conversational escalation emotional intensification continuous dialogues 2025 | 15,293,192 |
| V3 | verify | justification inflation large language model | 5,281,470 |

### 2b. arXiv API (phrase searches, 2026-11-03)

| ID | Cluster | Exact `search_query` | Hits (`totalResults`) |
|---|---|---|---|
| AX1 | (a) | `all:"Buridan"` | 8 |
| AX2 | (a/c) | `all:"random number generation" AND all:"large language models"` | 16 |
| AX3 | (b/c) | `all:"selection bias" AND all:"multiple choice"` | 13 |
| AX4 | (c) | `all:"tie-breaking"` | 237 (all fields; top hits are economics/game theory/algorithms, not LLMs) |
| AX5 | (b) | `all:"identical options"` | 6 |
| AX6 | (a) | `all:"forced choice" AND all:"language model"` | 60 |
| AX7 | (d) | `all:"introspection" AND all:"language models"` | 165 |
| AX8 | (d/e) | `all:"unfaithful" AND all:"chain-of-thought"` | 60 |
| AX9 | (e) | `all:"consensus" AND all:"justification" AND all:"language models"` | 11 |
| AX10 | (d) | `all:"self-report" AND all:"language models" AND all:"confabulation"` | 5 |
| AX11 | (d) | `all:"confabulation" AND all:"language models"` | 70 |

---

## 3. Screening results by cluster (top ~10 titles per search)

### (a) Forced choice / arbitrary choice between identical options / Buridan's ass + LLM
- **A1 (Crossref):** all 10 top hits are Buridan scholarship in philosophy/history (e.g., chapters on Buridan's mental language, 2008–2017) or unrelated; **no LLM experiment**.
- **AX1 (arXiv):** 8 hits total for "Buridan" — history of physics/philosophy, a quantum Buridan's-ass paper (2026), a decentralised-consensus paper (2026). **None applies Buridan's ass to LLMs.**
- **A2 (Crossref):** top hits concern forced-choice *formats* in LLM-administered personality/psychometric assessment (e.g., "Decoding LLM Personality Measurement: Forced-Choice vs. Likert", ACL Findings 2025, DOI 10.18653/v1/2025.findings-acl.480) — a different meaning of "forced choice". One tangential 2026 preprint, "Proof of Cognitive Divergence: Emergent Identity from Sampling Randomness in Identical LLM Agents" (Authorea, DOI 10.22541/au.177247325.53212131/v1), concerns *identical agents* diverging, not a model choosing between *identical options*; screened, not a precedent for this paradigm.
- **AX6 (arXiv):** 60 hits; top titles are psychometric forced-choice and evaluation-bias papers. None studies choices engineered to be logically indifferent.
- **A3 (Crossref):** top 10 entirely off-topic (options pricing, consumer choice psychology).
- **Screening verdict (a):** No direct precedent found in this search for an LLM Buridan-type / identical-options paradigm with logical indifference as the central variable.

### (b) Choice between identical options — symmetry / indifference
- **B1 (Crossref):** top hits are noise (papers in the journal *Symmetry*, theses) except one genuinely close neighbour at rank 7: **Pezeshkpour & Hruschka (2024)** on option-order sensitivity (verified in §4).
- **B2 (Crossref):** top 10 all physics/evacuation-modelling "symmetry breaking"; no LLM choice study.
- **AX5 (arXiv):** 6 hits for "identical options"; none is an LLM choice-between-identical-options study (one robotics disambiguation paper, the rest unrelated).
- **AX3 (arXiv):** 13 hits, all about **selection bias in multiple-choice QA** (see §4) — documented neighbouring territory, but those studies use questions *with* correct answers and study accuracy distortion, not indifference.
- **Screening verdict (b):** No direct precedent found for symmetry/indifference as the experimental variable; the neighbouring selection-bias literature is substantial and must be cited (it directly predicts parts of this paper's consensus patterns via token/position preferences).

### (c) Tie-breaking / arbitrary decisions (incl. random-number selection)
- **C1 (Crossref) / AX4 (arXiv):** no LLM tie-breaking study in the top hits; tie-breaking literature is economics/algorithms.
- **C2 (Crossref):** two close items in the top 10: "A Survey on Selection Bias in Large Language Models" (2026 preprint, DOI 10.20944/preprints202604.2234.v1 — post-dates the study, listed for completeness) and **"Emergent Numeric Bias in Large Language Models: An Empirical Study on the Anomalous Recurrence of the Number 27 Across Independent Sessions"** (Nath, 2025; verified in §4) — direct documentation of a specific-number attractor in exactly the "independent sessions" design this paper uses for its number prompt.
- **AX2 (arXiv):** 16 hits; the relevant ones are the dedicated LLM random-number-generation literature (Harrison 2024; Coronado-Blázquez 2025; Karanjai et al. 2025 — all verified in §4), documenting strong, model-specific, non-uniform number preferences.
- **Screening verdict (c):** Tie-breaking *outcomes* (which option/number a model lands on, and cross-model convergence on attractors such as 7) are **well documented** — this cluster is NOT novel as a phenomenon. What was not found is a study cataloguing the *verbalised tie-breaking rules* models announce (e.g., a stated left-rule, clock-modulo, quantum-fluctuation appeals) as a cross-model taxonomy; see §5.

### (d) Confabulated self-report of mechanism / false self-reference / system-clock self-report
- **D1, D2 (Crossref):** top 10s are noise (self-reflection/self-distillation engineering papers; human confabulation neurology). No hit describes a model fabricating a mechanism for its own choice (e.g., claiming to use a system clock it cannot access).
- **AX10 (arXiv):** only 5 hits for self-report + confabulation + language models; all are introspection papers, none about fabricated mechanism self-reports in a choice task. AX11 (confabulation generally): 70 hits, concerning hallucination/confabulation of *content*, not of *choice mechanisms*.
- **AX7 (arXiv):** 165 introspection hits; the verified close neighbours (§4) show the framing literature: models' access to their own processes is limited, learnable only in narrow ways, and conceptually contested (Binder et al. 2024; Betley et al. 2025; Song, Hu & Mahowald 2025; Comsa & Shanahan 2025). Also surfaced: Lindsey, "Emergent Introspective Awareness in Large Language Models" (arXiv record dated 2026-01-05 in the API listing) — noted, not relied on.
- **D3 (Crossref):** rank-1 hit is the canonical unfaithful-explanation paper (Turpin et al. 2023, verified in §4): models' stated reasons demonstrably do not always reflect the features driving their outputs.
- **Screening verdict (d):** No direct precedent found for the specific clock-modulo-type fabricated mechanism self-report in a symmetry-choice task. But the *interpretation* of such reports as confabulation/unfaithful self-explanation is established literature, not a novel insight of this paper.

### (e) Same choice, different justifications — justification divergence under cross-model consensus
- **E1 (Crossref):** top hits off-topic (justification logic, travel-mode choice, clinical-output reproducibility). No study of cross-model justification divergence under identical choices.
- **E2 (Crossref):** top hits are multi-model consensus *methods* (peer-review frameworks, market models), not behavioural comparisons of justifications.
- **AX9 (arXiv):** 11 hits; the closest is **Ding et al. (2025), "'Pull or Not to Pull?': Investigating Moral Biases in Leading Large Language Models Across Ethical Dilemmas"** (verified in §4) — a cross-model comparison on trolley-type dilemmas, i.e. the same comparison *genre* as this paper's trolley prompt, but about choice/bias patterns, not about justification divergence under output consensus.
- **AX8 (arXiv) / D3:** the faithfulness literature (Turpin et al. 2023; Lanham et al. 2023) documents within-model divergence between stated reasons and actual drivers — the conceptual neighbour for justification divergence.
- **Screening verdict (e):** No direct precedent found in this search for cross-model justification divergence under identical forced choices. Neighbouring literatures (unfaithful explanations; cross-model moral-choice comparisons) exist and must be cited.

---

## 4. Verified close / related precedents (every record verified 2026-11-03 via OpenAlex DOI lookup or Crossref, as noted — nothing here is taken from the manuscript's own reference list on trust)

**Selection / position / token bias in LLM choices (clusters b, c — MUST CITE):**
1. Zheng, C., Zhou, H., Meng, F., Zhou, J., & Huang, M. (2023). *Large Language Models Are Not Robust Multiple Choice Selectors.* arXiv:2309.03882. DOI: 10.48550/arXiv.2309.03882. — LLMs prefer specific option IDs because of token bias; the direct documented alternative explanation for this paper's corridor/option consensus patterns. (OpenAlex-verified.)
2. Pezeshkpour, P., & Hruschka, E. R. (2024). *Large Language Models Sensitivity to The Order of Options in Multiple-Choice Questions.* Findings of the Association for Computational Linguistics: NAACL 2024. DOI: 10.18653/v1/2024.findings-naacl.130. — Option-order (position) sensitivity. (OpenAlex-verified.)
3. Wei, S.-L., Wu, C.-K., Huang, H.-H., & Chen, H.-H. (2024). *Unveiling Selection Biases: Exploring Order and Token Sensitivity in Large Language Models.* Findings of the Association for Computational Linguistics: ACL 2024. DOI: 10.18653/v1/2024.findings-acl.333. (OpenAlex-verified; the OpenAlex record gives the ACL Findings DOI above.)
4. Wang, P., Li, L., Chen, L., Cai, Z., Zhu, D., et al. (2024). *Large Language Models are not Fair Evaluators.* Proceedings of ACL 2024 (Vol. 1: Long Papers). DOI: 10.18653/v1/2024.acl-long.511. — Position bias when LLMs judge paired options. (Crossref title-query verified.)

**Random-number / arbitrary-number selection (cluster c — MUST CITE):**
5. Harrison, R. M. (2024). *A Comparison of Large Language Model and Human Performance on Random Number Generation Tasks.* arXiv:2408.09656. DOI: 10.48550/arXiv.2408.09656. **Sole author.** (OpenAlex-verified. See §6: the manuscript's reference list miscites this record.)
6. Coronado-Blázquez, J. (2025). *Deterministic or probabilistic? The psychology of LLMs as random number generators.* arXiv:2502.19965. DOI: 10.48550/arXiv.2502.19965. **Sole author.** Documents cross-model convergence on culturally primed values (7 dominant in the 1–10 range in most configurations, per the paper's abstract as indexed). (OpenAlex-verified. See §6: also miscited in the manuscript.)
7. Karanjai, R., Yang, L., Chodavarapu, R., Xu, L., & Shi, W. (2025). *Evaluating the Quality of Randomness and Entropy in Tasks Supported by Large Language Models.* arXiv:2510.12080. DOI: 10.48550/arXiv.2510.12080. (OpenAlex-verified; author list as returned by OpenAlex — "Lu Yang" in the arXiv listing.)
8. Nath, S. S. (2025). *Emergent Numeric Bias in Large Language Models: An Empirical Study on the Anomalous Recurrence of the Number 27 Across Independent Sessions.* Research Square. DOI: 10.21203/rs.3.rs-7128459/v1 (also posted as SSRN 5404673). — Single-author preprint in a weak venue; cite, if at all, only as corroborating preprint evidence, clearly labelled as such. (OpenAlex-verified.)

**Unfaithful explanations / justification faithfulness (clusters d, e — MUST CITE):**
9. Turpin, M., Michael, J., Perez, E., & Bowman, S. R. (2023). *Language Models Don't Always Say What They Think: Unfaithful Explanations in Chain-of-Thought Prompting.* Advances in Neural Information Processing Systems 36 (NeurIPS 2023). Proceedings DOI: 10.52202/075280-3275; arXiv:2305.04388. (OpenAlex-verified.)
10. Lanham, T., Chen, A., Radhakrishnan, A., Steiner, B., Denison, C., et al. (2023). *Measuring Faithfulness in Chain-of-Thought Reasoning.* arXiv:2307.13702. DOI: 10.48550/arXiv.2307.13702. (OpenAlex-verified.)

**LLM introspection / self-report limits (cluster d — MUST CITE for the confabulation reframe):**
11. Binder, F. J., Chua, J., Korbak, T., Sleight, H., Hughes, J., Long, R., Perez, E., Turpin, M., & Evans, O. (2024). *Looking Inward: Language Models Can Learn About Themselves by Introspection.* arXiv:2410.13787. DOI: 10.48550/arXiv.2410.13787. (OpenAlex-verified.)
12. Betley, J., Bao, X., Soto, M., Sztyber, A., Chua, J., & Evans, O. (2025). *Tell me about yourself: LLMs are aware of their learned behaviors.* arXiv:2501.11120. DOI: 10.48550/arXiv.2501.11120. (OpenAlex-verified.)
13. Song, S., Hu, J. C. W., & Mahowald, K. (2025). *Language Models Fail to Introspect About Their Knowledge of Language.* arXiv:2503.07513. DOI: 10.48550/arXiv.2503.07513. (OpenAlex-verified.)
14. Comsa, I. M., & Shanahan, M. (2025). *Does It Make Sense to Speak of Introspection in Large Language Models?* arXiv:2506.05068. DOI: 10.48550/arXiv.2506.05068. (OpenAlex-verified.)

**Cross-model moral-choice comparison (cluster e — SHOULD CITE):**
15. Ding, J., Jiang, P., Xu, Z., Ding, Z., Zhu, Y., Jiang, J., & Li, Y. (2025). *'Pull or Not to Pull?': Investigating Moral Biases in Leading Large Language Models Across Ethical Dilemmas.* arXiv:2508.07284. DOI: 10.48550/arXiv.2508.07284. (OpenAlex-verified; author names as returned by OpenAlex.)

**Screened and judged NOT precedents (for the record):** forced-choice psychometric-format papers (A2/AX6); "Proof of Cognitive Divergence … Identical LLM Agents" (2026, Authorea — identical agents, not identical options); multi-model consensus *methods* papers (E2); the general confabulation/hallucination literature (AX11 — content confabulation, not choice-mechanism self-report); Buridan scholarship in philosophy (A1/AX1 — the classical source, already represented in the manuscript by Rescher, 1960).

---

## 5. The two manuscript references the build asked this search to verify

### 5.1 "Wang, Z., et al. (2025). B3Emo … IEEE Access" — RECORD FOUND, CITATION WRONG
The paper exists, but **not** as cited. Verified record (Crossref DOI lookup + Crossref search rank-1, 2026-11-03):

> Stepin, A., Mozikov, M., Kabanov, A., Kubasov, V., Akimov, R., Nasonov, I., Glazkov, N., Sultimov, R., Makovetskiy, I., Severin, N., Maximov, Y., Savchenko, A. V., & Makarov, I. (2026). *B3Emo: Quantifying Affect as a Double-Edged Sword in Strategic LLM Interactions.* IEEE Access, 14, 48127–48144. DOI: 10.1109/access.2026.3673221.

The 13-author list contains **no author named Wang**, and the year is **2026**, not 2025 (Crossref: published-print 2026; volume 14; pages 48127–48144; licence start 2026-01-01). **Action for the build:** either correct the entry to the Stepin et al. (2026) record above, or remove the citation. Do not retain "Wang, Z., et al. (2025)".

### 5.2 "Zhang et al., 2025" on justification inflation / conversational escalation — NO MATCHING RECORD FOUND
The manuscript (§5, Phenomenon 3) states: "studies of conversational escalation (Zhang et al., 2025) have documented emotional intensification in continuous dialogues." There is **no Zhang entry anywhere in the manuscript's reference list**. Searches run: Crossref V2 ("Zhang conversational escalation emotional intensification continuous dialogues 2025" — top 10 all unrelated, incl. a *Conversational AI* textbook's chapters) and V3 ("justification inflation large language model" — top 10 all economics "inflation" papers); the arXiv cluster searches (AX6–AX11) likewise returned nothing matching. **Conclusion: no genuine record matching this citation was found in this search. It must be treated as missing/unverifiable — removed, never completed by invention.** (Separately, the manuscript's discussion cites Park et al. (2025) for hidden conversational escalation; that record was not part of this verification task and should be verified on its own before reuse.)

---

## 6. Adjacent reference-list errors discovered during verification (for the W11 fix list)

Both were verified against OpenAlex DOI records on 2026-11-03:
- Manuscript: "Taves, J., et al. (2024). A comparison of large language model and human performance on random number generation tasks. arXiv:2408.09656." → The record is **Harrison, R. M. (2024), sole author**. There is no Taves on it.
- Manuscript: "Campajola, C., et al. (2025). Deterministic or probabilistic? … arXiv:2502.19965." → The record is **Coronado-Blázquez, J. (2025), sole author**. There is no Campajola on it.

---

## 7. Bottom line — what novelty phrasing this evidence supports, per cluster

- **(a) + (b) — the paradigm:** Supported: *"No direct precedent was found in a documented search of Crossref and arXiv (2026-11-03) for a study that places frontier LLMs in forced choices between options engineered to be logically indifferent, with indifference as the central experimental variable."* NOT supported: any claim that LLM choice behaviour under such conditions is wholly undocumented — token bias, selection bias and option-order sensitivity (Zheng et al. 2023; Pezeshkpour & Hruschka 2024; Wei et al. 2024; Wang et al. 2024) are documented, directly relevant mechanisms and must be cited as such.
- **(c) — tie-breaking / number selection:** The phenomenon (non-random, model-specific, cross-model-convergent arbitrary picks, incl. the pull toward 7 in 1–10) is **previously documented** (Harrison 2024; Coronado-Blázquez 2025; Karanjai et al. 2025). The manuscript may claim, at most, that no direct precedent was found in this search for a *cross-model taxonomy of the verbalised tie-breaking rules models announce* for such picks. "Bias Proximity Effect" survives only as a new label for behaviour inside a documented phenomenon class.
- **(d) — confabulated mechanism self-report:** Supported: *"No direct precedent was found in this search for a model's fabricated self-report of its choice mechanism (e.g., a system-clock procedure) inside a symmetry-choice task."* The confabulation *interpretation* must be presented as an application of the documented unfaithfulness/introspection-limits literature (Turpin et al. 2023; Lanham et al. 2023; Binder et al. 2024; Betley et al. 2025; Song et al. 2025; Comsa & Shanahan 2025), not as a novel theoretical move.
- **(e) — justification divergence under consensus:** Supported: *"No direct precedent was found in this search for cross-model divergence of stated justifications under identical forced choices."* Must be positioned next to unfaithful-explanation research (within-model reason/output divergence) and cross-model moral-choice comparisons (Ding et al. 2025).
- **General:** The original draft's novelty apparatus — the Perplexity-based classification, the "4 novel / 11 partially novel / **0 previously documented**" distribution, and unqualified "novel phenomenon" labels — is **contradicted by this search** for the selection-bias and random-number clusters and is unsupportable as a method. It should be deleted and replaced by the per-cluster sentences above, with this search (databases, strings, date) reported in the manuscript's methods/limitations so a reader can re-run it.

*Prepared 2026-11-03. Raw API logs: `crossref-search-log-2026-11-03.json`, `arxiv-search-log-2026-11-03.json`, `verified-records-2026-11-03.json` (same folder). Known limitation: OpenAlex search counts could not be obtained on the access date due to the API's shared-IP daily budget being exhausted (error recorded verbatim in §1); OpenAlex was used for record-level verification instead. Re-running the OpenAlex search strings in §2 after the budget reset is a cheap way to close that gap before submission.*
