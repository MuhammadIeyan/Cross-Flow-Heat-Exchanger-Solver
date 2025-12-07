# Cross-Flow Heat Exchanger SOlver
https://colab.research.google.com/drive/1nWd59-1BZ7ZhdlCuIWg4C1zJVDlHFRdf?usp=sharing

## 📌 Project Overview
This project is a numerical simulation tool designed to analyze the thermal performance of a cross-flow heat exchanger. Specifically, it models the cooling of engine oil flowing through a smooth copper pipe when exposed to external cross-flow air.

The solver iteratively calculates temperature-dependent fluid properties to determine the **Convection Heat Transfer Coefficients** ($h$), **Overall Heat Transfer Coefficient** ($U$), and the spatial temperature distribution along the pipe length.

## ⚙️ Methodology & Physics
The simulation integrates several empirical correlations to ensure physical accuracy:

* **Internal Flow (Oil):**
    * Uses the **Petukhov Equation** for the friction factor in turbulent smooth pipes.
    * Uses the **Dittus-Boelter** correlation (cooling mode, $n=0.3$) for the Nusselt number.
    * Includes a laminar flow fallback ($Nu = 3.66$) for low-velocity scenarios.
* **External Flow (Air):**
    * Uses the **Hilpert Correlation** for flow over a cylinder to determine the external drag and heat transfer.
* **Solver Logic:**
    * Implements an iterative loop to converge on the bulk mean fluid temperature.
    * Dynamically interpolates fluid properties (density, viscosity, Prandtl number) using `scipy.interpolate` based on real-time temperature updates.

## 📊 Results & Sensitivity Analysis
The tool allows for sensitivity analysis to observe how flow velocity impacts cooling efficiency.

![Simulation Results](simulation_results.png)

* **Scenario A (Operating Condition):** At high velocity ($5 \text{ m/s}$), the residence time is short, resulting in a minimal temperature drop ($\approx 0.4^\circ\text{C}$), demonstrating high mass throughput but lower thermal change per unit mass.
* **Scenario B (Low Velocity):** At $0.1 \text{ m/s}$, the fluid exhibits a classic exponential decay curve, validating the physical correctness of the heat transfer model.

## 🚀 How to Run
1.  Click the "Open in Colab" badge above.
2.  Run the cells to generate the simulation data and plots.

## 📚 References
* *Heat and Mass Transfer: Fundamentals and Applications*, Cengel & Ghajar, 5th Edition.
