# 📊 Static Analysis of ASTM D638 Tensile Specimen in Elmer FEM

This guide details a complete step-by-step workflow to perform static structural analysis of a standard ASTM D638 tensile test specimen using **Elmer FEM software**.

---

## 📚 Prerequisites

* **Elmer FEM Software** installed ([Download Elmer](https://www.elmerfem.org/blog/binaries/))
* CAD model of ASTM D638 specimen in **STEP/STL format** (you can use FreeCAD/Fusion/SolidWorks to model it)

---
## VonMorcess Stress Simulation Result
![Alt Text](ASTM D638 ELEMER FEM\ASTM D638 Stress Color Plot.png)

## 📌 Simulation Workflow

### 📂 1️⃣ Create or Import Geometry

* Open **ElmerGUI**
* Go to `File → Open Mesh` if you already have a mesh
  or
  Mesh externally using **Gmsh** and import mesh files (`.msh`)

---

### 📝 2️⃣ Generate or Load Mesh

* Go to `Mesh → Load Mesh`
* Select your mesh directory (should contain `mesh.header`, `mesh.nodes`, `mesh.elements`)
* Click `Reload` if necessary
* Check mesh quality with `Mesh → Show Mesh`

---

### ⚙️ 3️⃣ Define Material Properties

* Go to `Model → Set Model`
* Select **Equation** → `Linear Elasticity`
* Go to `Model → Materials`
* Click `Add` and fill PLA (or your material) properties:

| Property        | Value (Example for PLA) |
| :-------------- | :---------------------- |
| Density         | 1250 kg/m³              |
| Young's Modulus | 3.5e9 Pa                |
| Poisson's Ratio | 0.36                    |
---

### 📌 4️⃣ Assign Boundary Conditions

* Go to `Model → Boundary Conditions`
* Click `Add`
* Define:

  * **Fixed boundary** at one end: set **Displacement 1, 2, 3 = 0**
  * **Applied force boundary** at other end: Traction Boundary Condition -> F3(Z-direction) = 12019230

    * In **Volume forces** → `Force = 0`

---

### 📌 5️⃣ Define Solver Settings

* Go to `Model → Setup`
* Set:

  * Solver log level: **5**
  * Output: **ElmerPost** or **VTU**
  * Steady-state analysis

---

### 📌 6️⃣ Export SIF File

* Go to `Run → Export`
* Save your `case.sif` (Elmer simulation input file)

---

### 📌 7️⃣ Run the Simulation

* Go to `Run → Start Solver`
* Check solver logs for convergence status

---

### 📈 8️⃣ Visualize Results

* Use **ElmerPost**

  * If using VTU output: open `.vtu` in Veiw -> StartElmerVTU
  * View **stress distribution**, **displacement vectors**, **deformed shape**

---

## 📊 Notes:

* Calculate cross-sectional area from D638 specimen dimensions for Traction F3 boundary condition:

  ```
  A = width × thickness
  ```

  e.g.
  Width = 13 mm, Thickness = 3.2 mm → A = 41.6 mm² = 41.6e-6 m²

* Traction Boundary condition F3 = Force(500) / Area
