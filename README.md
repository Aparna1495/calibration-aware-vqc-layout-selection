# Calibration-Aware Physical Layout Selection for Variational Quantum Circuits on Noisy Quantum Hardware

**Author:** Aparna Sasi  
**Research Area:** Quantum Machine Learning | Variational Quantum Circuits | Hardware-Aware Quantum Computing  
**Framework:** Qiskit and Qiskit Aer  
**Research Status:** Simulation-based prototype

## Overview

This project investigates calibration-aware physical layout selection for four-qubit Variational Quantum Circuits (VQCs).

Three circuit architectures — Linear, Ring and Star — are compared using ideal statevector simulation and noisy density-matrix simulation with synthetic depolarising noise.

The study also explores a heuristic cost-based selection procedure using synthetic calibration profiles to evaluate architecture and physical-layout configurations.

**Important:** All reported quantum experiments were conducted using classical simulation. No physical quantum hardware execution or quantum advantage is claimed.

## Research Objectives

- Implement and compare Linear, Ring and Star four-qubit VQC architectures.
- Evaluate ideal classification performance using a common dataset split.
- Investigate transpilation overhead under different connectivity configurations.
- Estimate implementation costs using synthetic calibration profiles.
- Evaluate noisy circuit execution using Qiskit Aer density-matrix simulation.
- Investigate heuristic physical-layout selection.

## Methodology

### Dataset and preprocessing

A synthetic binary classification dataset was generated using Scikit-learn.

- 100 samples
- 4 input features
- 2 classes
- 75 training samples
- 25 test samples
- Stratified train–test split
- MinMaxScaler feature mapping to [-π, π]

### Quantum circuit architectures

Three four-qubit VQC architectures were investigated:

1. Linear VQC
2. Ring VQC
3. Star VQC

A measurement-observable audit identified an issue with the original qubit-0 measurement. The experiment was corrected to measure logical qubit 3 using the Qiskit Pauli label `ZIII`, and the architectures were retrained.

### Optimisation

- Classical optimiser: COBYLA
- Maximum iterations: 500
- Initialisations: 5

### Noise and physical-layout analysis

Noisy evaluation used Qiskit Aer density-matrix simulation with synthetic depolarising noise.

The separate heuristic layout selector evaluated:

- 3 circuit architectures
- 2 hardware connectivity configurations
- 4 initial physical layouts
- 20 synthetic calibration profiles

Total configurations evaluated: **480**

## Key Results

### Ideal simulation

| Architecture | Test accuracy | F1 score |
|---|---:|---:|
| Linear VQC | 52% | 0.3333 |
| Ring VQC | 52% | 0.3333 |
| Star VQC | 64% | 0.6087 |

Star VQC achieved the highest test accuracy in the corrected ideal simulation.

### Noisy simulation

The tested synthetic noise configurations preserved classification accuracy and F1 scores while slightly increasing mean squared error.

For Star VQC, mean test MSE was approximately 0.2138 in ideal simulation and 0.2142–0.2144 in noisy simulation.

### Physical-layout selection

The heuristic selector evaluated 480 candidate configurations and selected Linear VQC in all 40 profile–hardware cases.

Selected physical layouts:
- Forward mapping: 26 cases
- Reverse mapping: 14 cases

The cost-optimal architecture and the best-performing classifier were different under the current experimental setup.

## Repository Structure

```text
calibration-aware-vqc-layout-selection/
│
├── README.md
├── QML.ipynb
├── requirements.txt
├── Calibration_Aware_VQC_LaTeX_Report.pdf
│
└── results/
    ├── README.md
    ├── corrected_ideal_results.csv
    ├── corrected_noisy_results.csv
    └── corrected_layout_selection.csv
```

## Installation

Clone the repository:

```bash
git clone https://github.com/Aparna1495/calibration-aware-vqc-layout-selection.git
cd calibration-aware-vqc-layout-selection
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Running the Project

The notebook can be opened directly in Google Colab:

[Open QML.ipynb in Google Colab](https://colab.research.google.com/github/Aparna1495/calibration-aware-vqc-layout-selection/blob/main/QML.ipynb)

Alternatively, open `QML.ipynb` using Jupyter Notebook.

## Limitations

- The dataset contains only 100 synthetic samples.
- Results are based on one fixed train–test split.
- Calibration profiles are synthetic and do not represent actual quantum processor measurements.
- The noise model does not comprehensively include relaxation, readout errors, crosstalk and coherent noise.
- The physical-layout selection score uses manually chosen heuristic weights.
- Star noisy comparisons require topology-faithful recompilation before strong topology-specific conclusions.
- No physical quantum hardware execution was performed.

## Future Work

- Incorporate real quantum processor calibration data.
- Investigate T1, T2, readout errors and crosstalk.
- Improve topology-aware circuit compilation.
- Evaluate additional physical-layout selection strategies.
- Repeat experiments across independent datasets and train–test splits.
- Validate selected circuits on physical quantum hardware.

## References

1. M. Cerezo et al., "Variational quantum algorithms," Nature Reviews Physics, 2021.
2. M. Schuld and F. Petruccione, *Supervised Learning with Quantum Computers*, Springer, 2018.
3. IBM Quantum — Qiskit Documentation.
4. Qiskit Aer Documentation.

---

**Research by Aparna Sasi**  
Quantum Computing | Quantum Machine Learning | Quantum Hardware-Aware Circuit Design
