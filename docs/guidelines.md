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

**Registration deadline:** 21 November, 2025

To register, please compile the CfI form at the following [link](https://docs.google.com/forms/d/e/1FAIpQLSdKLnMNzds1oaGwPYOVB7FTbmzWTqhTG5fWdsh6lozzdmVPnQ/viewform?usp=dialog) and send an email to [ateit.info@gmail.com](mailto:ateit.info@gmail.com) with the subject line **“ATE-IT Team Registration”**, including the following details:
- Group name and acronym
- Participants’ full names and affiliations
- Contact email address(es)
- Subtask(s) you wish to participate in
- *Optional:* Discord username(s)

👉 **Important:** At least one author of each accepted paper must register for the EVALITA conference in Bari (with a workshop fee) and present their work during the ATE-IT workshop.

💬 **Looking for a team?** Join our [official Discord server](https://discord.gg/7MBGSJQzT7), introduce yourself, and connect with fellow participants!

---
## Program
**Detailed program:** [Key Dates](dates.md)

The shared task consists of four consecutive phases.

- **Phase 1: Development (22 September – 23 November, 2025)**  
  Training and development data will be released on the [Data](data.md) page.
  Teams should design, implement, and test their system(s) for one or both subtasks using the provided data.

- **Phase 2: Evaluation (24 November – 1 December, 2025)**  
  Test data will be released on the [Data](data.md) page.
  Teams must generate predictions and submit results in the format required for each subtask ([Subtask A - Output](subtask_a.md#Output), [Subtask B - Output](subtask_b.md#Output)). We also encourage participants to include a link to the source code repository on GitHub.

- **Phase 3: Reporting (15 December, 2025 – 16 February, 2026)**
  Teams must write and submit a short technical report following the provided format.
  The report should describe the system(s) and include:
  - System architecture and methods
  - Resources and pretrained models used
  - Results and error analysis

- **Phase 4: Final Workshop (26 – 27 February, 2026; in Bari)**  
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
- tokenisers, lemmatisers, POS taggers, etc.
- other pretrained models
- lexical resources
- external corpora
- terminology resources

*All external resources must be clearly documented in the team’s technical report.*

**Participation options:**  
Teams may choose to participate in:
- **Subtask A (Term Extraction) only**, or  
- **Both Subtask A and Subtask B**
- Participation in **Subtask B only (Term Variants Clustering)** is **not allowed**.


**Submission rules:**  
- Each team may submit up to **2 runs per subtask**.  
- For ranking, only the **best run per evaluation metric** will be considered.  

Both training and development data may be used to train models.<br>
**Using test data for training is strictly forbidden.**

---
### Manual runs

We also accept runs where the test data is **manually annotated**.

Such runs must be **thoroughly documented** in the technical report. The report should include:
- the annotators’ level of expertise  
- the annotation guidelines provided  
- the tools used for annotation  
- inter-annotator agreement measures  

They will be used to compare ATE systems against human performance.<br>  
👉 **Important:** Manual runs will **not** be used for official ranking.

---
## Submission

**Submition deadline:** *December 1, 2025*

All submissions should be sent by email to [ateit.info@gmail.com](mailto:ateit.info@gmail.com) with the subject line **“ATE-IT Submission”**. Please attach your files in **CSV** or **JSON** format, following the specifications required for each subtask ([Subtask A - format specification](subtask_a.md#Output), [Subtask B - format specification](subtask_b.md#Output)). 
Include the following information in the body of the email:

- Group name and acronym
- Subtask(s) addressed
- Short description of your system (about 300 words)
- Contact email address(es)
- *Optional:* Link to the GitHub repository

Please ensure that your files are named consistently using the format:

```
[group_acronym]_[subtask_letter]_[runID].csv
[group_acronym]_[subtask_letter]_[runID].json
```
