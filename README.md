# Custom 4-Bit CPU Architecture and PCB Design

Designed and simulated a 4-bit microprocessor datapath using discrete logic, including an ALU, program counter, and memory units. Created full schematic and PCB layouts for all individual modules using KiCad, and successfully fabricated and tested the physical ALU board.

## System Architecture

This project implements a rudimentary discrete logic 4-bit processor datapath. The architecture is modularly designed, consisting of the following key components:

### Program Counter (PC)
* 2 Bit Counter using D-Flip Flop to cycle between 4 instructions

### Instruction Memory
* A network of 8 4x1 MUXs to obtain an instruction of 8 bit wide and have 4 instructions at a time loaded.
 <img width="1172" height="723" alt="8x4_instruction_memory" src="https://github.com/user-attachments/assets/534adb8c-a73f-4ece-8d7d-ab9b67676e22" />


### 4x4 Memory Unit
* Consists of 4 2x4 Decoders, 4 4-Bit Registers and 4 4x1 MUXs.
* 2x4 Decoder : Used to load values into the register, controlled using Enable signals while in write mode.
* 4-Bit Register: Receives data from Decoders, interconnected as, all Bit-0s from decoder to Register-1, all Bit-1s from decoder to Register-2, all Bit-2s from decoder to Register-3, all Bit-3s from decoder to Register-4.
* 4x1 MUX: Used to read data from the register when in read mode, similar interconnect network as instruction memory.
  <img width="1501" height="757" alt="4x4_memory_unit" src="https://github.com/user-attachments/assets/8dcbfad7-620c-49f1-9078-1c7a9e718b2f" />


### Operand controller
* Complementary pair of Tri-State Buffers connected to both Registers containing operand A and B
  <img width="537" height="575" alt="operand selector" src="https://github.com/user-attachments/assets/c0420d31-8963-4186-b572-249f4cab5c6b" />


### Arithmetic Logic Unit (ALU)
* Could do 7 operations AND, OR, XOR, ADD, SUB, ROR, ROL.
* AND, OR, XOR operations are directly computed from the received inputs directly using dedicated ICs.
* ADD and SUB is done in a single circuit consisting of 2 Full adders and a XOR IC, where ADD = A+B and SUB = A + 2's complement(B).
* Rotate operations ROR (right) and ROL (left) is done with a 4-bit barrel shifter(used to shift in a single clock cycle).
  <img width="940" height="685" alt="4_bit_alu" src="https://github.com/user-attachments/assets/cbfbb5d0-6218-42a8-a79e-0661a9e79f8a" />


### Output Control Unit
* All the outputs are simultaneouslly calculated in the ALU,
* Each output is 4-Bit wide and is connected to a dedicated set of 4-Bit Tri-state buffers controlled using a 3x8 Decoder to output the desired value.
  <br>
  <img width="562" height="400" alt="output_control_unit" src="https://github.com/user-attachments/assets/6316ea8e-ceb6-4189-b219-b9f69c8fc3f4" />


---

## Tools & Technologies

* **Logic Simulation:** Cedar Logic
* **Schematic Capture & PCB Layout:** KiCad
* **Hardware:** Discrete logic ICs, custom fabricated PCB

---

## Hardware Implementation & PCB Design

All functional modules were modeled, schematized, and routed as individual PCBs. The ALU module was fabricated in PCB and the rest were validated in breadboard circuitry.

### Hardware implementation of 4x4 Memory unit 
<img width="590" height="443" alt="image" src="https://github.com/user-attachments/assets/b88d19f6-d0a5-4e5e-a38f-ee0642eb24da" />
<br>

* 4 4x1 MUXs - 74LS153.
* 4 4-Bit Registers - 74LS173.
* 4 2x4 Decoder - 74LS139.
<br>

<img width="706" height="765" alt="image" src="https://github.com/user-attachments/assets/0d5ccc57-5ca1-4e82-85e3-f213e0f25900" />
<br>

### Hardware implementation of Memory Data Register (Operand Selector)
<img width="605" height="295" alt="image" src="https://github.com/user-attachments/assets/321f2755-517f-4105-aeb0-a5cd7ab2b6bc" />
<br>

* 3 4-Bit Registers - 74LS173.
* 1 8xTri-State Buffers - 74LS244.
* 1x2 Decoder made using AND and NOT ICs.

### ALU implementaion in PCB
![alu pcb_re](https://github.com/user-attachments/assets/b637865c-1cce-4273-bef4-7d1d298be97b)
<br>

* AND - 7408.
* OR - 7432.
* XOR - 7486.
* 4-Bit Full Adder - 7483.
* 4x1 MUX - 74153.
<br>

<img width="761" height="786" alt="image" src="https://github.com/user-attachments/assets/6c7a6a8e-eb4d-4a47-869f-2b247f65b83d" />
<br>

### Output Control Unit
![output control](https://github.com/user-attachments/assets/ee683840-45fa-457b-9afc-7a81f8c8bdb8)
<br>

* 3x8 Decoder - 74138.
* 7 4-Bit Registers - 74173.
<br>

![alu_full](https://github.com/user-attachments/assets/52c0fcec-a940-4eb1-a0d0-468a43847b87)

<br>

### KiCad PCB Layouts
<img width="1150" height="1083" alt="image" src="https://github.com/user-attachments/assets/bfd3fe66-0835-46bd-9cb5-679028c6c8a6" />
<br>

<img width="1090" height="524" alt="image" src="https://github.com/user-attachments/assets/3d923681-9837-4f2f-95d0-f30ad8bfe763" />
<br>

* PCB Layout of Memory Unit
<br>

<img width="1245" height="873" alt="image" src="https://github.com/user-attachments/assets/80e93dba-5849-4542-9ae0-1c27dba7ece5" />
<br>

<img width="1121" height="403" alt="image" src="https://github.com/user-attachments/assets/cce30211-63d3-4231-b995-cf05f184cbe2" />
<br>

* PCB layout of ALU
<br>

<img width="1523" height="361" alt="image" src="https://github.com/user-attachments/assets/ff991347-417f-49bf-80a0-c8bce274421f" />
<br>

<img width="990" height="543" alt="image" src="https://github.com/user-attachments/assets/8088f4dc-6445-4a0c-a571-9efc7385440f" />
<br>

* PCB layout of Output Control Unit

### Cedar Logic Simulation
<img width="1666" height="885" alt="4-bit cpu" src="https://github.com/user-attachments/assets/b5f69f88-e5ab-4eb6-90c6-ba9281d835d4" />
<br>

---

## Repository Structure

```text
├── simulations/          # Cedar Logic simulation files
│   ├── full_layout 
├── kicad_projects/       # KiCad schematics and PCB layout files
│   ├── Output_control_unit/
│   ├── ALU_module/
│   └── 4x4_Memory_Unit/     
└── README.md
