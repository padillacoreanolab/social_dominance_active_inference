# Installation Commands

## Elo Score Environment

```
# Creating the Conda environment
# Doing it in the root directory to simplify
conda create --prefix ./elo_score_calculation_env python=3.9 --yes
# Turning on the Conda environment
conda activate ./elo_score_calculation_env

# Installing general data processing libraries
conda install -c conda-forge jupyterlab --yes
conda install -c conda-forge pandas --yes
conda install -c conda-forge scipy --yes
conda install -c conda-forge seaborn --yes
conda install -c conda-forge git --yes
conda install -c conda-forge gitpython --yes
conda install -c conda-forge openpyxl --yes
conda install -c conda-forge h5py --yes
```