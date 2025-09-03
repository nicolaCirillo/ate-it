---
layout: default
title: Subtask B – Term Variants Clustering
parent: Participation Guidelines
---

# Subtask B – Term Variants Clustering

---
## Overview

From the list of unique extracted terms, **participants must cluster together those terms that refer to the same underlying concept**.  
For example, *“raccolta porta a porta”* and *“raccolta domiciliare”* should be placed in the same cluster.

- Each cluster should represent a single concept within the waste management domain.
- Inflected forms of the same lemma should be clustered together (e.g. *“isola ecologica”* and *“isole ecologiche”*).
- Acronyms, initialisms, and their full forms should be clustered together (e.g. *“ccr”* and *“centro comunale di raccolta”*).
- Synonyms should be clustered together (e.g. *“isola ecologica”* and *“centro comunale di raccolta”*).
- Hypernyms and hyponyms should **not** be clustered together (e.g. *“rifiuti”* and *“rifiuti indifferenziati”* must be assigned to different clusters).

---
## Input

The input is a **CSV** or **JSON** file containing a list of terms.
These terms are inflected forms, not lemmas.  

👉 **Important:** The organizers will not provide the input file. Participants must use the list of unique terms extracted during [Term Extraction](subtask_a.md).

---
## Output

The system output must also be a **CSV** or **JSON** file, where each term is assigned to a cluster.

**Output requirements:**  
- Each cluster must be represented by an integer cluster ID.

---
### Example of CSV output file

```
term,cluster
centro di raccolta,1
ccr,1
isola ecologica,1
isole ecologiche,1
indifferenziato,2
secco residuo,2
```

---
### Example of JSON output file

```json
{
  "data": [
    { "term": "centro di raccolta", "cluster": 1 },
    { "term": "ccr", "cluster": 1 },
    { "term": "isola ecologica", "cluster": 1 },
    { "term": "isole ecologiche", "cluster": 1 },
    { "term": "indifferenziato", "cluster": 2 },
    { "term": "secco residuo", "cluster": 2 }
  ]
}
```

---
## Evaluation
Performance in the Term Variants Clustering subtask will be measured using the **BCubed F1 score** ([Bagga & Baldwin, 1998](references.md); [Amigó et al., 2009](references.md)).  

The code used for evaluation is available to participants ([Subtask B - Evaluation Notebook](https://colab.research.google.com/github/nicolaCirillo/ate-it/blob/main/evaluation/subtask_b_evaluation.ipynb))

---
### BCubed F1 score

BCubed evaluates clustering quality by computing precision and recall at the item level and then averaging across all items.

👉 **Important** In this version of BCubed, the set of items in the predicted clustering does not necessarily correspond to the set of items in the gold clustering.

Let:

* $$N_{pred}$$ = elements in the predicted clustering  
* $$N_{gold}$$ = elements in the gold clustering  
* $$C(x)$$ = the predicted cluster containing element $$x$$ (if $$x$$ is not in the predicted clustering, $$C(x)=\emptyset$$)
* $$L(x)$$ = the gold cluster containing element $$x$$ (if $$x$$ is not in the gold clustering, $$L(x)=\emptyset$$)

For each element $$x$$:

$$
P(x) = \frac{|\{ y \in C(x) : L(y) = L(x) \}|}{|C(x)|}
$$

$$
R(x) = \frac{|\{ y \in L(x) : C(y) = C(x) \}|}{|L(x)|}
$$

The global scores are averages over all items:

$$
Precision = \frac{1}{N_{pred}} \sum_{x=1}^{N_{pred}} P(x)
$$

$$
Recall = \frac{1}{N_{gold}} \sum_{x=1}^{N_{gold}} R(x)
$$

$$
F1 = \frac{2 \cdot Precision \cdot Recall}{Precision + Recall}
$$


## Baseline

**Baseline code:** ([Subtask B - Baseline Notebook](https://colab.research.google.com/github/nicolaCirillo/ate-it/blob/main/baseline/subtask_b_baseline.ipynb)

We provide a baseline that participants are encouraged to improve upon. It is built on the latest Gemini model (`gemini-2.5-flash`) in a **zero-shot setup**.
Namely, we provided Gemini the following prompts and processed the unique terms in batches of 20:

**System prompt:**
```
You are a term clustering agent.
You will receive a list of term clusters and a list of unclustered terms related to municipal waste management.
Your task is to cluster together exact synonyms.
Each cluster must represent a single, well-defined concept.

Output:
Return the list of clusters with the newly added terms. Each cluster must be on a new line.

Example Output:

term1; term2
term3
term4; term5; term7
term6; term8

Instructions:
* Group terms by meaning, not form. Use their lemma.
* Focus on their meaning within the municipal waste management context.
* If a term does not belong to an existing cluster, create a new cluster.
```

**User prompt:**
```
CLUSTERS:
centro di raccolta; ccr; isola ecologica; isole ecologiche
[...]
indifferenziato


UNCLUSTERED TERMS:
secco residuo
```

---
### Baseline score

| Dataset | BCubed-Precision | BCUbed-Recall | BCubed-F1 | 
| ------- | ---------------- | ------------- | --------- |
| dev     | 0.172            | 0.537         | 0.260     |
