# NV-Center Quantum Sensing for Biomedicine
Simulated nanodiamond relaxometry of mitochondrial free radicals using Qiskit.

This repository contains a compact simulation study inspired by NV‑nanodiamond relaxometry experiments in mitochondria. It models the NV center as an effective qubit undergoing amplitude damping, runs an inversion‑recovery protocol, fits T1 values, and demonstrates standard‑quantum‑limit scaling with independent NV ensembles. The accompanying report provides the biomedical and quantum‑sensing context.

**At a glance**
- Focus: NV‑center $T_1$ relaxometry as a proxy for local radical concentration in mitochondria
- Model: single‑exponential relaxation under amplitude damping
- Outputs: fitted $T_1$ values for low/medium/high radical conditions and 1/√N scaling across NV ensembles

## Contents
- `NV_T1_relaxometry_mitochondria_simulation.ipynb` Jupyter notebook with the full simulation workflow
- `nv_center_application_report.pdf` Full report with background, methods, and discussion
- `README.md` Project overview and usage

## Key Results (from the report)
- Three representative relaxation times are simulated: $T_1 = 3.0\ ms$ (low radicals), $1.5\ ms$ (medium), and $0.7\ ms$ (high).
- Single‑exponential fits recover the underlying $T_1$ values with sub‑percent relative error using $4096$ shots.
- For homogeneous ensembles of $N$ independent NV centers, the standard deviation of the estimated $T_1$ scales approximately as $1/\sqrt{N}$, consistent with the standard quantum limit.

## Method Summary
- Each NV‑nanodiamond is modeled as a single qubit with amplitude‑damping noise.
- Inversion‑recovery is implemented by preparing $\ket{1}$, applying an identity gate with amplitude damping parameterized by $T_1$, and measuring.
- The probability $P(\ket{1})$ vs delay $\tau$ is fit to a single‑exponential model to estimate T1.
- Ensemble scaling is assessed by repeating the experiment with $N$ qubits and aggregating fitted $T_1$ values.

## Requirements
The notebook installs Qiskit directly, but a clean environment is recommended.

- Python 3.9+
- `qiskit`, `qiskit-aer`, `numpy`, `scipy`, `matplotlib`

Quick install:
```bash
python -m pip install qiskit qiskit-aer numpy scipy matplotlib
```

## Run the Notebook
```bash
jupyter lab NV_T1_relaxometry_mitochondria_simulation.ipynb
```
or
```bash
jupyter notebook NV_T1_relaxometry_mitochondria_simulation.ipynb
```

Expected generated figures (saved by the notebook):
- `fig_single_nv.png` Single‑NV inversion‑recovery curves and fits
- `fig_nv_ensemble_sql.png` Standard‑quantum‑limit scaling plot

## Notes
- The model is intentionally simplified and does not include multi‑exponential relaxation, spatial inhomogeneity, or explicit radical diffusion.
- It is designed to be a clean, reproducible starting point for more detailed relaxometry simulations.

## Contact: 
Van Tien Nguyen (vantnprof@gmail.com)
