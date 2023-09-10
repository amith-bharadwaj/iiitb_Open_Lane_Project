# iiitb_Open_Lane_Project
<details>
    
<summary>DAY-1</summary>

# Introduction

**OpenLane** is an open-source digital ASIC (Application-Specific Integrated Circuit) flow that automates the entire process of designing and fabricating digital chips. It is developed by efabless and Google Cloud, and it aims to democratize chip design by making it more accessible to a wider community of designers, especially for those who may not have access to expensive commercial tools.OpenLane provides a complete end-to-end flow for designing and fabricating digital ASICs. This includes steps like synthesis, floorplanning, placement, routing, and more. It also incorporates various open-source tools and libraries to streamline the process.One of the significant advantages of OpenLane is that it can work with various Process Design Kits (PDKs), including the SkyWater 130nm PDK (process design kit).

**SkyWater 130 PDK:** The SkyWater 130nm PDK, often referred to as Sky130 PDK, is a Process Design Kit provided by SkyWater Technology Foundry. It contains all the essential components, models, and data necessary for designing integrated circuits using the SkyWater Technology's 130nm CMOS process.

A **Process Design Kit** is a collection of files (such as technology files, cell libraries, and models) provided by a semiconductor foundry to enable chip designers to create layouts and designs that are compatible with the foundry's manufacturing process. It serves as a bridge between the designer and the fabrication facilities.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/95020f0b-3abc-4cbc-b0c5-a3bdb2b5508a)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/1ee989eb-7f5a-4bef-8c73-7ff665737caf)

**Foundry IPs (Intellectual Properties)** refer to pre-designed and pre-verified functional blocks or modules that are provided by semiconductor foundries for integration into custom or semi-custom integrated circuits. These IPs serve as building blocks that designers can use to construct larger and more complex integrated circuits without having to design these components from scratch.

## Open Source Digital Asic Design

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/58499c4e-3016-47ad-bcdf-632e2060ba5e)

**Open-source digital ASIC** (Application-Specific Integrated Circuit) design refers to the practice of creating custom integrated circuits using open-source tools, libraries, and methodologies. This approach aims to make the process of designing and fabricating ASICs more accessible and transparent to a wider community of designers.
Here are key aspects of open-source digital ASIC design:

**Tools and Flows:** Open-source tools like OpenROAD, Yosys, Magic, and Qflow are used to automate various stages of the ASIC design process, including synthesis, placement, routing, and verification. These tools are typically available for free and can be modified or extended by the community.

**Libraries and IP Blocks:** Open-source libraries provide a collection of pre-designed digital blocks, such as standard cells, memories, and interfaces. These can be used as building blocks for creating custom ASICs. Additionally, open-source IP cores (e.g., processors, communication controllers) are available for integration.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/4c410f2e-8cf6-481b-b98f-543a8d2f31d1)

The RTL to GDSII (Register-Transfer Level to Graphic Data System II) flow is the process of transforming a digital circuit design described in RTL (Register-Transfer Level) into a physical layout that can be manufactured as an integrated circuit. Here's a simplified explanation of the steps involved:

**RTL Design:** At the RTL level, the designer describes the behavior of the digital circuit using a hardware description language (HDL) like Verilog or VHDL.

**Synthesis:** RTL synthesis translates the behavioral RTL code into a gate-level netlist.Timing constraints are also defined at this stage.

**Floorplanning**: Floorplanning involves determining the placement of major blocks (like CPU, memory, I/O) on the chip.It considers factors like area, power, signal routing, and clock distribution.

**Placement**:Placement involves determining the precise location of each gate and flip-flop on the chip.
The goal is to minimize wire lengths and optimize for performance.

**Clock Tree Synthesis (CTS)**: CTS involves creating a well-distributed clock network to ensure synchronous operation of the circuit.
Clock signals need to reach all parts of the chip at roughly the same time.

**Routing**:This step involves creating the physical wires (metal tracks) that connect the gates and flip-flops.
Global routing defines the general path, while detailed routing refines the connections.

**Physical Verification:** This step involves checking the layout for rule violations, such as minimum spacing between wires, proper width of connections, etc.
DRC (Design Rule Checking) and LVS (Layout versus Schematic) checks are performed.
Extraction:

**Static Timing Analysis (STA):** STA verifies that the circuit meets timing requirements (setup, hold times, etc.).
It considers gate delays, interconnect delays, and clock skew.

**Final Verification:** Final checks are performed to ensure that the layout adheres to all design rules and constraints.

**GDSII Generation:** GDSII is a file format that describes the physical layout of the integrated circuit.
It includes information about layers, polygons, and other details needed for fabrication.

**Tape-Out:** The GDSII file is sent to a semiconductor foundry for manufacturing.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/6b4e55cb-23f8-4142-9440-c80b0b91876b)


</details>
