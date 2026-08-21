# SpinSynth

This repository includes the codes for manuscript: <a href="https://arxiv.org/abs/2608.15928">https://arxiv.org/abs/2608.15928</a>

**“Synthesizing like a chemist: an iterative, feedback-driven loop for materials discovery”**

## Overview

SpinSynth is a closed-loop framework for iterative materials synthesis optimization that integrates large language models (LLMs), high-throughput hyperspectral imaging, and multi-objective Bayesian optimization (MOBO). The framework is designed to place **human tacit synthesis knowledge in the loop** while reducing the time and effort for synthesizing a novel material. The framework consists of three main components:

1. **LLM-assisted initialization** — synthesis knowledge is extracted from the literature and used to define a chemically informed parameter space and propose initialization conditions for MOBO.
2. **High-throughput characterization** — hyperspectral imaging and auto-charaterization algorithm provide rapid quantitative experimental feedback of film coverage, uniformity, and a phase-purity proxy.
3. **Iterative Bayesian optimization** — multi-objective Bayesian optimization uses high-throughput charaterization results to propose synthesis conditions over successive rounds.

We demonstrate the workflow using the spin-coating synthesis of the perovskite-inspired composition **Rb₃BiI₆** which has not been reported before and compare LLM-assisted Bayesian optimization (LLM-BO) with conventionally Bayesian optimization initialized by Latin Hypercube Sampling (LHS).

## Repository structure

```text
SpinSynth/
├── README.md
├── LICENSE
├── requirements.txt
├── FAPbI3_Test/
├── Phase_Purity_Proxy_Test/
├── LLM_BO/                 # LLM-assisted initialization and MOBO workflows
├── Regular_BO/             # Conventional MOBO baseline
├── Example_Data/           # Dataset to demo the code
├── High-throughput Characterization/       # Hyperspectral characterization pipelines
    ├── film_coverage.ipynb
    ├── film_uniformity.ipynb
    └── phase_purity_proxy.ipynb
```

## System Requirements

### Operating system

The code was developed and tested on:

- macOS 12.6
- Apple Silicon (M1 Pro)
- Python 3.11.8

All the codes are written in Python. Other operating systems have not been systematically tested.

### Python dependencies

The MOBO code was adapted from **https://github.com/PV-Lab/MOBO-Kit**. Please see the repo for detailed requirements.

The high-throughput characterization analysis was performed in Python. Major dependencies include:

```text
requests
matplotlib
numpy
pandas
scikit-learn
scipy
shapely
spectral
seaborn
```

Exact package versions used for the manuscript analyses are provided in `requirements.txt`.

## Installation guide (2~5 mins)

### 1.Clone the repository

```bash
git clone https://github.com/PV-Lab/SpinSynth.git
cd SpinSynth
```

### 2.Create a Python environment

We recommend creating a dedicated environment rather than installing into an existing base environment.

```bash
conda create -n spinsynth python=3.11.8
conda activate spinsynth
```

### 3.Install dependencies through pip
```bash
pip install -r requirements.txt
```
Open the repository directly in VS Code and select the `spinsynth` environment as the notebook kernel to use the supplied Jupyter notebooks.

## Demo

The repository contains Jupyter notebooks for calculating the three hyperspectral-imaging-derived objectives:

- film coverage;
- film uniformity;
- phase purity proxy.

Example test datasets are provided in Example_Data folder.

The repository also includes MOBO codes for both LLM-BO group and regular BO group.

### 1.Film coverage (5~10 mins)

Open:

```text
[exact path]/film_coverage.ipynb
```
Set the correct datapath and savepath in the notebook and run all notebook cells.

### 2.Film uniformity (5~10 mins)

Open:

```text
[exact path]/film_uniformity.ipynb
```
Set the correct datapath and savepath in the notebook and run all notebook cells.
### 3.Phase purity proxy (10~20 mins)

Open:

```text
[exact path]/phase_purity_proxy.ipynb
```
Set the correct datapath and savepath in the notebook and run all notebook cells.

### 4.MOBO (5~10 mins)

Download the notebooks in the folder LLM-BO/Reugular BO and run all notebook cells.

### 5. Expected output
The expected outputs for each cell can be found on uploaded notebooks.

## Instructions for use

To analyze a thin-film sample:

1. Place the hyperspectral data in an accessible local directory.
2. Open the corresponding characterization notebook.
3. Modify the datapath and savepath. Modify the corresponding parameters in the functions based on the hypercube quality and the material types.
4. Run the notebook sequentially.
5. Record the resulting coverage, uniformity, and phase purity-proxy values.

The resulting objective values can then be supplied to the Bayesian optimization workflow as experimental feedback.

## Data availability

All the data supporting the manuscript are available at **https://osf.io/cbrk2/overview**.

## License

This repository is distributed under the MIT License. See `LICENSE` for details.
