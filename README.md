# Physics-Informed Neural Network for Leader–Follower Cell Invasion Modeling

This repository contains a PINN-based parameter inference framework for a leader–follower partial differential equation (PDE) model of collective cancer cell migration.  
The model simultaneously fits spatiotemporal data and enforces governing PDE constraints, recovering 8 biophysical parameters.

---

## Project Summary

This project uses a Physics-Informed Neural Network (PINN) to estimate diffusion, adhesion, and chemotaxis-related parameters in a biologically-inspired PDE system governing the interaction between leader and follower cells. The model is trained using both data fidelity loss and physics-based residual loss.

---

## Dataset

We use the data/

The training dataset is available as a compressed archive in the Releases page:

**[Download `data.zip`](https://github.com/SuperPeterLian/leader-follower-PINN/releases)**

After downloading:
1. Extract the archive to get a `data/` folder  
2. Place `data/` in the root directory  
3. Open and run `main.ipynb`

---

## Parameters Learned

The PINN estimates the following 8 physical parameters:

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

---

## How to Run

1. Download this repository:
   ```bash
   git clone https://github.com/SuperPeterLian/leader-follower-PINN.git
   cd leader-follower-PINN
