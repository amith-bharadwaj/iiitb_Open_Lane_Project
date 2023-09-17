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

## Lab Work

```
cd OpenLane
make mount
./flow.tcl -interactive

```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/4e41b51f-48fe-4a5e-8f53-5a7c6219d5e5)

```
package require openlane 0.9
prep -design picorv32a
```
### Synthesis
Type the command below to perform synthesis
```
run_synthesis
```
The report and netlist generated can be seen below.

![Screenshot from 2023-09-10 19-58-37](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/ef50e0f3-818a-4e7d-bbc5-32a7449bc222)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b125cb7e-af61-4c9f-8116-e10cdaea6eb0)


### Flop Ratio

The flop ratio can be calculated by dividing the number of D flip flops with the total number of cells.Here there are **1596** D Flip Flops and **10104**cells. Therefore the flop ratio is **0.15796**.

</details>

<details>
    
<summary>DAY-2</summary>

# Good floorplan vs bad floorplan and introduction to library cells

## Floor Planning

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/85afa22e-5cb4-4282-a0e6-db6de0dc9ebd)

In semiconductor manufacturing, floor planning refers to the initial phase of designing the physical layout of an integrated circuit (IC) on a silicon wafer. This step is crucial in organizing the various components, including transistors, resistors, capacitors, and interconnects, to optimize performance, power consumption, and space utilization.

**Block Placement:** Floor planning involves deciding where to place different functional blocks or modules on the silicon die. These blocks represent specific components like processing units, memory cells, input/output interfaces, and other specialized circuits.

**Interconnect Planning:** It encompasses planning the routes or pathways that will connect various blocks on the chip. Well-designed interconnects are essential for ensuring efficient data flow between different components.

**Power Grid Planning:** Floor planning also addresses the distribution of power across the chip. This includes determining the locations of power sources and how they will be distributed to ensure consistent and reliable power supply to all components.

**Clock Distribution:** Planning the distribution of clock signals is critical for synchronizing operations across different parts of the chip. Proper clock distribution minimizes timing issues and ensures reliable operation.

**Area Allocation:** Deciding how much physical space each block or functional unit should occupy on the die is part of floor planning. This allocation is influenced by factors like performance requirements, power constraints, and manufacturing considerations.

**I/O Planning:** Determining the placement and arrangement of input and output pads or pins is crucial for connecting the chip to external devices.

**Heat Dissipation and Thermal Considerations:** Floor planning also takes into account heat dissipation. Efficient placement of components can help manage the heat generated during operation.

**Design Constraints:** Various constraints, such as area limitations, power budgets, and performance targets, must be considered during floor planning.

**Iterative Process:** Floor planning is an iterative process. Designers often go through multiple iterations to fine-tune the layout based on simulations, performance analysis, and other considerations.

### Preplacement cells

In semiconductor chip design, "preplaced cells" (also known as "macrocells" or "hard macros") refer to predefined and fixed blocks of logic or functional elements that are placed on the chip layout before the automated placement and routing process begins. These preplaced cells are typically designed to perform specific functions and are inserted into the chip's layout in predetermined locations.

### Decoupling Capacitors

In floor planning for semiconductor chip design, decoupling capacitors play a critical role in ensuring stable and noise-free power distribution to various components on the chip. They are strategically placed in the layout to mitigate voltage fluctuations and reduce electromagnetic interference (EMI).

### Power Planning

It involves strategically organizing and distributing power supply networks across the chip to ensure reliable and efficient power delivery to all functional blocks and components. 

### Placement and Routing

**Placement**:Placement in semiconductor design is the phase where electronic components such as transistors, logic gates, and memory cells are arranged on a silicon wafer or chip. It involves selecting the locations for these components to optimize performance, power efficiency, and thermal characteristics.

**Routing**: Routing in semiconductor design is the subsequent phase that involves creating physical connections, called metal interconnects or wires, to link the placed components. These connections enable the flow of electrical signals and power throughout the chip, establishing the desired circuit connections and paths. Routing is essential for ensuring proper functionality and performance of the integrated circuit.

## LAB Work

To run floor planning, follow the below command after synthesis.

```
run_floorplan
```
after the floor planning process is completed, the def file will be generated, go to the floorplan directory and type the following command to invoke magic for viewing the layout.

```
 magic -T /home/amith/OpenLane/pdks/vsdstdcelldesign/libs/sky130A.tech lef read /home/amith/OpenLane/designs/picorv32a/runs/RUN_2023.09.11_14.44.38/tmp/merged.max.lef def read /home/amith/OpenLane/designs/picorv32a/runs/RUN_2023.09.11_14.44.38/results/floorplan/picorv32.def &
```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/4dcda57a-d609-4320-bf7e-37420eed76bf)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/e71bbc0d-2a58-45ad-9b2c-e12668db118d)

To zoom the layout,left click and right click for creating a rectangular region, press 's' for selecting and 'z' for zooming.In the console window, type 'what' after the selecting the region to get information about that component selected.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/d3f8f5cd-bb81-4042-8c3d-84bf1b3ab702)

### Placement Optimization

Optimizing placement using **repeaters** is a key strategy in integrated circuit design to enhance signal integrity over long interconnects. When critical paths exhibit signal degradation due to length, repeaters are strategically inserted to divide the path into shorter segments. This reduces signal delay, mitigates noise, and maintains signal strength. The process involves identifying long interconnects, selecting suitable repeater locations, and sizing the repeaters appropriately.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/67e06343-6e13-4899-acc3-5d6f958d8132)

### Congestion Aware Placement 
To perform the placement and view the layout, perform the following commands.

```
run_placement
magic -T /home/amith/OpenLane/pdks/vsdstdcelldesign/libs/sky130A.tech lef read /home/amith/OpenLane/designs/picorv32a/runs/RUN_2023.09.11_14.44.38/tmp/merged.max.lef def read /home/amith/OpenLane/designs/picorv32a/runs/RUN_2023.09.12_17.53.47/results/placement/picorv32.def &

```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b0da7014-3496-4439-849b-25ec690129ad)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/af23df08-d209-47a7-adc2-b458211786cb)

## Cell Design Flow

Cell design flow is the systematic process followed in semiconductor engineering to create and optimize individual functional blocks, or cells, that form the building blocks of integrated circuits (ICs).The flow typically begins with specification and architectural design, where the functionality, features, and interfaces of the cell are defined.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/108bd7de-0d04-4099-9aa8-be8615d265c9)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/6c9a93b0-390e-475f-8479-ddfbd49efa80)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/83bde8a6-bdb8-4df3-9671-ed7f49ce15aa)

## Characterization Flow

A configuration file containing models,tech files,spice netlist and simulation commands is given as input to GUNA.This software will generate timing,noise and power models.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/dee73b9b-820d-49ad-86e3-45b170ece5ef)

## Timing threshold

defintion |	Value
-------------- | --------------
slew_low_rise_thr	| 20% 
slew_high_rise_thr | 80% 
slew_low_fall_thr |	20% 
slew_high_fall_thr |	80% 
in_rise_thr	| 50% 
in_fall_thr |	50% 
out_rise_thr |	50% 
out_fall_thr | 50% 

### Propagation Delay and Transition Time 

#### Propagation Delay 

The time difference between when the transitional input reaches 50% of its final value and when the output reaches 50% of its final value. Poor choice of threshold values lead to negative delay values. Even thought you have taken good threshold values, sometimes depending upon how good or bad the slew, the dealy might be still +ve or -ve.

**Propagation delay = time(out_thr) - time(in_thr)**

#### Transition Time

The time it takes the signal to move between states is the transition time , where the time is measured between 10% and 90% or 20% to 80% of the signal levels.

**Rise transition time = time(slew_high_rise_thr) - time (slew_low_rise_thr)**

**Low transition time = time(slew_high_fall_thr) - time (slew_low_fall_thr)**

</details>

<details>
    
<summary>DAY-3</summary>

# DAY-3

## SPICE Deck Creation

A SPICE deck is a text file used to describe an electronic circuit in a format that can be interpreted by SPICE (Simulation Program with Integrated Circuit Emphasis), a widely used software tool for simulating and analyzing electronic circuits. The deck contains information about circuit components (such as resistors, capacitors, transistors, etc.), their connections, and simulation parameters. It also includes commands for specifying the type of analysis to be performed (e.g., transient, AC, DC) and other simulation settings. SPICE decks allow engineers and designers to model and predict the behavior of electronic circuits before physically building them, aiding in the design and optimization process.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/cccd8eae-e2b2-4907-9fdf-14680d341583)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/29d37e44-8196-4a08-a7f0-4f67c1301a60)

## Switching Threshold of cmos inverter

The switching threshold of a CMOS (Complementary Metal-Oxide-Semiconductor) inverter is the input voltage at which the output of the inverter transitions from a logic low (0) to a logic high (1), or vice versa. In other words, it's the voltage level at which the inverter changes its output state.

In a basic CMOS inverter, there are two transistors: a PMOS (p-type metal-oxide-semiconductor) transistor and an NMOS (n-type metal-oxide-semiconductor) transistor. When the input voltage is below a certain threshold, the PMOS transistor conducts and the NMOS transistor does not, resulting in a logic high output. Conversely, when the input voltage is above the threshold, the NMOS transistor conducts and the PMOS transistor does not, resulting in a logic low output.

The switching threshold depends on various factors including the characteristics of the transistors, the supply voltage, and the manufacturing process. It is generally determined by the Vth (threshold voltage) of the transistors, which is a parameter that characterizes the voltage at which a transistor begins to conduct.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/521a548e-3bfd-4ccc-87ea-8fecd44c0593)

## LAB Work

Follow the below commands to gitclone vsdstdcelldesign and then run magic.

```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
magic -T sky130A.tech sky130_inv.mag &
```

![Screenshot from 2023-09-16 15-02-55](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/0ddd73cf-6171-4439-8182-bc12d6e3fe55)

## Inception of Layout ( A CMOS Fabrication Process)

A 16-mask CMOS (Complementary Metal-Oxide-Semiconductor) process refers to a semiconductor fabrication process that involves 16 distinct steps (or masks) to create integrated circuits. Each mask defines a specific pattern or layer on the silicon wafer, and these patterns are built up in a series of steps to form the final integrated circuit.

Here is a simplified overview of the steps involved in a typical 16-mask CMOS process:

**Substrate Preparation:** The process begins with a silicon wafer, which serves as the foundation for the integrated circuits. This wafer is typically made of single-crystal silicon.

**Oxide Layer Formation (Mask 1):** The first mask is used to define areas where a thin layer of silicon dioxide (SiO2), also known as oxide, will be grown or deposited. This layer serves as an insulator.

**Active Region Definition (Mask 2):** The second mask defines the areas where the active components of the transistors will be located. These areas will later be doped to create the source and drain regions.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/ac4cda08-3fa8-413e-a7df-c50fa0c0c456)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/94cf5f4f-e060-4e3e-a894-2991e0edf227)

**Gate Formation (Mask 3):** This mask defines the location and shape of the gates of the transistors. The gate is typically made of polysilicon.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/7f36831c-1cc1-4b19-bf87-2dc96ac5cf57)

**Gate Insulation (Mask 4):** This step involves depositing a thin layer of silicon dioxide on top of the gate to insulate it from the channel region.

**Source and Drain Implantation (Mask 5):** Dopants are introduced into the silicon to create the source and drain regions of the transistors.

**Channel Formation (Mask 6):** This mask defines the region between the source and drain, which is known as the channel. The channel is what allows or restricts the flow of current.

**Contact Holes (Mask 7):** This step involves etching holes through the insulating layers to allow for electrical connections to the source, drain, and gate.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/fa198202-c1d5-418d-b11c-610752e791b4)


**Metal Interconnects (Mask 8):** Metal layers are deposited and patterned to form the interconnects that link various components together.

**First Metal Contact Holes (Mask 9):** Similar to Step 8, this step involves etching holes through insulating layers to allow for electrical connections to the metal interconnects.

**Metal Contact (Mask 10):** Metal is deposited to make electrical connections between the metal interconnects and the active regions of the transistors.

**Passivation (Mask 11):** A protective layer is added to shield the integrated circuits from environmental factors.

**Bond Pads (Mask 12):** Areas are defined for attaching wires that will connect the integrated circuits to external components.

**Final Metal (Mask 13):** Additional metal layers may be added for complex circuits.

**Test Structures (Mask 14):** Test structures and markers are added to facilitate testing and quality control.

**Final Inspection and Packaging (Mask 15):** The completed wafers are inspected, tested, and then diced into individual chips. These chips are then packaged for use in   electronic devices.

![Screenshot from 2023-09-16 15-47-55](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/57e0c9f3-492e-4f94-a85b-768c5c2ec418)

## Lab introduction to Sky130 basic layers layout and LEF using inverter

Inverter is, PMOS and NMOS connected together. Gates of both PMOS and NMOS are connected together and given to input. NMOS source connected to ground, PMOS source is connected to VDD.Drains of PMOS and NMOS are connected together and given to the output.From Layout, we see the layers which are required for CMOS inverter.The First layer in skywater130 is localinterconnect layer (locali).

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/e4d08cf2-79a6-4b92-86cb-e2cc047cbe7e)



