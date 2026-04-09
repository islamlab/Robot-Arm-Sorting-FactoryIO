# 🤖 Industrial Robot Arm Sorting System

## 📌 Project Overview
This project is a complete simulation of an industrial pick-and-place and sorting operation using a 3D Robot Arm and a conveyor belt system. The logic is designed to ensure precise sequential movements, transferring boxes to their designated pallets without mechanical conflicts or step-skipping. 

The control architecture is built using **Siemens TIA Portal V16** and simulated in a highly realistic 3D environment using **Factory I/O**.

## 🛠️ Tech Stack & Tools
* **PLC Programming:** Siemens TIA Portal V16 (Ladder Logic).
* **Simulation Environment:** Factory I/O.
* **Control Concept:** State Machine / Step-Sequence Logic.

## 🧠 Logic & Architecture Highlights
To achieve industrial-grade reliability, the control logic avoids basic Set/Reset spaghetti code and instead utilizes a robust **State Machine** architecture:
* **Step-Sequence Control:** An `Incrementer` variable is used to define the current active state of the robot (0 = Home, 1 = Move Z Down, 2 = Grab, etc.).
* **Race Condition Prevention:** To prevent the PLC's rapid scan cycle from skipping steps, **Positive Edges (P-Trig)** are strictly integrated between the Timer outputs (`TON`) and the Incrementer inputs.
* **Dynamic Reset:** `MOVE` instructions are utilized to intelligently reset the system cycle to step 0 automatically upon completion or manual reset.

## 📁 Repository Structure
* 📂 `TIA_Portal_Project/`: Contains the archived TIA Portal V16 project (.zip).
* 📂 `Simulation_Scene/`: Contains the `.factoryio` custom 3D scene.
* 📂 `Documentation/`: Includes a highly readable PDF export of the Main OB1 Ladder Logic for quick code review.

## 🚀 How to Run the Simulation
1. Download and extract the repository.
2. Open the `.factoryio` scene file in Factory I/O.
3. Open the TIA Portal project and start the **S7-PLCSIM**.
4. Connect Factory I/O to the simulated PLC via the drivers menu.
5. Press the "Start" button on the physical control panel inside the Factory I/O environment.

## 👨‍💻 About the Author
**Islam**
Mechatronics Engineering Student passionate about Industrial Automation, Robotics, and clean PLC programming logic.
