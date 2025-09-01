---
layout: default
title: Data
nav_order: 3
---

# Data

---
## Subtask A - Term Extraction

Please refer to [Subtask A - Term Extraction](subtask_a.md) for more information about the dataset format.

- Training set ( [CSV]() \| [JSON]() ) (Coming soon)
- Development set  ( [CSV]() \| [JSON]() ) (Coming soon)
- Test set   ( [CSV]() \| [JSON]() ) (Coming soon)

---
## Subtask B - Term Variant Clustering

Please refer to [Subtask B - Term Variant Clustering](subtask_b.md) for more information about the dataset format.

- Training set  ( [CSV]() \| [JSON]() ) (Coming soon)
- Development set ( [CSV]() \| [JSON]() ) (Coming soon)
- Test set ( [CSV]() \| [JSON]() ) (Coming soon)

---
## License and attribution
The datasets available on this page are released under the [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/)

If you use the training and development datasets in a scientific publication, please cite:

```bibtex
@dataset{itaist_gru2025,
  author       = {Nicola Cirillo and
                  Daniela Vellutino and
                  David Nicoletti and
                  Enzagiulia Sabarese and
                  Benedetta Rubino},
  title        = {ItaIst\_GRU},
  month        = mar,
  year         = 2025,
  publisher    = {Zenodo},
  version      = {thesis},
  doi          = {10.5281/zenodo.15173712},
  url          = {https://doi.org/10.5281/zenodo.15173712},
}
```

---
## Data source
The training and development sets come from the publicly available ItaIst-TermRifiuti corpus and ItaIst-WasteLexicon termbase ([Cirillo et al., 2025](references.md)), while the test set is specifically designed for the ATE-IT shared task.

**ItaIst-TermRifiuti** is a stratified sample of the broader ItaIst-DdAC_GRU corpus (Italiano Istituzionale per il Diritto di Accesso Civico – Gestione Rifiuti Urbani) ([Vellutino & Cirillo, 2024](references.md)), consisting of institutional texts on municipal waste management.
It is balanced between administrative texts (e.g., ordinances, service charters, tenders) aimed at experts and informative texts (e.g., public notices, guides, press releases) for the general public.
This balance supports the analysis of terminological variation across different registers and audiences.
The corpus includes 622 paragraphs from 69 documents, 2,888 sentences and 41,333 words.
It is manually annotated by four trained annotators who identified all relevant terminological units and assigned them to one of several predefined domains: waste management, law/administration, waste management law/administration, environment, environmental law, and other.

The **ItaIst-WasteLexicon** termbase contains 950 selected terms from the ItaIst-TermRifiuti corpus.
It includes selected terms related to waste management, waste management law/administration, environment, and environmental law.
The terms are organised within a conceptual framework that links each term to its corresponding concept and encodes conceptual relations such as generic/specific and comprehensive/partitive.
Concepts are further enriched with definitions drawn from European and Italian legislation.

---
**GitHub repository:** [github.com/nicolaCirillo/ate-it](https://github.com/nicolaCirillo/ate-it)
