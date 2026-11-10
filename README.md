# PyPSA Interview Assignment

Solutions to the PyPSA interview assignment for the funded Ph.D. position on the Alberta Restructured Energy Market (REM) PyPSA Modelling Project, Delta E+ Research Lab, SFU.

Author: Kuma Erkisso

## Contents

| File | What it covers |
|---|---|
| `task1_ac_dc_meshed.ipynb` | Runs the meshed AC-DC example, describes the system and generator sizes, explains the Frankfurt Gas dispatch at 05:00 |
| `task2_generation_curtailment_storage.ipynb` | Stacked area chart of generation with total load, why Frankfurt Gas runs in only 2 snapshots, curtailment, value of storage |
| `task3_single_node_capital_cost.ipynb` | Single-node model, capital cost sweep, threshold at which Norway Wind replaces Frankfurt Gas |
| `PyPSA_Assignment_Response_Kuma_Erkisso.docx` / `.pdf` | Written response summarising the answers |
| `figures/` | Exported charts |
| `build_notebooks.py` | Script used to generate the notebook structure |

## Setup

Tested with Python 3.13 and PyPSA 1.4.0 on Windows.

```bash
conda create -n pypsa312 python=3.13
conda activate pypsa312
pip install pypsa jupyterlab matplotlib ipykernel
python -m jupyterlab
```

Alternatively: `conda env create -f environment.yml`.

The notebooks use the open-source HiGHS solver, which is installed with PyPSA, so no commercial licence is needed.
The example network is downloaded automatically by `pypsa.examples.ac_dc_meshed()`.

## Key results

* **Task 1:** Optimal build is about 4.1 GW Manchester Wind, 1.5 GW Norway Wind, 1.7 GW Frankfurt Wind and 982 MW Frankfurt Gas. Frankfurt Gas is the only gas plant built because the binding CO2 cap makes gas a peaker, and Frankfurt Gas has the lowest capital and fuel cost.
* **Task 2:** Gas runs only at 05:00 and 09:00, the two hours where available wind is below load. About 5,550 MWh (15%) of wind is curtailed, all at Manchester. An illustrative battery removes curtailment and cuts system cost by about 19%.
* **Task 3:** In the single-node model, Norway Wind starts replacing Frankfurt Gas once its capital cost drops below **114.67 EUR/MW**, with further steps at 110.67 and 106.67 EUR/MW (full replacement).
