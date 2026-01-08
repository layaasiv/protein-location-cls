# Classifying proteins based on subcellular location using ESM2 and MLP

## Overview 
Using ESM2 tokenizer and encoder to embed protein sequences, and a small MLP to classify proteins by subcellular location (multiclass classification). 

## Data
Derived from UniProt database. 

Labels: cytosol, membrane, nucleus.

## Findings 
The model is able to identify and differentiate membrane proteins from the other 2 classes; it shows high precision and recall for these proteins. However, it struggles to differentiate between cytosolic and nuclear proteins. Cytosolic proteins show low precision and recall (0.67; 0.40), while nuclear proteins have a reasonably high recall (0.87) and low precision (0.67). Thus, the model misclassifies cytosolic proteins as nuclear at a high rate. 

## Conclusions
