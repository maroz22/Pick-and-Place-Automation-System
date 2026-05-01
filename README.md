# Electro-Pneumatic Pick-and-Place Automation System

[![CAD](https://img.shields.io/badge/Designed_in-SolidWorks-red.svg)](https://www.solidworks.com/)
[![Simulation](https://img.shields.io/badge/Simulated_in-FluidSim-blue.svg)](https://www.festo.com/)
[![Control](https://img.shields.io/badge/Logic-Classic_Control-green.svg)]()

<div align="center">
  <video src="https://github.com/user-attachments/assets/a81c558c-6bcb-426c-9195-5db1f502ab9a" muted autoplay loop width="80%"></video>
</div>

---

## 📌 Project Overview
This project involves the full mechanical, pneumatic, and electrical design of an automated 3-axis Pick-and-Place system. It represents a core application of industrial automation, transferring objects from a magazine feed to a secondary placement coordinate. Precise motion control and sequencing are achieved through a custom-built classic control panel relying on 24V relays and magnetic reed switch feedback.

### The Engineering Constraints
The system had to be executed purely through classic control and electro-pneumatic logic without the use of microcontrollers. Furthermore, the pneumatic circuit required a highly specific feed sequence, engineered strictly using cascade control methods and check valves.

---

## ⚙️ System Sequence & Kinematics

The operation follows a complex sequential step diagram utilizing three double-acting pneumatic cylinders and a vacuum generator:
* **Cylinder A:** Feed Cylinder
* **Cylinder B:** Vertical (Z-axis) Cylinder
* **Cylinder C:** Horizontal (X-axis) Cylinder
* **S:** Air Suction Cup


**Pneumatic Step Sequence:** `A+ | A- | A+ | B+ | S+ | B- | C+ | B+ | S- | B- | C-`

1. **Feeding:** The cycle begins with Feed Cylinder A normally extended (`A+`). Upon pressing START, it immediately retracts (`A-`) to load a product from the magazine, then extends again (`A+`) to push the product into the pick-up position.
2. **Picking:** The Vertical Cylinder B extends (`B+`), making contact with the product. The single-stage vacuum generator activates (`S+`), and the cylinder retracts (`B-`) to lift the payload.
3. **Translating:** Horizontal Cylinder C extends (`C+`), carrying the entire Z-axis assembly across the gantry using a metal caster wheel tracking system.
4. **Placing:** Cylinder B extends (`B+`), the vacuum is cut (`S-`) to release the product, and Cylinder B retracts (`B-`).
5. **Resetting:** Horizontal Cylinder C retracts (`C-`), returning the assembly to the home position.

---

## 🛠️ Execution & Design

### 1. Mechanical Design (SolidWorks)
The system was fully modeled in 3D to verify cylinder strokes, tolerances, and the caster wheel tracking groove before fabrication. The frame is ground-settled with overall dimensions of `60cm x 35cm x 70.37cm`.

| Complete Assembly | Exploded View |
| :---: | :---: |
| ![SolidWorks Assembly](https://github.com/user-attachments/assets/55d1b49d-02bd-464b-99ee-1504fcef9aef) | ![Exploded View](https://github.com/user-attachments/assets/ee81260f-0930-4262-955e-e0e4a0bfd843) |

### 2. Electro-Pneumatic Circuit (FluidSim)
The logic was simulated in Festo FluidSim prior to hardware wiring to guarantee collision-free operation and validate the relay latching logic.

<div align="center">
  <img src="https://github.com/user-attachments/assets/de23cb83-31a5-438b-8dc4-2b09393fc83e" width="90%" alt="Electro-Pneumatic Circuit Diagram">
</div>

### 3. Hardware & Control Panel Implementation
The physical hardware incorporates 3 double-acting cylinders, a single-stage vacuum generator, 6 magnetic reed position sensors, and a custom-wired classic control panel.

| Custom Control Panel Wiring | Full Hardware Implementation |
| :---: | :---: |
| ![Control Panel](https://github.com/user-attachments/assets/b50b25cb-c80b-4245-87e2-4f3fbdf8f7fa) | ![Hardware Built](https://github.com/user-attachments/assets/40dab023-9d10-4609-8f74-416695b72cb9) |

*The control panel processes 24V DC logic via multiple relays to sequence the pneumatic solenoid valves, with emergency STOP capabilities that halt all operations and safely return the system to its initial state.*
## Author : Marwan Elsayed Ali
