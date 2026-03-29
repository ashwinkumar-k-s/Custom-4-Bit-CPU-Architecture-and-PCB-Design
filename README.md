# Custom 4-Bit CPU Architecture and PCB Design

Designed and simulated a 4-bit microprocessor datapath using discrete logic, including an ALU, program counter, and memory units. Created full schematic and PCB layouts for all individual modules using KiCad, and successfully fabricated and tested the physical ALU board.

## 🏗️ System Architecture

This project implements a rudimentary discrete logic 4-bit processor datapath. The architecture is modularly designed, consisting of the following key components:

### Program Counter (PC)
* [Describe how the hardwired PC sequences through instructions, how it increments, and its integration with the instruction memory.]

### Instruction Memory
* [Detail the structure of the instruction memory and how the fetched instructions drive the rest of the datapath.]

### 4x4 Memory Unit
* [Explain the structure of the 4x4 memory array, how data is addressed, read/write operations, and its interface with the ALU.]

### Arithmetic Logic Unit (ALU)
* [List the specific arithmetic and logical operations the ALU can perform (e.g., ADD, SUB, AND, OR). Mention the specific logic gates or ICs used for direct connections.]

---

## 🛠️ Tools & Technologies

* **Logic Simulation:** Cedar Logic
* **Schematic Capture & PCB Layout:** KiCad
* **Hardware:** Discrete logic ICs, custom fabricated PCB

---

## 📷 Hardware Implementation & PCB Design

All functional modules were modeled, schematized, and routed as individual PCBs. The ALU module was selected for physical fabrication to validate the design in hardware.

### ALU Fabrication & Testing
![Fabricated ALU Board](link-to-your-image.jpg)
* [Briefly describe the testing process, how you verified the logic outputs, and the results of the physical ALU board.]

### KiCad PCB Layouts
![KiCad 3D Render / Routing](link-to-your-image.png)
* [Add a screenshot or two of your routed boards or 3D renders from KiCad for the un-fabricated modules (PC, Memory units) to showcase your routing capabilities.]

### Cedar Logic Simulation
![Cedar Logic Datapath](<img width="1702" height="882" alt="image" src="https://github.com/user-attachments/assets/d1a31d45-59f7-4b1e-8e1e-1cd382a2bb65" />
)
* [Add a screenshot of the full system simulation running in Cedar Logic.]

---

## 📂 Repository Structure

```text
├── simulations/          # Cedar Logic simulation files 
├── kicad_projects/       # KiCad schematics and PCB layout files
│   ├── ALU_module/
│   ├── Program_Counter/
│   ├── Instruction_Memory/
│   └── 4x4_Memory_Unit/
├── hardware_photos/      # High-resolution photos of the fabricated ALU
└── README.md
