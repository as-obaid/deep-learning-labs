<div align="center">

# Deep Learning Labs

Hands-on deep learning labs, from shallow networks and generalization to CNN architectures and attention.

[Highlights](#highlights) · [Labs](#labs) · [Tech stack](#tech-stack) · [Getting started](#getting-started)

</div>

Each lab runs controlled experiments against a fixed baseline, selects models
on validation data only, and scores the test set once. A fixed seed and
deterministic TensorFlow ops make every run reproducible with the same library
versions and hardware. Every notebook is saved fully executed, so results can
be read on GitHub without running anything.

## Highlights

| Area | Result |
| --- | --- |
| Shallow networks | A one-hidden-layer, 256-unit ReLU network is off by **$35,300** on average when predicting California block-group house values (test MAE, 1990 dollars); at that width ReLU beats Tanh and Sigmoid on validation MSE (**0.2835** vs. 0.3226 and 0.3351) |
| Weight initialization | He-normal keeps the second hidden layer's activation scale at **0.99** of its input, against **0.64** under Glorot, yet best Fashion-MNIST validation accuracy is a tie (0.8968 vs. 0.8987) |
| Regularization | Dropout 0.2 gives the best Fashion-MNIST validation accuracy of six runs (**0.9031**); L2 at λ = 0.001 shrinks the hidden weights sixfold with no accuracy gain |
| Batch size | On CIFAR-10, batch 512 reaches 45% validation accuracy in **792** weight updates; batch 32 needs **11,256** |
| Batch normalization | Adding BN without dropout widens the train–validation gap to **59** points and cuts validation accuracy by **8.8** points (50.62% → 41.86%) |
| Hyperparameter search | With 8 trials each, random search finds **52.40%** validation accuracy and Optuna's TPE **50.90%**; the selected model scores **52.01%** on test |

## Labs

| # | Lab | What it covers | Data | |
| :-: | --- | --- | --- | :-: |
| 01 | [Shallow Neural Networks](ShallowNN.ipynb) | • One-hidden-layer regression network<br>• Hidden width: 16, 64 and 256 units<br>• ReLU vs. Tanh vs. Sigmoid<br>• Test error by house-value band | California Housing | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/deep-learning-labs/blob/main/ShallowNN.ipynb) |
| 02 | [Generalization](Generalization.ipynb) | • Glorot vs. He initialization, checked against theory<br>• L2 regularization at two strengths<br>• Dropout at two rates<br>• Early stopping and the generalization gap | Fashion-MNIST | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/deep-learning-labs/blob/main/Generalization.ipynb) |
| 03 | [Hyperparameter Tuning](HyperparameterTuning.ipynb) | • Batch size: 32, 128 and 512<br>• Batch normalization<br>• Random search vs. Bayesian optimization (Optuna TPE)<br>• Per-class test accuracy and confusion matrix | CIFAR-10 | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/deep-learning-labs/blob/main/HyperparameterTuning.ipynb) |

> **Coming next:** CNN Architectures · Attention-Based Text Classification

## Tech stack

| Library | Role | Labs |
| --- | --- | :-: |
| ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) | Language | 01‑03 |
| ![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white) | Backend and deterministic training | 01‑03 |
| ![Keras](https://img.shields.io/badge/Keras-D00000?style=for-the-badge&logo=keras&logoColor=white) | Dense networks, dropout, batch normalization, Fashion-MNIST and CIFAR-10 loaders | 01‑03 |
| ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white) | California Housing, stratified splits, feature scaling, confusion matrix | 01‑03 |
| ![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white) | Arrays and metrics | 01‑03 |
| ![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white) | Result tables | 01‑03 |
| ![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge) | Learning curves and diagnostic plots | 01‑03 |
| ![Optuna](https://img.shields.io/badge/Optuna-2C5BB4?style=for-the-badge) | Bayesian optimization (TPE sampler) | 03 |
| ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white) | Notebooks, runnable on Google Colab | 01‑03 |

## Getting started

**Colab:** click a badge in the [Labs](#labs) table, then choose **Runtime → Run all**.
Datasets download on first use, Lab 03 installs Optuna if it is missing, and no
GPU is needed. On an Apple M1 Pro CPU, full runs take about 2, 4 and 25 minutes.

**Locally:**

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install jupyter tensorflow scikit-learn pandas matplotlib optuna
jupyter lab
```

Each notebook prints its library versions in its setup cell. The saved results
come from Python 3.12, TensorFlow 2.21 and Keras 3.15.

## About

Coursework for AAI 6640 *Applied Deep Learning* at Northeastern University,
Fall 2026.

**Muhammad Obaidullah** · [github.com/as-obaid](https://github.com/as-obaid)
