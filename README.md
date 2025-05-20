# Delta Zero: Open-Source FEM & Simulation Software Accuracy Benchmark

## Overview

This project benchmarks and compares the accuracy of various open-source Finite Element Method (FEM) and simulation software packages. Using the ASTM D638 tensile specimen as a standard test case, we evaluate how different tools perform in static structural analysis scenarios.

## Goals

- Assess the accuracy of open-source FEM/simulation software (e.g., Elmer FEM, CalculiX, Code_Aster, OpenFOAM, etc.)
- Provide reproducible workflows and input files for each software
- Compare simulation results (stress, displacement, etc.) against analytical solutions and reference data

## Project Structure

- `ASTM D638 ELEMER FEM/`  
  Elmer FEM simulation files, geometry, mesh, and results for ASTM D638 specimen.
- `Dense Mesh ELEMER ASTM D638/`  
  High-resolution mesh and simulation results for Elmer FEM.
- `D638/`  
  CAD models, G-code, and other reference files for the ASTM D638 specimen.

## Workflow

1. **Geometry Preparation:**  
   CAD models of ASTM D638 specimen are created or imported.
2. **Meshing:**  
   Meshes are generated using Gmsh or built-in tools.
3. **Simulation Setup:**  
   Material properties and boundary conditions are defined according to ASTM D638 standards.
4. **Solver Execution:**  
   Simulations are run in each FEM software.
5. **Results Comparison:**  
   Output (stress, strain, displacement) is compared across software and with analytical calculations.

## Included Software

- [Elmer FEM](https://www.elmerfem.org/)

## How to Reproduce

Each subfolder contains a README with step-by-step instructions for running the simulation in the respective software.  
General steps:
- Install the required software
- Follow the workflow in the relevant folder
- Compare results using provided scripts or manually

## Displacemnt
![Simulation file](./D638/D638%20Topology%20Optimised.STL)

## Von Mises Stress Simulation Result
![Simulation file](./D638/D638%20Removed%20part%20after%20topology%20optimization.STL)
## References

- ASTM D638 Standard Test Method for Tensile Properties of Plastics
- [Elmer FEM Documentation](https://www.elmerfem.org/blog/documentation/)

---
