---
layout: default
title: Subtask A – Term Extraction
parent: Participation Guidelines
---

# Subtask A – Term Extraction

---
## Overview

Participants will receive a collection of sentences extracted from a specialised corpus on **municipal waste management**.  
The goal of this subtask is to identify and extract **domain-relevant terms** from each sentence.  

- Terms can be either **single-word** or **multi-word expressions**.  
- Accepted terms may include **nouns, verbs, or adjectives**.  
- Extracted terms must correspond to concepts within the waste management domain.

---
## Input

The input will be provided as a **CSV** or **JSON** file.  
Each entry corresponds to one sentence and contains the following fields:  

- `document_id` – identifier of the source document  
- `paragraph_id` – identifier of the paragraph within the document  
- `sentence_id` – identifier of the sentence  
- `sentence_text` – the full text of the sentence  

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

The system output must also be a **CSV** or **JSON** file containing the extracted terms for each sentence.  

**Output requirements:**  
- Terms must be **lowercased only** (no lemmatisation, stemming, or other transformations).  
- All extracted terms for a given sentence must be concatenated into a single string, separated by **semicolons (“;”)**.  
- **No duplicate terms** are allowed within the same sentence.  
- **Nested terms are not permitted** (e.g., if “impianto di trattamento rifiuti” is extracted, the inner term “trattamento rifiuti” must not be included).  

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
## Evaluation

Performance in the Term Extraction subtask will be measured using two complementary metrics:

- **Micro F1 score** – evaluates precision and recall across all **sentences** in the dataset.  
- **Type F1 score** – evaluates precision and recall across **unique term types**, disregarding frequency.  

---
### Micro F1 score

Micro-averaged F1 is calculated as follows.

Let:

* $$TP_s$$ = number of terms extracted from sentence $$s$$ that match the gold standard  
* $$FP_s$$ = number of terms extracted from sentence $$s$$ that do not match the gold standard  
* $$FN_s$$ = number of gold standard terms in sentence $$s$$ that were not extracted  

Then, micro-averaged precision and recall are defined as:

$$
Precision_{micro} = \frac{\sum_{s \in D} TP_s}{\sum_{s \in D} (TP_s + FP_s)}
$$

$$
Recall_{micro} = \frac{\sum_{s \in D} TP_s}{\sum_{s \in D} (TP_s + FN_s)}
$$

Finally, the Micro F1 score is:

$$
F1_{micro} = \frac{2 \cdot Precision_{micro} \cdot Recall_{micro}}{Precision_{micro} + Recall_{micro}}
$$

---
### Type F1 score

Type F1 is computed over the set of unique term types (i.e., distinct term forms that appear at least once in the dataset).

Let:

* $$TP$$ = number of extracted unique terms that appear in the gold set  
* $$FP$$ = number of extracted unique terms that do not appear in the gold set  
* $$FN$$ = number of gold unique terms that were not extracted  

Then:

$$
Precision = \frac{TP}{TP + FP}
$$

$$
Recall = \frac{TP}{TP + FN}
$$

Finally, the Type F1 score is:

$$
F1 = \frac{2 \cdot Precision \cdot Recall}{Precision + Recall}
$$
