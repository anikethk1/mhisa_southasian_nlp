# MHISA: South Asian Name Matching with NLP

An exploratory name-matching workflow that combines curated name dictionaries, fuzzy string similarity, linguistic patterns, and pretrained name models to study South Asian name recognition. The notebook brings several imperfect signals together in a transparent, inspectable pipeline.

**[Explore the notebook](south_asian_nlp_mhisa.ipynb)**

## How it works

1. **Normalize and split names.** Convert dictionary entries to uppercase and separate an input's first and last tokens.
2. **Search the reference dictionaries.** Check exact matches, then combine RapidFuzz partial, token-sort, and full-string similarity scores. Weight these scores 50%, 30%, and 20%, respectively, with additional checks for short tokens and length differences.
3. **Add linguistic signals.** Score selected prefixes and letter patterns in first and last names.
4. **Apply model-based checks.** Use `ethnicolr` census surname statistics and its Wikipedia-trained name model, including the `Asian,IndianSubContinent` output, to refine candidate matches.
5. **Collect results.** The notebook includes an exploratory evaluation and a batch-processing example that writes selected matches to CSV.

## Repository contents

| File | Purpose |
| --- | --- |
| [south_asian_nlp_mhisa.ipynb](south_asian_nlp_mhisa.ipynb) | Matching functions, threshold experiments, and batch-processing workflow |
| [first.txt](first.txt) | First-name reference dictionary: 196 unique normalized entries |
| [last.txt](last.txt) | Surname reference dictionary: 190 unique normalized entries |

The main functions are `check_name_fuzzy`, which evaluates dictionary similarity, and `process_name`, which combines the matching stages into a boolean result. The notebook exposes the thresholds so the decision logic can be examined directly.

## Tools and interpretation

**Python · pandas · NumPy · RapidFuzz · ethnicolr · Jupyter Notebook**

This project demonstrates text normalization, approximate matching, heuristic feature design, and integration of pretrained models. A name-based prediction is an uncertain statistical association; it does not establish a person's ethnicity, nationality, language, or self-identified background.

## Author

Aniketh Kalagara.
