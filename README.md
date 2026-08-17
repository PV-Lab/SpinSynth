# SpinSynth

This repository includes the codes for manuscript:

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
├── FAPbI3_Test/
├── Phase_Purity_Proxy_Test/
├── LLM_BO/                 # LLM-assisted initialization and MOBO workflows
├── Regular_BO/             # Conventional MOBO baseline
├── High-throughput Characterization/       # Hyperspectral characterization pipelines
    ├── film_coverage.ipynb
    ├── film_uniformity.ipynb
    └── phase_purity_proxy.ipynb
```

## Requirements

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

## Data availability

All the data supporting the manuscript are available at **https://osf.io/cbrk2/overview**.

## License

This repository is distributed under the MIT License. See `LICENSE` for details.
