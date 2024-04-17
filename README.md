# Active-SVM
This project is inspired by the innovative application of ActiveSVM in **“Minimal gene set discovery in single-cell mRNA-seq datasets with ActiveSVM”**. **ActiveSVM** is a feature selection technique that identifies minimal yet highly informative gene sets, enabling efficient classification in single-cell datasets. In this project, we adapt ActiveSVM for chemoinformatic classification tasks. By employing this approach, we aim to streamline the classification tasks, enhancing accuracy and reducing computational requirements. With ActiveSVM in chemoinformatics, we can achieve robust classification results with a minimal number of features, making it a valuable tool for drug discovery and molecular property prediction.

## Installation
### We can install acitveSVC using :
```bash
!pip install activeSVC==4.0.1
!pip install psutil
```
Two variations are used in activeSVC **"min_complexity"** using fewer samples per iteration, and **"min_acquisition"** focusing on reusing samples from previous rounds to minimize total samples.
```bash
from activeSVC import min_complexity
from activeSVC import min_acquisition
from activeSVC import min_complexity_cv
from activeSVC import min_acquisition_cv
from activeSVC import min_complexity_h5py
from activeSVC import min_acquisition_h5py
```
### Installing Signaturizer and Mordred
```bash
pip install signaturizer
```
For detailed information on installation refer [signaturizer](https://pypi.org/project/signaturizer/)
```bash
pip install mordred
```
Refer [Mordred](https://mordred-descriptor.github.io/documentation/master/introduction.html#installation) for setting up the environment.

## WorkFlow
 **1. Data Extraction**
 
SMILES representations are extracted from datasets including Tox21, BBBP, and BACE from the DeepChem library. Users can access the datasets from the following link.[Deepchem](https://deepchem.readthedocs.io/en/latest/api_reference/moleculenet.html)

**2. Feature Generation**

**Modred** and **Signaturizer** are utilized for feature generation from the SMILES representations, converting them into numerical features suitable for machine learning algorithms.
* **Bioactivity signatures** are multi-dimensional vectors that capture biological traits of the molecule in a numerical vector format that is akin to the structural descriptors or fingerprints used in the field of chemoinformatics. **Signaturizers** relate to bioactivities of 25 different types (including **target profiles, cellular response, and clinical outcomes**)
* **Mordred (chemical-based descriptors)** is a powerful descriptor-calculation software designed for chemoinformatics applications. Developed to calculate over 1800 2D and 3D descriptors. Many types of molecular descriptors have been developed, such as the number of **carbon atoms, molecular weight, and predictive values of LogP (XLogP, ALogP,)**.

**3. Feature Selection**

Feature selection techniques used are :
* **Boruta:** A wrapper built around random forest to identify relevant features.
* **Recursive Feature Elimination (RFE):** Iteratively removes the weakest features while fitting a model to the remaining features until the desired number of features is reached.
* **LASSO (Least Absolute Shrinkage and Selection Operator):** Applies regularization to shrink coefficients of less important features to zero, effectively performing feature selection.

**4. Cluster Score Calculation**

Cluster scores are calculated to assess the quality of the data clustering
* **Silhouette Score:** Measures how similar an object is to its own cluster compared to other clusters.  i.e. **intra-cluster distance** and **inter-cluster distance**. The value ranges from **-1 to 1**. A higher score indicates better clustering.
* **Normalized Mutual Information (NMI):** a metric calculated between two clusterings and is a normalization of the Mutual Information (MI) score to scale the results between **0 (no mutual information) and 1 (perfect correlation)**.
* **Adjusted Rand Index:** Determines whether two cluster results are similar to each other. i.e. calculates a similarity between two cluster results by taking all points identified within the same cluster.

**5. Machine Learning Model Training**

* Various machine learning models are trained using the selected features. Models suitable for chemoinformatic classification tasks such as **Random Forest, Support Vector Machines (SVM), Gradient Boosting, etc., are chosen**. Hyperparameter tuning is performed to optimize model performance.

### Conclusion 
By integrating ActiveSVM into chemoinformatics, this project aims to revolutionize classification tasks by using minimal yet informative feature sets. The workflow includes feature generation, selection, cluster score calculation, and model training. With its potential to enhance accuracy while reducing computational overhead, ActiveSVM holds promise as a valuable tool in drug discovery.
  

