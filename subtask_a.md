---
layout: default
title: Subtask A – Term Extraction
parent: Participation Guidelines
---

# Subtask A – Term Extraction

---
## Overview

Participants receive a set of sentences drawn from a specialised corpus related to municipal waste management. For each sentence, the goal is to identify and extract the terms that are relevant to the waste management domain. Terms may consist of single words (single-word terms) or multiword expressions (multi-word terms), including nouns, verbs, and adjectives.

---
## Input

The system will receive as input a CSV or JSON file containing a list of sentences alongside their identifier. 

---
### Example of CSV input file


```
document_id,paragraph_id,sentence_id,sentence_text
doc_poggiomarino_02,8,1,"Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti."
doc_santagnello_19,3,2,"- Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)"
doc_nola_05,2,6,"Il ritiro “a domicilio” è attivo dal 01 aprile al 30 settembre, sarà effettuato ogni 15 giorni su prenotazione telefonica."
```

---
### Example of JSON input file

```json
{
  "data": [
    {
      "document_id": "doc_poggiomarino_02",
      "paragraph_id": 8,
      "sentence_id": 1,
      "sentence_text": "Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti."
    },
    {
      "document_id": "doc_santagnello_19",
      "paragraph_id": 3,
      "sentence_id": 2,
      "sentence_text": "- Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)"
    },
    {
      "document_id": "doc_nola_05",
      "paragraph_id": 2,
      "sentence_id": 6,
      "sentence_text": "Il ritiro “a domicilio” è attivo dal 01 aprile al 30 settembre, sarà effettuato ogni 15 giorni su prenotazione telefonica."
    }
  ]
}
```

---
## Output

The system must output a CSV or JSON file containing the extracted terms for each sentence alongside the corresponding identifiers. Extracted terms must not contain duplicates and must be only lowercased (lemmatisation or other modifications are not allowed). In the output file, the terms extracted from each sentence must be represented as a string and separated by a semicolon “;”.

**Important:** nested terms are NOT allowed.

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

The Term Extraction subtask is evaluated using:
- **MicroF1** score, which evaluates precision and recall across all term occurrences in the test set (Verborgh et al., 2018)
- **Type F1** score, which assesses the ability to identify unique term types correctly.

---
### Micro F1

Micro-averaged Precision is computed as in the following formulas, where $i$ is an item of the dataset $D$.

$$
\mathrm{Precision}_{\text{micro}}(\mathcal{D})
=
\frac{\sum_{i \in \mathcal{D}} \mathrm{TP}_i}
{\sum_{i \in \mathcal{D}} \left(\mathrm{TP}_i + \mathrm{FP}_i\right)}
$$
