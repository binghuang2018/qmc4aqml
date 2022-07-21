The QMC4AQML dataset

Authors: 
- Bing Huang (University of Vienna, bing.huang@univie.ac.at)
- O. Anatole von Lilienfeld (University of Toronto, anatole.vonlilienfeld@utoronto.ca)
- Jaron T. Krogel (Oak Ridge National Laboratory, krogeljt@ornl.gov) 
- Anouar Benali (Oak Ridge National Laboratory, benali@anl.gov)


# General

- Purpose: used for testing multi-level quantum machine learning model aiming for an accuracy at the quantum Monte Carlo (QMC) level
- Molecular data are provided in the extxyz format (https://wiki.fysik.dtu.dk/ase/ase/io/formatoptions.html#extxyz).
- Single point energies (SPE) are in the unit Hartree
- Geometries were optimzed at the level of B3LYP/cc-pVTZ
- All FN-QMC energies were obtained using the B3LYP/cc-pVTZ nodal surfaces.
    - retrievable through the key `qmc_b3lyp` in the extxyz file
- Quantum chemical (QC) levels of theory include
    - HF, DFT (PBE, B3LYP)
    - post-HF levels of theory: MP2, CCSD(T)
    - and basis set is fixed to cc-pVTZ
    - with SPE retrievable as the key of format `theory+vtz`
        - e.g., B3LYP/cc-pVTZ energy is assigned the key `b3lypvtz` (which is identical to key `b5vlypvtz`)


# Test molecules

- located in the folder `targets/`
- totalling 50 molecules, drawn randomly from the QM9 dataset
- calculated at FN-QMC level and various other cheaper levels


# Training set

Two sets of amons are available:

- graph amons (with QMC energy) of the QM9 dataset (in the folder `amons-ni5-qmc/`)
    - made up of at most 5 heavy atoms
    - totalling 1175
    - amounts to force-field global minima
- conformer amons (without QMC energy) for the 50 test molecules (in `amons-ni7/`)
    - the maximal number of heavy atoms is now 7
    - include all conformational degrees of freedom
        - that is, multiple conformer amons may share the same SMILES string
    - the conformer amons for, say the first test molecule (`targets/frag_0001.xyz`), are `amons-ni7/frag_0001_a*xyz`

