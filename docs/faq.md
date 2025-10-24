---
layout: default
title: FAQ
nav_order: 7
---

# FAQ

---

**Why do I see inconsistencies in the annotation of the training and development datasets?**

**Answer:** The annotation variations are intentionally retained to provide a realistic manual annotated dataset.
These variations reflect the real-world complexity of specialized terminology.
This approach ensures that participating systems are robust and can generalize to real-world data, not just to perfectly clean benchmarks.

---

**Why are some objects not annotated as terms (e.g., posate, musicassette, cocci di ceramica), while others are (e.g., pannolini)?**

**Answer:** This is a crucial distinction based on the terminological focus of the ATE task.
We follow the principle that only waste fractions (categories of waste to be collected/managed) and concepts with a specific technical meaning within the waste management domain are annotated as terms.

---

**Why are verbs annotated as terms in the dataset?**

**Answer:** In the field of Automatic Term Extraction (ATE) and Terminology, a term is defined as an expression that designates a key concept within a specific domain, regardless of its grammatical category.	
In the domain of waste management, many crucial concepts are processes or actions (e.g., to dispose of, to collect, to recycle).
Consequently, verbs and verb-based expressions are annotated as terms when they have a specific technical meaning in the context of urban waste management.	

---

**Will the full source documents or additional materials be provided with the test set?**

**Answer:** No. For the evaluation phase, the test set will consist only of the sentences required for the task (as defined in the input specification of [Subtask A](subtask_a) and [Subtask B](subtask_b)).
