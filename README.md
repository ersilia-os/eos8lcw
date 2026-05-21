# Antimicrobial activity prediction against Staphylococcus aureus from public ChEMBL and PubChem data

Bioactivity prediction of growth inhibition in Staphylococcus aureus, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL and PubChem. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (percent inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.



## Information
### Identifiers
- **Ersilia Identifier:** `eos8lcw`
- **Slug:** `antimicrobial-activity-saureus`

### Domain
- **Task:** `Annotation`
- **Subtask:** `Activity prediction`
- **Biomedical Area:** `Antimicrobial resistance`, `Pneumonia`
- **Target Organism:** `Staphylococcus aureus`
- **Tags:** `Gram-positive bacteria`, `ESKAPE`, `Antimicrobial activity`, `ChEMBL`

### Input
- **Input:** `Compound`
- **Input Dimension:** `1`

### Output
- **Output Dimension:** `95`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Staphylococcus aureus from 94 ChEMBL- and PubChem-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 94 sub-models. Recommended threshold: 0.963. |
| individual_inhibition | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4296184 (inhibition %; cutoff 25 %; n=3686). Recommended threshold: 0.775. |
| individual_mic_decoys_a | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL1640441 (MIC; cutoff 10 uM; n=1170 incl. decoys). Recommended threshold: 0.869. |
| individual_gi_decoys | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL4011044 (growth inhibition %; cutoff 50 %; n=1030 incl. decoys). Recommended threshold: 0.897. |
| individual_mic_decoys_b | float | high | Probability from sub-model trained on ChEMBL assay CHEMBL807231 (MIC; cutoff 20 uM; n=1010 incl. decoys). Recommended threshold: 0.919. |
| merged_iz_decoys_e | float | high | Probability from sub-model trained on IZ measurements merged across 12 ChEMBL assays (cutoff 10 mm; n=2280 incl. decoys). Recommended threshold: 0.896. |
| merged_mic_decoys_ai | float | high | Probability from sub-model trained on MIC measurements merged across 9 ChEMBL assays (cutoff 20 uM; n=2180 incl. decoys). Recommended threshold: 0.825. |
| merged_mic_decoys_ag | float | high | Probability from sub-model trained on MIC measurements merged across 9 ChEMBL assays (cutoff 20 uM; n=2170 incl. decoys). Recommended threshold: 0.863. |
| merged_mic_decoys_al | float | high | Probability from sub-model trained on MIC measurements merged across 8 ChEMBL assays (cutoff 10 uM; n=1980 incl. decoys). Recommended threshold: 0.833. |
| merged_mic_decoys_aj | float | high | Probability from sub-model trained on MIC measurements merged across 7 ChEMBL assays (cutoff 10 uM; n=1950 incl. decoys). Recommended threshold: 0.853. |

_10 of 95 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`

### Resource Consumption


### References
- **Source Code**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication**: [https://github.com/ersilia-os/chembl-antimicrobial-models](https://github.com/ersilia-os/chembl-antimicrobial-models)
- **Publication Type:** `Other`
- **Publication Year:** `2026`
- **Ersilia Contributor:** [arnaucoma24](https://github.com/arnaucoma24)

### License
This package is licensed under a [GPL-3.0](https://github.com/ersilia-os/ersilia/blob/master/LICENSE) license. The model contained within this package is licensed under a [GPL-3.0-or-later](LICENSE) license.

**Notice**: Ersilia grants access to models _as is_, directly from the original authors, please refer to the original code repository and/or publication if you use the model in your research.


## Use
To use this model locally, you need to have the [Ersilia CLI](https://github.com/ersilia-os/ersilia) installed.
The model can be **fetched** using the following command:
```bash
# fetch model from the Ersilia Model Hub
ersilia fetch eos8lcw
```
Then, you can **serve**, **run** and **close** the model as follows:
```bash
# serve the model
ersilia serve eos8lcw
# generate an example file
ersilia example -n 3 -f my_input.csv
# run the model
ersilia run -i my_input.csv -o my_output.csv
# close the model
ersilia close
```

## About Ersilia
The [Ersilia Open Source Initiative](https://ersilia.io) is a tech non-profit organization fueling sustainable research in the Global South.
Please [cite](https://github.com/ersilia-os/ersilia/blob/master/CITATION.cff) the Ersilia Model Hub if you've found this model to be useful. Always [let us know](https://github.com/ersilia-os/ersilia/issues) if you experience any issues while trying to run it.
If you want to contribute to our mission, consider [donating](https://www.ersilia.io/donate) to Ersilia!
