# Capstone Proposal: Pipe Network Hydraulic Analysis Engine

## 1. The Problem
Civil and environmental engineering calculations for fluid flow and pressure head loss across pipe networks are frequently performed using fragmented spreadsheets or manual hand calculations. These legacy methods are highly prone to unit conversion errors, lack systematic boundary checking, and cannot be easily integrated into automated testing pipelines.

## 2. Solution Structure
The solution is structured as a modular Python engineering library built around discrete layers:
- **Boundary Unit Module (`src/units.py`):** Converts incoming input data into standard internal SI units at the program boundary.
- **Hydraulic Domain Models (`src/models.py`):** Encapsulates physical properties of pipes, fluid dynamics, and network geometry using clean data classes.
- **Computational Solver Engine (`src/solver.py`):** Executes friction factor and head-loss algorithms (Darcy-Weisbach and Hazen-Williams).
- **Automated Verification Suite (`tests/`):** A `pytest` test suite verifying mathematical correctness against published benchmark values.

## 3. Architectural Justification vs. Alternatives
An obvious alternative is a single monolithic script or spreadsheet model. However, blending user input, unit conversions, physics calculations, and output printing in one file creates a high risk of double-conversion bugs and makes individual algorithms untestable. The modular structure isolates unit conversions to entry boundaries, allowing core hydraulic equations to execute deterministically and enable clean automated unit testing.

## 4. Four Core Features to Deliver by Module 8
1. **Automated Boundary Unit Standardization:** Full conversion support for imperial and SI inputs with strict boundary enforcement.
2. **Multi-Pipe Head-Loss Calculation Engine:** Solves major and minor friction losses for single pipelines and parallel network configurations.
3. **Automated Pytest & Edge-Case Verification Suite:** Complete test suite covering known analytical solutions, zero-flow conditions, and invalid physical inputs.
4. **Exportable Summary & Plot Generator:** Automatically generates formatted Markdown/PDF engineering summary reports and Hydraulic Grade Line (HGL) plots.
