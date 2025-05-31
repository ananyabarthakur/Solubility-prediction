#  Molecular Descriptor Generation Using ASE, MOPAC, and Mordred

This repository contains code that automates the process of **geometry optimization** for molecules using **ASE** and **MOPAC (PM7)**, followed by the computation of **2D and 3D molecular descriptors** using **Mordred**. The final descriptors are exported as a CSV file for further analysis.

---

##  What Does This Code Do?

 **Reads SMILES and molecule IDs** from a CSV file.  
 **Optimizes molecular geometries** using ASE and the MOPAC PM7 semi-empirical method.  
 **Maps 3D coordinates** from ASE to RDKit molecules.  
 **Computes a wide range of 2D and 3D descriptors** using Mordred, including:
- Atom counts, hydrogen bond donors/acceptors
- Bond and aromaticity descriptors
- Polarizability, topological indices
- 3D surface area and shape descriptors (PNSA, PPSA, DPSA, etc.)

 **Handles failures gracefully**, excluding molecules that failed during optimization or descriptor calculation.  
 **Exports** the final descriptor dataset to a CSV file for use in downstream machine learning or data analysis.

---

##  Key Components

- **ASE + MOPAC (PM7):** Geometry optimization of XYZ files.
- **RDKit:** SMILES parsing and molecule handling.
- **Mordred:** Descriptor calculation (2D & 3D).
- **Pandas & NumPy:** Data handling and export.
- **Error Handling:** Skips molecules that fail during optimization or descriptor generation.

---

## Example Workflow

1. Reads a dataset CSV file with:
   - Column 1: ID
   - Column 2: SMILES strings
   - Column 3: Target property (e.g. solubility).

2. For each molecule:
   - Reads its XYZ file from a specified directory.
   - Uses ASE to optimize geometry with MOPAC (PM7).
   - Updates RDKit 3D coordinates.
   - Calculates descriptors with Mordred.

3. Aggregates all descriptors in a dictionary.

4. Exports descriptors to a CSV file (`trial.csv`).

---

## 🛠️ Usage

1. Install dependencies:
```bash
pip install ase rdkit pandas mordred
