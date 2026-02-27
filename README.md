---
![](./docs/header.png)
---

# ATE-IT @ EVALITA

**ATE-IT** (Automatic Term Extraction - Italian Testbed) is a *shared task* organized within the framework of [**EVALITA 2026**](https://www.evalita.it/campaigns/evalita-2026/), the evaluation campaign for Natural Language Processing (NLP) systems for Italian.  

This repository hosts the official task website: 👉 [ATE-IT Website](https://nicolacirillo.github.io/ate-it/)  

## Repository Contents

- Task website
- Dataset
- Evaluation code
- Baseline code

## ATE-IT at a glance

- **Goal**: to evaluate *Automatic Term Extraction* systems for Italian, with the aim of identifying relevant terms in specific domains.  
- **Part of**: [EVALITA](http://www.evalita.it/), the evaluation campaign for NLP in Italian.  
- **Subtasks**:
  - *Term Extraction:* given a collection of Italian texts from specialised domains, automatically extract candidate terms and compare them against gold-standard term lists.  
  - *Term Variants Clustering:* given the list of terms extracted in the previous subtask, cluster together those terms that denote the same concept.  

## Attribution

If you use the ATE-IT datasets in a scientific publication, please cite:

```bibtex
@inproceedings{ateit2026overview,
title={ATE-IT at EVALITA 2026: Overview of the Automatic Term Extraction Italian Testbed Task},
author={Cirillo, Nicola and Di Nunzio, Giorgio Maria and Vezzani, Federica},
booktitle={Proceedings of the Ninth Evaluation Campaign of Natural Language Processing and Speech Tools for Italian. Final Workshop (EVALITA 2026)},
publisher = {CEUR.org},
year = {2026},
month = {February},
address = {Bari, Italy}
}
```
Training and development datasets are sourced from:

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

```bibtex
@phdthesis{cirillo2025tesi,
  author  = {Cirillo, Nicola},
  title   = {Risorse Linguistiche Digitali per la Transizione Verde},
  school  = {University of Salerno},
  year    = {2025},
  type    = {PhD Thesis},
}
```
## Resources

🔗 [Official Task Website](https://nicolacirillo.github.io/ate-it/)  
🔗 [EVALITA](http://www.evalita.it/)  

## License

The contents of this repository are released under the [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/).  

