
# SFCSyntheticDataGenerator

## A Synthetic Data Generation System for ME/CFS Questionnaires

### 📄 About the Project

This repository hosts the implementation of the synthetic data generation system described in the paper **“A synthetic data generation system for myalgic encephalomyelitis/chronic fatigue syndrome questionnaires”**, published in *Scientific Reports* (Nature Portfolio):

> Lacasa, M., Prados, F., Alegre, J. & Casas-Roma, J.  
> *A synthetic data generation system for myalgic encephalomyelitis/chronic fatigue syndrome questionnaires.*  
> Sci Rep 13, 14256 (2023).  
> https://doi.org/10.1038/s41598-023-40364-6

Myalgic Encephalomyelitis/Chronic Fatigue Syndrome (ME/CFS) is a complex, multisystem illness where large datasets are scarce due to privacy restrictions and the lack of specific biomarkers.  
This project addresses the data scarcity problem by providing a Deep Learning–based generator that creates high-fidelity, risk-free synthetic patient records for research and education.

### 🔬 Scientific Methodology

The system is based on a prospective cross-sectional study of **2,522 patients** from the Vall d'Hebron Hospital Specialized Unit (Barcelona, Spain). Real patient questionnaire responses were used to train a cascade of models that generate synthetic counterparts.

#### The Cascade Model

The system relies on **graph theory** to determine an optimal order of generation based on the correlation strength between questionnaire subscales. The model requires the **SF-36** questionnaire as input and predicts five other clinical questionnaires in a cascading sequence:

1. **Input:** SF-36 (Short Form Health Survey)
2. **Step 1:** Predicts **HAD** (Hospital Anxiety and Depression Scale)
3. **Step 2:** Predicts **SCL-90-R** (Symptom Checklist-90-Revised)
4. **Step 3:** Predicts **FIS-8** (Fatigue Impact Scale – 8 items)
5. **Step 4:** Predicts **FIS-40** (Fatigue Impact Scale – 40 items)
6. **Step 5:** Predicts **PSQI** (Pittsburgh Sleep Quality Index)

The models achieve good performance (typical accuracy in the range 0.69–0.81 in the original paper) and were validated using statistical tests (e.g. Student's t-test) to ensure that synthetic data preserve the statistical properties of the real population.

For full methodological details, please refer to the Scientific Reports article.

---

### ⚠️ IMPORTANT: Accessing the Model Weights

**The pre-trained Deep Neural Network models (`.h5` files) required to run this code are not included in this repository.**

Due to GitHub’s file size limits and the large number of models required (one model per question across multiple questionnaires), the weights cannot be hosted here directly.

#### How to get the models

1. **Request access**  
   The models are hosted externally. You can request access via this link:  
   👉 [Google Drive Folder](https://drive.google.com/drive/folders/1dgBAP7qYim5MrS-iBoSFDf8LY58AK7mY?usp=sharing)

2. **Permission**  
   Please contact the author to grant download permissions.

3. **Setup**  
   Once downloaded, place the `.h5` files in the same directory as the `SyntheticDataGeneratorMESFCpatients.ipynb` script or update the paths in the code accordingly.

---

### 🚀 Usage

#### Prerequisites

You need a Python environment with the following libraries installed:

- `tensorflow`
- `pandas`
- `numpy` (implicit in pandas)

```bash
pip install tensorflow pandas
````

#### Running the Generator

The core logic is contained within `SyntheticDataGeneratorMESFCpatients.ipynb`.
The main function `SyntheticDataGeneratorSFC(X, metrics)` takes an input dataframe of SF-36 answers and returns synthetic data for the remaining questionnaires.

**Example code:**

```python
import pandas as pd
from tensorflow.keras import metrics
# Import the functions from the notebook or convert the notebook to a .py file
# from SyntheticDataGeneratorMESFCpatients import SyntheticDataGeneratorSFC

# 1. Load your SF-36 data (input matrix X)
# Ensure X has shape (n_patients, 36)
sf36_input = pd.read_csv('path_to_your_sf36_data.csv')

# 2. Define metrics
metrics_list = [
    metrics.Precision(name="precision"),
    metrics.Recall(name="recall"),
]

# 3. Generate synthetic data
# Note: Ensure .h5 model files are in the working directory
sf36, had, scl90r, fis8, fis40, psqi = SyntheticDataGeneratorSFC(sf36_input, metrics_list)

# 4. Save or inspect results
print("Generated HAD shape:", had.shape)
had.to_csv('synthetic_HAD.csv')
```

---

### 🔮 Roadmap & Future Work

* **Online application:** We are working on a web-based interface to allow researchers to generate synthetic datasets directly in the browser, without downloading heavy model weights or configuring a Python environment.
* **SF-36 generator:** A fully synthetic SF-36 generator (removing the need for real input data) is currently under validation and will be shared in the future.

---

### 📝 Limitations

* **Single-center data:** All training data come from a single specialized unit (Vall d'Hebron). The synthetic data may therefore reflect a bias toward more severe cases typically seen in specialised care versus primary care.
* **Demographics:** The underlying cohort may not fully represent non-Caucasian or globally diverse populations.
* **Cross-sectional design:** The models are based on cross-sectional data, not longitudinal trajectories. Temporal evolution of symptoms and scores is not captured.

---

### 📚 Citation

If you use this software or the synthetic data methodology in your research, please cite the original paper:

> Lacasa, M., Prados, F., Alegre, J. & Casas-Roma, J.
> **A synthetic data generation system for myalgic encephalomyelitis/chronic fatigue syndrome questionnaires.**
> *Scientific Reports* **13**, 14256 (2023).
> [https://doi.org/10.1038/s41598-023-40364-6](https://doi.org/10.1038/s41598-023-40364-6)

---

Perfecto, te dejo una sección **Contact** más completa, lista para pegar en el README. Solo tendrás que sustituir el email por el que quieras usar.


### ✉️ Contact

If you have questions about the code, encounter bugs, or would like to propose improvements, please:

1. **Open a GitHub Issue** in this repository, describing:
   - The context (what you were trying to do)
   - The exact error message (if any)
   - A minimal code snippet or screenshot, if relevant

2. **For access to model weights or collaboration inquiries**, you can contact the corresponding author of the paper:

**Dr. Marcos Lacasa Cazcarra**  
Data Scientist, Faculty of Health Sciences  
Universidad Internacional de La Rioja (UNIR), Spain  
Research collaborator, ME/CFS Unit, Vall d’Hebron University Hospital (Barcelona, Spain)  




