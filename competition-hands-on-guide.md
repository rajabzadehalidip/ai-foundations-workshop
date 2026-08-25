# Hands-on lab: embeddings for competition research

Use the [OpenRouter Colab notebook](./competition-openrouter-embeddings-colab.ipynb) for the workshop version. It uses OpenRouter's OpenAI-compatible embeddings endpoint and includes PCA visualization, centroid classification, a review queue, and a confusion matrix.

## Learning objective

Students will compare keyword search with semantic embeddings, classify a small corpus using a human-labelled gold set, inspect uncertain cases, visualize the embedding space, and discuss why evaluation and source traceability matter.

The exercise uses short **paraphrases** of public competition-policy material. The texts are not presented as quotations or as legal findings. Students should open the linked official source before making any substantive claim.

## Suggested timing: 45–60 minutes

1. **5 min — Frame the question**
   “Can a lightweight AI workflow help us organize competition-policy material without replacing researcher judgment?”
2. **10 min — Run the baseline**
   Use TF–IDF keyword similarity to classify the test rows.
3. **15 min — Run embeddings**
   Use the OpenRouter embedding model and nearest-centroid classification.
4. **10 min — Inspect uncertainty**
   Read the lowest-confidence cases. Decide whether the category definition, the gold set, or the model is the problem.
5. **10 min — Debrief**
   Compare accuracy, errors, omissions, and traceability. Discuss whether a researcher would accept the output for screening, drafting, or final analysis.

## Student task

Classify each test paragraph into one of these categories:

- `entry_barrier`
- `self_preferencing`
- `switching_cost`
- `exclusive_dealing`
- `merger_effect`
- `consumer_harm`
- `remedy`
- `market_definition`
- `other`

The `gold` rows are the labelled examples. The `test` rows are what the workflow must classify. In a real project, researchers—not the model—should define the labels and review the gold set.

## Questions for discussion

- Which categories are semantically close and most easily confused?
- What happens if the gold set contains only one writing style or one jurisdiction?
- Which errors are acceptable for document triage, and which are unacceptable in a published memo?
- How would you add page numbers, quotations, or document IDs to preserve traceability?
- Would you use embeddings for final legal/economic conclusions? Why not?

## Real-world source note

The corpus is built from short paraphrases inspired by public materials from the U.S. Department of Justice, Federal Trade Commission, UK Competition and Markets Authority, and European Commission. These links are starting points for reading, not substitutes for the underlying documents:

- [DOJ Apple antitrust case](https://www.justice.gov/opa/pr/justice-department-sues-apple-monopolizing-smartphone-markets)
- [FTC Google search case materials](https://www.ftc.gov/legal-library/browse/cases-proceedings/181-1017-google-search)
- [CMA cloud services market investigation](https://www.gov.uk/government/publications/cloud-services-market-investigation)
- [European Commission Digital Markets Act](https://digital-markets-act.ec.europa.eu/index_en)
- [European Commission merger policy](https://competition-policy.ec.europa.eu/mergers_en)
- [FTC guide to antitrust laws](https://www.ftc.gov/advice-guidance/competition-guidance/guide-antitrust-laws)

## Facilitator note

The dataset is intentionally small. The pedagogical point is not to claim that 27 rows represent a real market. The point is to make the workflow visible: define categories, create a gold set, embed, classify, inspect uncertainty, and evaluate. For a follow-up lab, replace the paraphrases with a carefully licensed or public-domain collection of paragraphs from one jurisdiction and preserve document/page metadata.

For the API demonstration, create a temporary OpenRouter key, set a small usage limit, and delete or rotate it after class. Students should not place keys directly in notebook cells or upload confidential documents.
