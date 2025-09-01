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
- **No duplicate terms** are allowed within the same sentence.  
- **Nested terms are not permitted** (e.g., if “impianto di trattamento rifiuti” is extracted, the inner term “trattamento rifiuti” must not be included, unless it also appears independently).  

---
### Example of CSV output file

```
document_id,paragraph_id,sentence_id,sentence_text,term
doc_poggiomarino_02,8,1,"Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.",centro di raccolta
doc_poggiomarino_02,8,1,"Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.",isola ecologica
doc_poggiomarino_02,8,1,"Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.",discarica
doc_poggiomarino_02,8,1,"Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.",impianto di trattamento rifiuti
doc_santagnello_19,3,2,"- Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)", tari
doc_santagnello_19,3,2,"- Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)",tassa rifiuti
doc_nola_05,2,6,"Il ritiro “a domicilio” è attivo dal 01 aprile al 30 settembre, sarà effettuato ogni 15 giorni su prenotazione telefonica.",ritiro a domicilio
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
      "sentence_text": "Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.",
      "term_list": ["centro di raccolta", "isola ecologica", "discarica", "impianto di trattamento rifiuti"]
    },
    {
      "document_id": "doc_santagnello_19",
      "paragraph_id": 3,
      "sentence_id": 2,
      "sentence_text": "- Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)",
      "term_list": ["tari", "tassa rifiuti"]
    },
    {
      "document_id": "doc_nola_05",
      "paragraph_id": 2,
      "sentence_id": 6,
      "sentence_text": "Il ritiro “a domicilio” è attivo dal 01 aprile al 30 settembre, sarà effettuato ogni 15 giorni su prenotazione telefonica.",
      "term_list": ["ritiro a domicilio"]
    }
  ]
}
```

---
## Evaluation

Performance in the Term Extraction subtask will be measured using two complementary metrics:

- **Micro F1 score** ([Verborgh et al., 2018](references.md)) – evaluates precision and recall across all **sentences** in the dataset.  
- **Type F1 score** – evaluates precision and recall across **unique term types**, disregarding frequency.  

The code used for the evaluation is available to participants ([Subtask A - Evaluation Notebook](https://colab.research.google.com/github/nicolaCirillo/ate-it/blob/main/evaluation/subtask_a_evaluation.ipynb)).

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

---
## Baseline

We provide a baseline that participants are encouraged to improve upon. It is built on the latest Gemini model (`gemini-2.5-flash`) in a **zero-shot setup**.
Namely, we provided Gemini the following prompts and processed the sentences in batches of 20.

**System prompt:**
```
You are an automatic term extraction agent. You will receive a list of sentences as input.
Your role is to extract waste management terms from the sentences. Output a list of terms for each sentence.

strictly adhere to the Example Output Format:

Example Output Format:
Sentence 1: [term1; term2; term3; term4]
Sentence 2: [term5; term6]
Sentence 3: []
Sentence 4: []
Sentence 5: [term7]


Instructions: 
* Extract only terms, ignore named entities; 
* Do not extract nested terms; 
* Extract only terms related to waste management, ignoring other domains; 
* If a sentence contains no terms, output an empty list for that sentence; 
* You must output 20 lists of terms, one for each sentence.
```
**User prompt:**
```
Sentence 1: Il Centro di Raccolta [Isola Ecologica] non è una discarica e non è un impianto di trattamento rifiuti.

Sentence 2: - Pagare la Tassa Rifiuti (TARI) mediante il canale pagoPA (carte di credito e circuiti bancari)

[...]

Sentence 20:  Il ritiro “a domicilio” è attivo dal 01 aprile al 30 settembre, sarà effettuato ogni 15 giorni su prenotazione telefonica.
```

**Baseline code:** ([Subtask A - Baseline Notebook](https://colab.research.google.com/github/nicolaCirillo/ate-it/blob/main/baseline/subtask_a_baseline.ipynb)).
