# Calibration-Aware Physical Layout Selection for Variational Quantum Circuits

**Author:** Aparna Sasi

## Overview
A simulation-based study of calibration-aware physical layout selection for Variational Quantum Circuits (VQCs) using Qiskit and Qiskit Aer.

## Objectives
- Compare Linear, Ring and Star four-qubit VQC architectures.
- Investigate hardware connectivity and transpilation overhead.
- Evaluate ideal and noisy quantum circuit simulations.
- Develop a heuristic approach for architecture and physical layout selection.

## Technologies
- Python
- Qiskit 2.6.2
- Qiskit Aer 0.18.2
- NumPy, Pandas, SciPy
- Scikit-learn
- Matplotlib

## Methodology
The study uses a synthetic binary classification dataset, ideal statevector simulations, synthetic noise models and density-matrix simulations.

## Key Results
- Star VQC achieved 64% test accuracy on the corrected fixed test split.
- Linear and Ring VQCs achieved 52% test accuracy.
- The layout selector evaluated 480 candidate configurations.
- Linear VQC was selected in all 40 profile-hardware cases.

## Repository Contents
- `QML.ipynb` – Google Colab research notebook.

## Limitations
This is a simulation-based prototype. Synthetic calibration profiles and simplified noise models were used. No physical quantum hardware execution or quantum advantage is claimed.

## Research Status
Exploratory simulation-based research.
