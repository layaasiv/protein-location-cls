# Classifying proteins based on subcellular location using ESM2 and MLP

Classifying proteins by subcellular location (cytosol, membrane, nucleus) using ESM-2 protein language model embeddings and a custom PyTorch MLP.

## Tools & Technologies
- **Model:** ESM-2 (Facebook/Meta protein language model via HuggingFace)
- **Framework:** PyTorch
- **Data:** UniProt database
- **Libraries:** HuggingFace Transformers, NumPy, pandas, scikit-learn, Matplotlib

## Project Overview
Protein subcellular localization is critical to understanding protein function. This project explores whether sequence-level embeddings from a pretrained protein language model (ESM-2) contain sufficient information to classify proteins by their subcellular compartment, without any structural or experimental data.

ESM-2 embeddings are extracted for each protein sequence and passed through a lightweight MLP classifier trained to predict one of three localization classes.

## Notebooks
| Notebook | Description |
|---|---|
| `multiclass.ipynb` | 3-class classification: cytosol, membrane, nucleus |
| `cytosol_v_membrane.ipynb` | Binary classification: cytosol vs membrane |
| `nucleus_v_membrane.ipynb` | Binary classification: nucleus vs membrane |
| `nucleus_v_cytosol.ipynb` | Binary classification: nucleus vs cytosol |

## Results

### Binary Classification
| Task | Accuracy |
|---|---|
| Cytosol vs Membrane | ~0.90 |
| Nucleus vs Membrane | ~0.90 |
| Nucleus vs Cytosol | ~0.72 |

### Multiclass Classification
The multiclass model identifies membrane proteins with high precision and recall, but struggles to differentiate cytosolic from nuclear proteins.

| Class | Precision | Recall |
|---|---|---|
| Cytosol | 0.67 | 0.40 |
| Membrane | high | high |
| Nucleus | 0.67 | 0.87 |

![Confusion matrix](./imgs/multiclass_cm.png)
* 0 = cytosol, 1 = membrane, 2 = nucleus

## Key Findings
Membrane proteins are highly separable from other classes, likely due to their distinctive structural features including hydrophobic transmembrane regions and signal peptides. Cytosolic and nuclear proteins are harder to distinguish, which is biologically expected: many proteins shuttle between these compartments depending on cell state, and the nuclear localization signal (NLS) is short and highly variable. Database annotations may also introduce label noise, as localization is often context-dependent.

## Future Directions
- Multi-label classification to account for proteins with multiple localizations
- Top-2 accuracy evaluation as a more biologically appropriate metric
- Expanding to additional subcellular compartments

## Setup
```bash
pip install torch transformers numpy pandas scikit-learn matplotlib
```
Clone the repo and run any notebook in Jupyter or VS Code. Protein sequences are sourced from UniProt — links to the specific datasets are provided within each notebook.
