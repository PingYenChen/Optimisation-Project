# Power System Cost Minimization Optimizsation 🚀

A Jupyter notebook implementing a **cost minimization model** for electricity generation in a hybrid power system: **4 thermal (CO2-emitting) power plants**, **1 wind farm**, and **1 energy storage unit (ESS)**. The goal is to meet hourly demand over a 24-hour period at minimum total cost, while handling variable wind output, ramping constraints, and storage dynamics.

I built this to demonstrate **linear/nonlinear programming** applied to real-world energy problems – mirroring techniques used in financial budgeting, scenario analysis, and resource allocation.

## Technologies Used
- **Pyomo**: Primary framework for modeling variables, constraints, and objective (supports nonlinear/quadratic terms).
- **PuLP**: Alternative linear programming implementation in notebook variants.
- **Gurobi Solver**: High-performance solver for non-convex problems (via Pyomo).
- **CBC Solver**: Open-source solver (default backend for PuLP).
- **Pandas & NumPy**: Data handling for inputs (demand, wind availability, generator parameters).
- **Matplotlib**: Visualization of dispatch schedules, storage state-of-charge (SOC), and costs.

## Key Features
- **Hybrid System Modeling**: Integrates thermal generation, variable wind power (with curtailment penalty), and battery storage (charge/discharge with efficiency losses).
- **Realistic Constraints**: Power balance, generator min/max limits, ramp-up/down rates, storage dynamics, and initial/final SOC requirements.
- **Quadratic Cost Functions**: Captures nonlinear fuel/maintenance costs for thermal units.
- **Wind Curtailment Penalty**: Encourages maximum renewable utilization.
- **CO₂ Emissions Tracking**: Explicit calculation (and optional minimization) via quadratic emission functions.
- **Optimal Dispatch Results**: Hourly schedules, total cost (~$223,360 example), and emissions (~870,440 kg).

## Process & Workflow
The notebook follows a structured optimization pipeline:

1. **Data Setup**: Define parameters – generator costs/limits/ramp rates, wind availability, hourly demand, storage capacity/efficiency.
2. **Model Formulation**: Create decision variables (power output per plant/time, wind used/curtailed, charge/discharge, SOC).
3. **Objective Definition**: Minimize total cost = thermal fuel costs (quadratic) + wind curtailment penalty.
4. **Constraints Addition**: Power balance, operational limits, ramping, storage energy balance.
5. **Solve**: Use Gurobi (for nonlinear) or CBC (linear) – models converge to optimal solutions.
6. **Results Extraction**: Extract optimal values into DataFrames.
7. **Visualization & Analysis**: Plots for generation stack, wind utilization, storage SOC/flows, cost breakdown, and emissions reporting.

Variants include linear (PuLP) vs. nonlinear (Pyomo + Gurobi) approaches for comparison.

## Potential Applications & Further Utilization
This optimization framework has broad applicability:
- **Energy & Utilities**: Economic dispatch, renewable integration planning, or grid decarbonization studies in Australia's transitioning power market.
- **Finance/Insurance Analytics**: Adapt for portfolio optimization, risk-constrained budgeting, or scenario-based forecasting (e.g., pricing under volatility).
- **Business Operations**: Resource allocation, supply chain cost minimization, or capacity planning with constraints.
- **Extensions**: Add stochastic wind/demand (robust optimization), multiple storage types, carbon pricing/taxes, unit commitment (binary on/off), or scale to full-year horizons. Integrate with Pandas for real datasets or deploy as a tool for sensitivity analysis.

Fork and modify parameters for your own scenarios – ideal for energy analytics or optimiation portfolios! 🌟
