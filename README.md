# Leader–Follower Cell Invasion Modeling via PINN and SINDy

This repository implements approaches for identifying biophysical parameters in a PDE-based model of collective cancer cell migration, where **leader** and **follower** cells obey coupled nonlinear partial differential equations.  
The goal is to **recover 8 key parameters** (diffusion, adhesion, chemotaxis) from the data.

---

# Methods

The methods we used to recover parameters:

1. **Physics-Informed Neural Networks (PINN):**  
   A deep learning framework that simultaneously fits spatiotemporal cell density data and enforces the governing PDE constraints, allowing accurate recovery of 8 key biophysical parameters from noisy or sparse data.

2. **Sparse Identification of Nonlinear Dynamics (SINDy):**  
   A regression-based method that constructs a library of candidate PDE terms and recovers governing equations and parameter combinations by solving a sparse linear system.  
   Our implementation uses custom dictionaries and multiple regression techniques (Ridge, Lasso, ElasticNet, Huber) to recover interpretable combinations of diffusion, adhesion, and chemotactic parameters.

---

## Dataset

We use the data/data11/4/ to recover parameters.

The training dataset is available as a compressed archive in the Releases page:

**[Download `data.zip`](https://github.com/SuperPeterLian/leader-follower-PINN/releases)**

After downloading:
1. Extract the archive to get a `data/` folder  
2. Place `data/` in the root directory  
3. Can operate the PINN code and SINDy code

---

## Parameters Learned

We tried to estimates the following 8 physical parameters:

| Parameter | Description |
|----------|-------------|
| `D_l`, `D_f` | Diffusion coefficients (leaders, followers) |
| `α_l`, `α_f`, `α_fl` | Adhesion coefficients |
| `κ`        | Adhesive flux scaling |
| `χ`, `β`   | Chemotaxis strength & gradient scaling |


The model enforces:
- Diffusion hierarchy: `D_l >> D_f`
- Adhesion hierarchy: `α_fl > α_f > α_l`
- All parameters positive via `softplus` or `sigmoid`







