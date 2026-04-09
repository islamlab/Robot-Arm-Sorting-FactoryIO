# 🤖 Industrial Robot Arm & Conveyor Sorting System

[![Simulation Video](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=VIDEO_ID)  
*(Note: Click the image above to watch the full system simulation on YouTube)*

## 📌 Project Overview
This project is a complete industrial automation simulation of a pick-and-place and sorting operation. It features a 3D Robot Arm and a conveyor belt system designed to transfer boxes to designated pallets accurately. 

The control architecture is programmed using **Siemens TIA Portal V16** and simulated in a highly realistic 3D industrial environment using **Factory I/O**.

## 🛠️ Tech Stack & Tools
* **PLC Programming Environment:** Siemens TIA Portal V16.
* **Logic Language:** Ladder Logic (LAD).
* **3D Simulation:** Factory I/O.
* **Virtual Controller:** S7-PLCSIM.

## 🧠 Logic & Control Architecture
To ensure industrial-grade reliability and avoid basic Set/Reset "spaghetti code," the control logic is built upon a robust **State Machine (Step-Sequence)** architecture. Key technical highlights include:

* **Sequence Control:** An `Incrementer` variable (Memory Word) acts as the active state tracker to define the robot's current step (e.g., 0 = Home, 1 = Move Z Down, 2 = Grab, etc.).
* **Race Condition Prevention:** To prevent the PLC's rapid scan cycle from executing multiple increments and skipping mechanical steps, **Positive Edges (P-Trig)** are strictly implemented between the Timer outputs (`TON.Q`) and the `INC` instruction inputs.
* **Precise Timing:** `TON` timers are integrated into each state to account for the physical mechanical delay of the 3D robot arm and conveyor rollers.
* **Dynamic System Reset:** `MOVE` instructions are utilized to write `0` to the incrementer, safely and intelligently resetting the entire sequence loop upon pallet completion.

## 📁 Repository Structure
* 📦 `TIA_Portal_Project_Archive.zap16`: The complete, compressed TIA Portal V16 project archive. Ready to be retrieved directly into TIA Portal without broken paths or missing hardware configurations.
* 🏭 `Robot_Sorting_Scene.factoryio`: The custom 3D scene built in Factory I/O containing all sensors, actuators, and mechanical components.
* 📄 `Main_OB1_Ladder_Logic.pdf`: A clear, exported PDF printout of the Main OB1 block for quick code review without needing the TIA Portal software.

## 🚀 How to Run the Simulation
1. Download this repository to your local machine.
2. Open Factory I/O and load the `Robot_Sorting_Scene.factoryio` scene.
3. Open TIA Portal V16, go to `Project` -> `Retrieve`, and select the `.zap16` archive.
4. Compile the project and start the **S7-PLCSIM**.
5. In Factory I/O, navigate to `File` -> `Drivers`, select `Siemens S7-PLCSIM`, and click Connect.
6. Press the "Start" button on the physical control panel inside the Factory I/O environment to initiate the sequence.

---
### 👨‍💻 About the Author
**Islam** Mechatronics Engineering Student | Passionate about Industrial Automation, Robotics Control, and writing clean, scalable PLC logic.
