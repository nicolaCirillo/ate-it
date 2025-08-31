---
layout: default
title: Participation Guidelines
has_children: true
nav_order: 2
---

# Participation Guidelines

---
## How to participate

**Participation is open to all NLP practitioners worldwide**: students, researchers, and industrial teams. You may join as an individual or as part of a team.

To register, please send an email to **ateit@gmail.com** with the following information:
- Group name and acronym
- Participants’ full names and affiliations
- Contact email address(es)
- Subtask(s) you wish to participate in
- *Optional:* Discord username(s)

👉 **Important:** At least one author of each accepted paper must register for the EVALITA conference in Bari (with a workshop fee) and present their work during the ATE-IT workshop.

---
## Program

The shared task consists of four consecutive phases:

- **Phase 1: Development (22 September – 2 November)**  
  Training and development data will be released on the [Data](data.md) page. Teams should design, implement, and test their system(s) for one or both subtasks using the provided data.

- **Phase 2: Evaluation (3 – 17 November)**  
  Test data will be released on the [Data](data.md) page. Teams must generate predictions and submit results in the required format. Submissions must also include a link to the source code repository on GitHub.

- **Phase 3: Reporting (18 November – 15 December)**  
  Teams must write and submit a short technical report following the provided format. The report should describe the system(s) and include:
  - System architecture and methods
  - Resources and pretrained models used
  - Results and error analysis

- **Phase 4: Final Workshop (26 – 27 February 2026 in Bari)**  
  Teams will present and discuss their work during the ATE-IT workshop at EVALITA.

---
## Rules

**There are no restrictions on techniques:** supervised and unsupervised machine learning, rule-based systems, deep learning, prompting, etc. Every technique is allowed.  
However, please note the following recommendations:

- We discourage simple fine-tuning of the latest models without additional **qualitative analysis**.  
- We strongly encourage the development of techniques that not only achieve good results but also provide **insights into Automatic Term Extraction (ATE) and terminology research**, thereby contributing to advancing the field. In particular, we encourage:
  - **the use of open-source LLMs**
  - **the exploitation of linguistic knowledge**

**Allowed external resources include (but are not limited to):**
- pretrained embeddings
- large language models (LLMs)
- tokenizers, lemmatizers, POS taggers, etc.
- other pretrained models
- lexical resources
- external corpora
- terminology resources

*All external resources must be clearly documented in the team’s technical report.*

**Participation options:**  
Teams may choose to participate in:
- **Subtask A (Term Extraction) only**, or  
- **Both Subtask A and Subtask B**  

⚠️ Participation in **Subtask B only (Term Variants Clustering)** is **not allowed**.


**Submission rules:**  
- Each team may submit up to **2 runs per subtask**.  
- For ranking, only the **best run per evaluation metric** will be considered.  

Both training and development data may be used to train models.<br>  
🚫 **Using test data for training is strictly forbidden.**


### Manual runs

We also accept runs where the test data is **manually annotated**.

Such runs must be **thoroughly documented** in the technical report. The report should include:
- the annotators’ level of expertise  
- the annotation guidelines provided  
- the tools used for annotation  
- inter-annotator agreement measures  

Manual runs will be used to compare ATE systems against human performance.<br>  
👉 They will **not** be used for official ranking.
