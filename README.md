# Eco-IPM 

This repository contains the code necessary to build, simulate, and fit ecosystem integral projection models (Eco-IPMs).

---
## Get started

---
### Set up locally

First make sure that you have installed Python and Anaconda for managing virtual environments.

To install the environment required for running the model run the following commands:

```
conda env create --name mbipm --file=environment.yml
conda activate mbipm
```

If this does not work you may have to create an empty environment and install packages manually:

```
conda create -n mbipm python=3.10 numpy matplotlib seaborn jupyter
conda activate mbipm
pip3 install torch torchvision
```
Now you can open jupyter lab by running in the terminal the following command:

```
jupyter lab
```

You are ready to explore the notebooks.

---
### Set up on Colab

1. Open [Google Colab](https://colab.research.google.com/).
2. Sign in to your Google account.
3. Select **File > Open notebook > GitHub** and enter the repository URL: <https://github.com/WillemBonnaffe/Eco-IPM>.
4. Open `E1-tutorial-V2.ipynb`.
5. To use GPU acceleration, select **Runtime > Change runtime type > T4 GPU**. You may need to click **Connect** in the top-right corner.
6. Follow the instructions in the notebook.

---
## Notebooks

The repository contains multiple notebooks that can be run sequentially.

`A1-format-time-series.r` is an R script that formats the full time series of animal counts in Yellowstone.

`C1-setup-calibration.ipynb` is a jupyter notebook that prepares the Yellowstone ecosystem model (YEM) for fitting to the time series.  

`C2-calibrate-artificial-data.ipynb` fits the YEM to simulated time-series data and visualises the parameter optimisation chains.

`C3a-calibrate-cross-validation.ipynb` fits the YEM to the time series using cross-validation to assess out-of-sample predictions.

`C3b-check-cross-validation.ipynb` simulates the calibrated YEM and compares parameter estimates and model outputs from the cross-validation runs.

`C4a-calibrate-full.ipynb` fits the YEM to the full Yellowstone time series and visualises the parameter optimisation chains.

`C4b-check-calibrate-full.ipynb` simulates the fully calibrated YEM and analyses the fitted parameter values and resulting model outputs.

`C4c-check-calibrate-full-repeated-1.ipynb` checks consistency of predictions in a repeated calibration run. 

`D1-simulate.ipynb` takes the calibrated model and performs long term simulations.

`D2a-simulate-extirpation-short.ipynb` simulates short-term predator extirpation and reintroduction and estimates the time to perturbation and recovery equilibria.

`D2b-simulate-extirpation-short-adjoint-sensitivity.ipynb` simulates short-term predator extirpation and reintroduction and calculates adjoint sensitivities during the experiment.

`D2c-simulate-extirpation-short-adjoint-sensitivity-repeated-1.ipynb` check consistency of the short-term experiment with another model from a repeated calibration run.

`D2d-simulate-extirpation-short-adjoint-sensitivity-repeated-2.ipynb` check consistency of the short-term experiment with another model from a repeated calibration run.

`D2e-simulate-extirpation-long.ipynb` simulates long-term predator extirpation and reintroduction and estimates the time to perturbation and recovery equilibria.

`D4-simulate-sensitivity-V1-14-25-10-10.ipynb` tests how changing model parameters affects simulated ecosystem dynamics.

`E1-tutorial-V2.ipynb` introduces how to load and simulate the Eco-IPM, change its parameters, and run a sensitivity analysis.

---
## Supporting files

The notebooks call various files which are detailed below.

`À1-outputs/A1-tab-all-time-series.csv` is the formatted time series that can be used to calibrate the model.

`f_YEM_<model-version-name>.py` defines all functions necessary to initiate and simulate the YEM.

`f_YEM_wrapper_<model-version-name>.py` defines a wrapper to optimise the paramters of the YEM following DE optimisation. 

`f_demc_sparse_noise.py` contains functions that are necessary to perform DE optimisation.

`ìnitial-conditions-<model-version-name>.yaml` contains the initial state of the variables in the YEM before calibration.

`ìnitial-conditions-apriori-<model-version-name>.yaml` contains the initial state of the variables in the YEM after calibration.

`parameters-aposteriori-<model-version-name>.yaml` contains the values of all parameters in the YEM after calibration.

`parameters-apriori-<model-version-name>.yaml` contains the values of all parameters in the YEM before calibration.

`settings-apriori-<model-version-name>.yaml` contains the settings (e.g. number of bins) of the YEM both for usable before and after calibration.

---
## Data

All data necessary to parameterise and calibrate the model are located in the folder `data`.

`data/master-v2025-05-15-17-06.xlsx` contains all raw time series of elk, bison, cougar, and wolves.

`data/atchley-1989-table-8.csv` contains plant measurements grouped by soil type. `Soil` names the soil category; `Shoot wt. (g)` and `Root wt. (g)` give shoot and root weights in grams; `Height (cm)` gives plant height in centimetres; `Shoot/root` is the shoot-to-root weight ratio; and `% Emerg.` gives the percentage emergence.
