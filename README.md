# OpenMM Protein Molecular Dynamics (100 ps)

This repository demonstrates the setup and execution of a short
protein molecular dynamics (MD) simulation using OpenMM in Python.
The workflow is implemented in a Jupyter notebook and is fully
reproducible using conda.

---

## Overview

- Software: OpenMM
- Simulation type: Classical MD
- System: Protein in explicit solvent
- Ensemble: NVT (Langevin dynamics)
- Simulation length: 100 ps
- Interface: Jupyter Notebook (VS Code)

---

## Environment Setup

This project uses a dedicated conda environment.

```bash
conda create -n openmm python=3.10
conda activate openmm
conda install -c conda-forge openmm notebook jupyterlab
