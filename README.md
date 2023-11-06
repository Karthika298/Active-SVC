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
### Datasets used for classification tasks:
1.Tox21 -Toxicology in the 21st Century
2.BACE - Provides binding results for a set of inhibitors of human beta-secretase (BACE-1)
3.BBBP -(Blood-Brain-Barrier Penetration)
