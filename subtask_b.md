---
layout: default
title: Subtask B – Term Variants Clustering
parent: Participation Guidelines
---

# Subtask B – Term Variants Clustering

---
## Overview

From the list of unique extracted terms, participants should cluster together those terms that refer to the same underlying concept.
For example, “raccolta porta a porta” and “raccolta domiciliare” should be placed in the same cluster.

- Each cluster should represent a single, coherent concept within the waste management domain.
- Inflected form of the same lemma should be clustered together (e.g. "isola ecologica" and "isole ecologiche" should be assigned to the same cluster)
- Acronyms, initialisms and full forms should be clustered together (e.g. "ccr" and "centro comunale di raccolta" should be assigned to the same cluster)
- Synonyms should be clustered together (e.g. "isola ecologica" and "centro comunale di raccolta" should be assigned to the same cluster)
- Hypernyms and iponyms should NOT be clustered together (e.g. "rifiuti" and "rifiuti indifferenziati" should be assigned to different clusters)

---
## Input

The system input will be a **CSV** or **JSON** file containing a list of terms.
Terms are inflected forms, not lemmas<br>
**Important:** The organizers do not provide the input file. Participants must use the list of unique terms extracted during [Subtask A].

---
### Example of CSV input file

```
term,
centro di raccolta,
ccr,
isola ecologica,
isole ecologiche,
indifferenziato,
secco residuo,

```

---
### Example of JSON input file

```json
{
  "data": [
    {
      "term": "centro di raccolta",
    },
    {
      "term": "ccr",
    },
    {
      "term": "isola ecologica",
    },
    {
      "term": "isole ecologiche",
    },
    {
      "term": "indifferenziato",
    },
    {
      "term": "secco residuo",
    }
  ]
}
```

---
## Output

The system output must also be a **CSV** or **JSON** file containing the assigned cluster for each term.


**Output requirements:**  
- Cluster should be represented as integer cluster IDs.

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
    {
      "term": "centro di raccolta",
      "cluster": 1,
    },
    {
      "term": "ccr",
      "cluster": 1,
    },
    {
      "term": "isola ecologica",
      "cluster": 1,
    },
    {
      "term": "isole ecologiche"
      "cluster": 1,
    },
    {
      "term": "indifferenziato"
      "cluster": 2,
    },
    {
      "term": "secco residuo"
      "cluster": 2,
    }
  ]
}
```

---
## Evaluation metrics

Performance in the Term Variants Clustering subtask will be measured using the **BCubed F1 score** (Amigó et al., 2009):

- The score will be computed in a way that makes it dependent on the results of the Term Extraction subtask 

---
### BCubed F1 score

BCubed F1 is calculAh, perfect — when you say *it must be the BCubed*, you’re pointing at the definitions from Bagga & Baldwin (1998): cluster evaluation with per–item precision and recall, then averaged across all items. Let’s rewrite properly in that spirit.

---

### BCubed Metrics 📊

Let:

* $N_{pred}$ = total number of elements in the predicted clustering
* $N_{gold}$ = total number of elements in the gold clustering
* $C(x)$ = the predicted cluster containing element $x$
* $L(x)$ = the gold cluster of element $x$

Then for each element $x$:

$$
P(x) \;=\; \frac{|\{ y \in C(x) : L(y) = L(x) \}|}{|C(x)|}
$$

$$
R(x) \;=\; \frac{|\{ y \in L(x) : C(y) = C(x) \}|}{|L(x)|}
$$

The global scores are averages over all items:

$$
\text{Precision} \;=\; \frac{1}{N_{pred}}\sum_{x=1}^N_{pred} P(x)
$$

$$
\text{Recall} \;=\; \frac{1}{N_{gold}}\sum_{x=1}^N_{gold} R(x)
$$

$$
F \;=\; \frac{2 \cdot \text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}
$$

