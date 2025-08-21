---
layout: default
title: Home
---

# Overview

## Automatic Term Extraction (ATE)

**ATE** is a foundational task in NLP and terminology work. Its goal is to identify domain-specific **terms** that encapsulate key concepts within a specialised field of knowledge. It differs from Named Entity Recognition (NER) because the focus of ATE – the term – refers to a potentially unlimited number of objects, unlike the named entity that refers to unique objects. The terms extracted through ATE serve as essential building blocks for downstream tasks such as information retrieval, machine translation, ontology construction, knowledge graph enrichment, and domain adaptation of large language models (LLMs).

## The ATE-IT Shared Task

The ATE-IT shared task offers the first large-scale evaluation campaign on Italian ATE, centred on a clearly defined real-world scenario: terminology extraction from institutional texts in the domain of waste management. This domain presents a rich variety of derived terms (e.g., “ecodizionario”, “biodigestore”), synonyms (e.g., “indifferenziato” and “secco residuo”), abbreviations (“TARI”, “RAEE”), and multiword expressions (“mastello contenitore”, “raccolta porta a porta”), making it an important testbed for assessing the robustness of different approaches.
The ATE-IT shared task comprises two subtasks of increasing complexity: Term Extraction and Term Variants Clustering   .

### Subtask A - Term Extraction.

Participants will receive a set of sentences drawn from a specialised corpus related to municipal waste management. For each sentence, the goal is to identify and extract the terms that are relevant to the waste management domain. Terms may consist of single words (single-word terms) or multiword expressions (multi-word terms), including noun, verbs and adjectives.

### Subtask B - Term Variants Clustering.

From the list of unique extracted terms, participants are then required to cluster together those terms that refer to the same underlying concept. For example, “raccolta porta a porta” and “raccolta domiciliare” should be placed in the same cluster. Each cluster should represent a single, coherent concept within the waste management domain. This subtask focuses on synonymy, lexical variation, and compositional semantics.
Both subtasks are designed to be linguistically and computationally challenging. The first subtask requires models to generalize from sparse domain-specific training examples. The second requires semantic comparison and abstraction over morphologically and syntactically diverse variants.

---

## 📂 Sezioni
- [Progetti](projects.md)
- [Chi sono](about.md)
- [Contatti](contact.md)

---

## ℹ️ Info
Puoi personalizzare i contenuti modificando i file `.md` e la configurazione in `_config.yml`.

Per saperne di più, leggi la [guida ufficiale](https://docs.github.com/it/pages).
