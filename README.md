# Antimicrobial activity prediction against Staphylococcus aureus from public ChEMBL and PubChem data

Bioactivity prediction of growth inhibition in Staphylococcus aureus, trained as binary (active/inactive) classifiers from publicly available data in ChEMBL and PubChem. Independent models are trained on multiple bioactivity datasets, corresponding to single-point (Inhibition) and dose-response (MIC) assays, among others. A ranking score is provided for each model alongside a combined consensus score.

This model was incorporated on 2026-05-19.Last packaged on 2026-07-22.

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
- **Output Dimension:** `19`
- **Output Consistency:** `Fixed`
- **Interpretation:** Probability of antimicrobial activity against Staphylococcus aureus from 18 ChEMBL- and PubChem-trained sub-models, plus a quality-weighted consensus score.

Below are the **Output Columns** of the model:
| Name | Type | Direction | Description |
|------|------|-----------|-------------|
| consensus_score | float | high | Tanh-transformed quality-weighted consensus probability across the 18 sub-models. Recommended threshold: 0.791. |
| chembl_single_point_0 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 257 assays (2660 compounds). Recommended threshold: 0.779. |
| chembl_single_point_1 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 191 assays (1861 compounds). Recommended threshold: 0.589. |
| chembl_single_point_2 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 154 assays (1775 compounds). Recommended threshold: 0.638. |
| chembl_single_point_3 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 79 assays (1058 compounds). Recommended threshold: 0.684. |
| chembl_single_point_4 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 69 assays (981 compounds). Recommended threshold: 0.586. |
| chembl_single_point_5 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 106 assays (959 compounds). Recommended threshold: 0.747. |
| chembl_single_point_6 | float | high | Probability from sub-model trained on ChEMBL single-point signal-based pool of 11 assays (266 compounds). Recommended threshold: 0.608. |
| chembl_dose_response_0 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 2733 assays (29133 compounds). Recommended threshold: 0.665. |
| chembl_dose_response_1 | float | high | Probability from sub-model trained on ChEMBL dose-response signal-based pool of 1546 assays (14627 compounds). Recommended threshold: 0.612. |

_10 of 19 columns are shown_
### Source and Deployment
- **Source:** `Local`
- **Source Type:** `Internal`
- **DockerHub**: [https://hub.docker.com/r/ersiliaos/eos8lcw](https://hub.docker.com/r/ersiliaos/eos8lcw)
- **Docker Architecture:** `AMD64`, `ARM64`
- **S3 Storage**: [https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos8lcw.zip](https://ersilia-models-zipped.s3.eu-central-1.amazonaws.com/eos8lcw.zip)

### Resource Consumption
- **Model Size (Mb):** `1013`
- **Environment Size (Mb):** `7208`
- **Image Size (Mb):** `8190.87`

**Computational Performance (seconds):**
- 10 inputs: `65.31`
- 100 inputs: `61.89`
- 10000 inputs: `-1`

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
