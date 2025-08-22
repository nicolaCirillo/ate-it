---
layout: default
title: Subtask A – Term Extraction
parent: Participation Guidelines
---

# Subtask A – Term Extraction

---
## Overview

Participants will be provided with a collection of sentences taken from a specialised corpus on **municipal waste management**.  
The objective is to identify and extract **domain-relevant terms** from each sentence.  

- Terms can be either **single-word** or **multi-word expressions**.  
- Accepted terms may include **nouns, verbs, and adjectives**.  
- Extracted terms must correspond to concepts in the waste management domain.

---
## Input

The system input will be a **CSV** or **JSON** file.  
Each entry corresponds to a sentence and includes:  

- `document_id` – identifier of the source document  
- `paragraph_id` – identifier of the paragraph within the document  
- `sentence_id` – identifier of the sentence  
- `sentence_text` – the text of the sentence itself  

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

