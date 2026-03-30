# S-Rail Crashworthiness — Simulation Dashboard

##  Overview
This repository contains a standalone, interactive web dashboard built to visualize Finite Element Analysis (FEA) crash-test results. The project was conducted as part of the **ESILV A4-MMN5** engineering curriculum (Team 505).

The primary objective is to evaluate and compare the crashworthiness and energy absorption capabilities of two structural designs:
1. **Classic Steel S-Rail** (Standard empty tube)
2. **Cross-Armature S-Rail** (Internal cross-shaped reinforcement)

## Technical Context & FEA Setup
The data presented is extracted from high-velocity impact simulations computed via **Abaqus/Explicit**. 

* **Impact Velocity:** 60,000 mm/s (approx. 216 km/h).
* **Material Model:** Steel with Isotropic Hardening and Ductile Damage ($\epsilon_f = 0.35$).
* **Elements:** SC8R (Continuum Shells).
* **Numerical Stability:** The simulation required strict management of the Courant stability condition, balancing element size, complex partitioning, and Mass Scaling to prevent excessive distortion errors at high velocities.

*Note: The Cross-armature data utilizes an unpartitioned mesh (Phase 2), while the Classic rail uses a structured high-quality mesh. The gains presented represent upper-bound estimates.*

## Key Performance Indicators (KPIs)
The introduction of the cross-armature yields massive structural improvements with a minimal weight penalty (+29% mass / +73g):

* **Energy Absorbed ($E_A$):** 726.8 J *(+244% vs Classic's 211.4 J)*
* **Specific Energy Absorption (SEA):** 2,209 J/kg *(+167% vs Classic's 826 J/kg)*
* **Mean Crushing Force (MCF):** 2,581 N *(x3.07 increase)*
* **Crush Force Efficiency (CFE):** 0.306 *(vs 0.098 for the classic design)*
* **Peak Force:** Maintained at a safe level (8,431 N vs 8,553 N), avoiding lethal initial decelerations.

## Dashboard Features
The provided `index.html` is a zero-dependency, single-file dashboard utilizing **Plotly.js**. It features interactive controls (smoothing windows, toggles for shaded areas and MCF lines) and includes:
* **Force-Displacement ($F-U$) Curves**
* **Energy Histories ($IE$ vs $KE$)** demonstrating stable pseudo-static folding (ALLKE << ALLIE).
* **Crashworthiness Maps** (Iso-SEA tracking).
* **Material Comparisons** (Steel vs. Aluminum 6061-T6 vs. Magnesium AZ31B).
* **Normalized Performance Radar Charts**.

## How to use
No server installation or backend is required. All data arrays are embedded within the script.
1. Clone this repository.
2. Open `index.html` directly in any modern web browser.
