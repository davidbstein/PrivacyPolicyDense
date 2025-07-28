
# Online Appendix for _Building a Long Text Privacy Policy Corpus with Multi-Class Labels_

> **Note (2025-07-28) — these files contain raw expert annotations. We may augment this dataset with additional annotations from reviewers.**

## The `PrivacyPolicyLong` Dataset

This repository is an online appendix for the paper [Building a Long Text Privacy Policy Corpus with Multi-Class Labels](https://aclanthology.org/2025.acl-long.401/) (Marotta-Wurgler & Stein, ACL 2025), and contains the dataset described by that paper.

### Overview

The appendix is structured into three `.ndjson` files, which contain newline-separated JSON objects. 

---

### Files
#### `questions.ndjson`

> The 64 questions used to annotate the policies, grouped into 11 legal categories (e.g., CCPA, GDPR, Enforcement).

<details>
<summary>see details...</summary>
Each entry includes:

* `label`: A unique identifier for the question
* `category`: Legal domain (e.g., "CCPA")
* `question`: The text of the question
* `allow_multiselect`: Whether the question supports multiple answers
* `options`: List of answer options with display text and IDs
</details>

#### `privacy_policies.ndjson`

> Full text of the privacy policy for each website, including incorporated documents.

<details>
<summary>see details...</summary>
Each entry includes:

* `url`: The firm's domain
* `policy_documents`: A list of documents parsed from that website, each of which contains for fields:

  * `label`: Document identifier
  * `name`: Document title
  * `paragraphs`: List of paragraphs as markdown
  * `format`: Always `markdown`. The data follows a strict subset of the "commonmark" markdown specification.

Note that there are some artifacts in the markdown (e.g., parsed navbar links at the top of files). The indicies in `coding_values.ndjson` include those artifacts. 
</details>

#### `coding_values.ndjson`

> Human annotation for each (website, question) pair.

<details>
<summary>see details...</summary>
Each entry includes:
  
  * `url`: The firm's domain
  * `question`: Question label (per `questions.ndjson`)
  * `responses`: A list of coder responses
  
    * `coder_id`
    * `selected_option_labels`: Chosen answer option(s)
    * `reported_likert_confidence`: self-reported confidence on a 1-5 likert scale, where `1` is least confident and `5` is most confident. If the coder did not report confidence the value is recorded as `null`.
    * `highlighted_sentences`: A list of triples `[doc_id, paragraph_idx, sentence_idx]` referencing (`doc_id`s and indicies from `privacy_policies.nsjson`). Each triple denotes a sentence that the coders marked as relevant for the given question.
  * (PENDING)\[optional] `review_response`: contains the same fields as a single entry in `responses` and have `coder_id` set to `"REVIEW"`. These responses were added by the (law professor) authors after discussion with the expert annotators and secondary review of the policy and question. 

</details>

### Citation

If you use this dataset, please cite:

```
@inproceedings{marotta-wurgler-stein-2025-building,
    title = "Building a Long Text Privacy Policy Corpus with Multi-Class Labels",
    author = "Marotta-Wurgler, Florencia  and
      Stein, David",
    editor = "Che, Wanxiang  and
      Nabende, Joyce  and
      Shutova, Ekaterina  and
      Pilehvar, Mohammad Taher",
    booktitle = "Proceedings of the 63rd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)",
    month = jul,
    year = "2025",
    address = "Vienna, Austria",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.acl-long.401/",
    pages = "8156--8219",
    ISBN = "979-8-89176-251-0"
}
```

### License

This dataset is made available under the Open Data Commons Attribution License: http://opendatacommons.org/licenses/by/1.0/


<!-- a first draft of this README was generated using an LLM -->
