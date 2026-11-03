# Glandular and Stromal Concept Activations Associated with Biochemical Recurrence in Prostatectomy Whole-Slide Images

Analysis code for the ISBI 2027 submission of the same title.

The notebook applies the GECKO concept-guided pipeline (Kapse et al., arXiv:2504.01009) to H&E radical prostatectomy whole-slide images. It covers:

- **Concept activations:** 25 pathologist-defined glandular and stromal concepts, scored as CONCH image–text similarity on patches inside annotated cancer regions.
- **Cohort-adjusted analysis:** each concept's activation compared between BCR+ and BCR− slides, with Hedges' g, permutation p-values and Benjamini–Hochberg q-values.
- **Prognostic evaluation:** cross-validation with GECKO retrained in every fold, followed by a linear probe on slide-mean activations.
- **Spatial maps:** exact patch-level decomposition of the probe's BCR logit.

## Data

Patient slides, labels and derived features are **not** included. They come from an institutional cohort and cannot be shared. Before running, set these placeholders in the notebook's first cell to your own directories:

| Placeholder | Contents |
|---|---|
| `<DATA_ROOT>` | patch features, concept activations, labels and fold splits |
| `<SLIDE_ROOT>` | whole-slide images, only needed for the map figures |
| `<GECKO_CODE_DIR>` | a local clone of the GECKO code |

The concept prompt file is expected at `<DATA_ROOT>/concept_prompts.json`.

## Requirements

Python 3.11 with PyTorch, NumPy, pandas, scikit-learn, SciPy, matplotlib and OpenSlide. You also need the CONCH weights (Lu et al., Nat. Med. 2024) and the GECKO code.
