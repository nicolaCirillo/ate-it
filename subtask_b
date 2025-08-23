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
      "term": "ccr"
    },
    {
      "term": "isola ecologica",
    },
    {
      "term": "isole ecologiche"
    },
    {
      "term": "indifferenziato"
    }
  ]
}
```

---
## Output

The system output must also be a **CSV** or **JSON** file containing the extracted terms for each sentence.  

**Output requirements:**  
- Terms must be **lowercased only** (no lemmatisation, stemming, or other transformations).  
- Each sentence’s extracted terms must be concatenated into a single string and separated by a **semicolon (“;”)**.  
- No duplicates are allowed.
- **Nested terms are not permitted** (e.g., if “impianto di trattamento rifiuti” is extracted, the inner term “trattamento rifiuti” must not appear).

---
### Example of CSV output file

```
document_id,paragraph_id,sentence_id,term_list
doc_poggiomarino_02,8,1,"centro di raccolta; isola ecologica; discarica; impianto di trattamento rifiuti"
doc_santagnello_19,3,2,"tari; tassa rifiuti"
doc_nola_05,2,6,"ritiro a domicilio"
```

---
### Example of JSON output file

```json
{
  "data": [
    {
      "document_id": "doc_poggiomarino_02",
      "paragraph_id": 8,
      "sentence_id": 1,
      "term_list": "centro di raccolta; isola ecologica; discarica; impianto di trattamento rifiuti"
    },
    {
      "document_id": "doc_santagnello_19",
      "paragraph_id": 3,
      "sentence_id": 2,
      "term_list": "tari; tassa rifiuti"
    },
    {
      "document_id": "doc_nola_05",
      "paragraph_id": 2,
      "sentence_id": 6,
      "term_list": "ritiro a domicilio"
    }
  ]
}
```

---
## Evaluation metrics

Performance in the Term Extraction subtask will be measured using two complementary metrics:

- **Micro F1 score** – evaluates precision and recall across all **term occurrences** in the dataset.  
- **Type F1 score** – evaluates precision and recall across **unique term types** only (ignoring frequency).  

---
### Micro F1 score

Micro-averaged F1 is calculated as follows, where $$i$$ is an item of the dataset $$\mathcal{D}$$:

$$
\mathrm{Precision}_{\text{micro}}(\mathcal{D}) = \frac{\sum_{i \in \mathcal{D}} \mathrm{TP}_i} {\sum_{i \in \mathcal{D}} (\mathrm{TP}_i + \mathrm{FP}_i)}
$$

$$
\mathrm{Recall}_{\text{micro}}(\mathcal{D}) = \frac{\sum_{i \in \mathcal{D}} \mathrm{TP}_i} {\sum_{i \in \mathcal{D}} (\mathrm{TP}_i + \mathrm{FN}_i)}
$$

$$
F1_{\text{micro}}(\mathcal{D}) = \frac{2 \cdot \mathrm{Precision}_{\text{micro}}(\mathcal{D}) \cdot \mathrm{Recall}_{\text{micro}}(\mathcal{D})} {\mathrm{Precision}_{\text{micro}}(\mathcal{D}) + mathrm{Recall}_{\text{micro}}(\mathcal{D})}
$$

---
### Type F1 score

Type F1 is calculated over the set of unique terms (that appear at least in one document)

$$
\mathrm{Precision} = \frac{\mathrm{TP}}{\mathrm{TP} + \mathrm{FP}}
$$

$$
\mathrm{Recall} = \frac{\mathrm{TP}}{\mathrm{TP} + \mathrm{FN}}
$$

$$
F1 = \frac{2 \cdot \mathrm{Precision} \cdot \mathrm{Recall}}{\mathrm{Precision} + \mathrm{Recall}}
$$
