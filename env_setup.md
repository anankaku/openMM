# OpenMM + VS Code Environment Setup and Execution Manual

## Purpose

This manual describes how to set up an OpenMM Python environment from scratch, correctly configure the conda environment and Jupyter kernel in VS Code, and successfully execute OpenMM code.
It also documents common issues encountered during setup and their corresponding solutions.

---

## I. Environment Setup Workflow (From Zero to Execution)

### Step 1 | Verify Conda Installation

In a terminal, verify that conda is available:

```bash
conda --version
```

If the command is not found, Miniconda or Anaconda must be installed first.

---

### Step 2 | Create a Dedicated OpenMM Conda Environment

```bash
conda create -n openmm python=3.10
```

Activate the environment:

```bash
conda activate openmm
```

Verify the Python executable in use:

```bash
which python      # macOS / Linux
where python      # Windows
```

**Notes**

* The path should contain `envs/openmm`
* It is recommended to use a dedicated conda environment for each research project

---

### Step 3 | Install OpenMM in the Conda Environment

```bash
conda install -c conda-forge openmm
```

---

### Step 4 | Verify OpenMM Installation in the Terminal (Critical)

Before opening Jupyter or a VS Code notebook, verify that OpenMM is installed:

```bash
python -c "import openmm; print(openmm.__version__)"
```

**Evaluation**

* ✅ A version number is printed → OpenMM is correctly installed in the `openmm` environment
* ❌ `ModuleNotFoundError` → OpenMM is not installed successfully

> ⚠️ If this step fails, all subsequent kernel and notebook configuration steps are invalid.

---

## II. VS Code Configuration (Ensuring the Correct Environment Is Used)

### Step 5 | Open the Project Folder in VS Code

* `File → Open Folder`
* Select the actual project folder (not the parent or root directory)

---

### Step 6 | Set the Python Interpreter (Project-Level)

* `Ctrl + Shift + P`
* Select `Python: Select Interpreter`
* Choose `Python (openmm)`

This step creates the following file in the project directory:

```
.vscode/settings.json
```

**Notes**

* The interpreter setting applies to the entire project
* Do not set the interpreter at a top-level directory (e.g., `Research/`, `Projects/`)

---

### Step 7 | Set the Jupyter Kernel (Notebook-Level)

* Open the `.ipynb` file
* Top-right corner → `Select Kernel`
* Choose `Python (openmm)`

**Notes**

* The kernel is configured per notebook
* A correct interpreter does not guarantee a correct kernel

---

### Step 8 | Verify the Kernel Configuration (Strongly Recommended)

Execute the following in the first notebook cell:

```python
import sys
print(sys.executable)

import openmm
print(openmm.__version__)
```

**Evaluation**

* The Python path contains `envs/openmm`
* OpenMM imports successfully

At this point, OpenMM code can be executed safely.

---

## III. Git Initialization (Not Required for Execution, but Essential)

### Step 9 | Initialize the Git Repository

* VS Code sidebar → Source Control
* Click `Initialize Repository`

---

### Step 10 | Configure Git User Information (One-Time Setup)

In the VS Code terminal, run:

```bash
git config --global user.name "Annie Kuo"
git config --global user.email "GitHub registered email"
```

Verify the configuration:

```bash
git config --global --list
```

**Notes**

* This information is used as the commit author metadata
* It is independent of GitHub authentication/login
