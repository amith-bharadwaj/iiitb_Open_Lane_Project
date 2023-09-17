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

Inverter is designed by, PMOS and NMOS connected together. Gates of both PMOS and NMOS are connected together and given to input. NMOS source connected to ground, PMOS source is connected to VDD.Drains of PMOS and NMOS are connected together and given to the output.From Layout, we see the layers which are required for CMOS inverter.The First layer in skywater130 is localinterconnect layer (locali).

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/e4d08cf2-79a6-4b92-86cb-e2cc047cbe7e)

### Spice Extraction in Magic
]
Folllow the below command for creating extraction file
```
extract all
```
sky130_inv.ext file will be  created

```
ext2spice cthresh 0 rthresh 0
```
This command extracts parasatic capcitances and a file sky130_inv.spice will be created.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/16f821d2-561c-4657-9fc6-76617d62fd36)

## SKY130 Tech file labs
We should edit the spice file to do the analysis.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/381c18b4-d103-44b0-93ca-06ed3983f177)

Run it in ngspice by giving the following command.

```
ngspice sky130_inv.spice
plot y vs time a
```

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/ebb2f54f-080d-47da-9ce8-3aa0bcaa2460)
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b0e5e6ef-8b5b-4d4c-88c8-3b33e975a9f6)

## Magic DRC

Magic VLSI (Very Large Scale Integration) is a powerful open-source software tool used in the design and layout of integrated circuits. It provides a user-friendly environment for creating, editing, and analyzing electronic circuits at the transistor level. Magic VLSI offers a range of features, including a versatile and intuitive interface, the ability to handle various technology nodes, and support for both digital and analog circuit design. It also allows for the visualization of the physical layout of a chip, enabling engineers to optimize for performance, area, and power consumption. Additionally, Magic VLSI facilitates compatibility with industry-standard file formats, enhancing its interoperability with other EDA (Electronic Design Automation) tools in the semiconductor industry. Overall, Magic VLSI plays a crucial role in the development of complex integrated circuits, making it an essential tool for VLSI designers and engineers.

### Design Rule Check

DRC, or Design Rule Check, is a critical step in the process of designing integrated circuits (ICs). It is a set of predefined geometric and electrical constraints that ensure the manufacturability and functionality of the chip. During DRC, the layout of the IC is examined to verify if it complies with these specified rules. This involves checking parameters like minimum spacing between elements, width of conductors, and alignment of components. DRC helps catch potential issues early in the design process, preventing costly errors that could lead to fabrication defects or performance issues. It is an indispensable part of the semiconductor design flow, ensuring that the final chip design adheres to the requirements of the fabrication process.

### LAB Work

Follow the below commands to extract the drc test files

```
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
tar xfz drc_tests.tgz
```

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/ff448c4f-e45d-44dc-b0f7-5c4410dadb76)

let us check the files in the directory.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/7e1eb184-6856-46b0-936e-84b46f5cc5df)
Let us view the layout of met3.mag on magic
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/4962d5a7-3db4-4c5d-ad40-abc7f8477081)
In the console window give the command ```drc why ``` to know if errors are there are what are those errors associated with the selected object.
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/478e2af2-d708-4a2b-b3a2-97d1d0c431a3)
Draw a box with met3 ,move the pointer to the colour box on the right panel, use 'p' to fill the box with the selected met3 layer.
![Screenshot from 2023-09-17 10-04-32](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/855b1011-7c6b-4565-952b-b12d9add694b)
type the command ``` cif see VIA2 ```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/7d0b3202-2196-457d-8958-337983c1f445)

## Load Sky130 tech rules for drc challenges

Let us load the poly.mag file on magic layout window.     
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/d724e9bd-9ea5-4396-b861-b80774deda35)
zoom in, select the box between the contacts and type 'box' in the console window to know the dimensions. 
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/bdbdbe32-0944-4835-95d8-a1fba929da5a)
we need to modify the sky130A.tech file for making the corrections. Use gedit and modify the techfile as below.
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/48d41705-7b2e-4a64-93dc-1beab8efedef)
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b312c55a-0e4c-473d-b27a-ee52a6c38bdc)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/cce2802f-0aef-4d33-8a30-56df59b7cceb)
Now we need to reload the mag file into the magic layout window. Now we can see the modified layout.And then type ```
drc runcheck ``` in the console window.


![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/36ef0072-2723-469b-beed-9b4876124293)

open the sky130A techfile using gedit, and search for cifmaxwidth and make the changes as shown in the pictures below.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/45194eac-2ec6-4a70-ad82-452d01976e03)


Make modifictions to the tech file as shown below.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/6dc89c78-a5b6-4a40-ab68-43fac06382ba)

First create a box around cell nwell6 , Now in tkcon terminal type below commands:

![Screenshot from 2023-09-17 12-25-57](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/3ec70738-d34a-4ccf-bc6c-b0d99518d10e)



![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/944ac4a6-4bff-4eb6-adb5-2ce07b195b19)

Make modifications to the sky130A tech file as shown below.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b7214a21-094d-438a-bc97-da9e1e05fdf8)
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/cdf71df2-ebd2-46d0-be9a-4272b44df40d)

After reloading the magic layout window,run the drc commands as shown below, when we zoom in, we can find the regions having errors.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/ff8be22a-e68d-4a15-a4ea-68c92b725525)
![Screenshot from 2023-09-17 12-40-27](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/c17608a7-3856-4a39-8aed-dc89bf33b90b)

Now tap using nsubstrate contact, we can see the change in the drc value shown.
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/59c57631-43c9-4a11-a1f9-d0ff20da0ff5)

</details>
    
<details>
    
<summary>DAY-4</summary>

    
# Timing Analysis and Clock Tree Synthesis

## Grid into Track Info

To implement our own stdcell,the inout output ports must lie on the intersection of Horizontal and vertical tracks and
Width and Height of standard cell are odd mutliples of Horizontal track pitch and Vertical track pitch.
Give the below command to view grids of specific dimensions on layout.
```
grid 0.46um 0.34um 0.23um 0.17um
```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/58142b9b-96b2-45f0-8a80-1db223df3236)

## Creation of Port Defination

After loading the inverter design, select the required port by double pressing 's' in the region.click on edit and then text.Here we can enter the label.Ensure to check the enable check box.
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/e53a7284-a749-4f3f-9f8f-614951372f1d)

## Setting port class and port use attributes

Type the following commands in the console,enter 2 commands at a time after selecting input,output,vdd and ground ports respectively.

```
port class input
port use signal
port class output
port use signal
port class inout
port use power
port class inout
port use ground
```
To generate the lef file, follow the below command.
```
lef write

```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/9ea3fd4e-29db-4b44-b327-0c2d32dc4f02)

Copy the lef file,sky130_fd_sc_hd_typical.lib, sky130_fd_sc_hd_slow.lib, and sky130_fd_sc_hd_fast.lib files from the libs folder in vsdstdcelldesign to the src folder of picorv32a. And then we need to modify the config.tcl file.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/5359e327-2fa8-474d-8fb3-cd43fc26641f)

Follow the below commands in openlane to run synthesis.

```
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/81606d21-9b2f-4c13-9d60-15f656e1ed91)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/9b8979ab-7fab-4c9a-bd68-e37ddd09b258)

## Delay Tables

Timing is a pivotal parameter that holds significant sway over our cell designs, influencing all other aspects of timing considerations. The delay of a cell is contingent on factors such as input transition and output load. For instance, when a cell (X1) is situated at the end of a lengthy wire (Scenario 1), its delay is affected by unfavorable transitions due to the wire's resistance and capacitance. Conversely, in the case of a shorter wire (Scenario 2), the delay differs as the transition is less adverse. This demonstrates the sensitivity of delay to varying conditions, even for identical cells. Additionally, the output load also plays a role in shaping delay characteristics. To maintain signal integrity during buffer insertion, VLSI engineers have established specific guidelines, emphasizing consistent buffer sizing at each level. Despite this, delays may fluctuate depending on the load they drive. To address this, engineers introduced "delay tables," which contain 2D arrays encompassing input slew and load capacitance values, each associated with various buffer sizes. These tables serve as essential timing models for the design process. Algorithms interact with these tables, using provided input slew and load capacitance values to calculate corresponding delay values for the buffers. In cases where precise delay data is unavailable, interpolation techniques are employed. These techniques identify the nearest available data points and extrapolate from them to estimate the required delay values.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/c12ca424-a636-46de-a95f-af4bd0f999bd)

Let us perform floor plan and placement.

```
run_floorplan
run_placement
```
Let us invoke magic from the results/placement directory

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/35bb6f08-f83b-4a70-8438-ad89f5793dce)

## Timing Analysis

Setup time is a crucial concept in digital electronics and refers to the minimum amount of time that a data input signal must be stable and valid before the clock signal arrives for the flip-flop or latch to capture that data. In simpler terms, it is the time duration between when the input data is available and when the clock edge arrives, ensuring that the data is correctly registered by the flip-flop or latch. Failing to meet the setup time requirement can result in erroneous or unpredictable behavior in the digital circuit. It's a fundamental parameter for ensuring reliable operation of synchronous digital systems.

Metastability is a phenomenon that can occur in digital electronic circuits, particularly in synchronous systems. It arises when a digital flip-flop or latch receives a signal that arrives very close to the clock edge. In this narrow time window, the signal may oscillate unpredictably between the high and low states, causing the flip-flop or latch to have difficulty in determining the correct state to latch onto.

Designers take measures to minimize the likelihood of metastability by ensuring that signals meet setup and hold time requirements and by using techniques like synchronizers to reduce the probability of metastable events. However, it's important to note that metastability is an inherent part of digital electronics and can never be entirely eliminated, only managed.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/f1c3eb96-63ed-45db-9e53-0f3128977e64)

### Clock Jitter

Clock jitter is a phenomenon in digital systems that refers to the variations in the timing of a clock signal. It is characterized by small, random fluctuations in the arrival times of clock edges. These fluctuations can occur due to various factors, such as electronic noise, power supply fluctuations, and imperfections in the clock generation circuitry. Clock jitter can have significant implications for the performance of digital circuits, as it can lead to timing uncertainty and ultimately affect the stability and accuracy of data processing. Designers employ techniques like jitter reduction circuits and high-quality clock sources to mitigate the impact of jitter and ensure reliable operation of digital systems. Managing clock jitter is especially crucial in high-speed and precision applications, where precise timing is paramount.


![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/0f04283f-369f-48da-a32b-a4e7296e271e)


## Clock Tree Synthesis (CTS)
Clock Tree Synthesis (CTS) is a crucial step in the physical design of integrated circuits (ICs), especially for synchronous digital systems. It involves the generation of an optimized network of clock distribution lines (referred to as the "clock tree") that evenly and efficiently distributes the clock signal to all sequential elements (like flip-flops) across the chip.

Here's a breakdown of the key steps involved in Clock Tree Synthesis:

**Clock Signal Generation:** The first step is generating the primary clock signal, usually from an external crystal oscillator or a phase-locked loop (PLL). This signal serves as the reference clock for the entire system.

**Buffer Insertion:** The clock signal from step one is generally weak and may not be able to drive all the sequential elements in the design directly. Therefore, buffers (usually in the form of inverters) are inserted strategically along the clock path to strengthen the signal.

**Clock Distribution Network:** This step involves creating a network of clock lines that originate from the clock source and spread out across the chip, reaching every sequential element. The goal is to minimize clock skew (variation in arrival times of the clock signal) and ensure that all elements receive the clock signal simultaneously.

**Balancing Delays:** The clock tree synthesis tool considers factors such as wire lengths, resistance, and capacitance to balance the delays in the clock distribution network. This ensures that the clock arrives at all elements at the same time, reducing setup and hold time violations.

**Optimization for Power and Area:** CTS tools aim to minimize power consumption and area usage while maintaining good clock distribution characteristics. This may involve techniques like buffer sizing and placement optimization.

**Clock Gating:** In some designs, clock gating elements are added during CTS. These elements can selectively enable or disable clock signals to specific parts of the design, conserving power when those parts are not in use.

**Verification and Analysis:** After generating the clock tree, it's crucial to perform extensive verification and analysis. This includes checks for clock skew, setup and hold time violations, and power consumption.

**Iterative Process:** Clock Tree Synthesis is often an iterative process. Designers may need to make adjustments to the clock tree, such as buffer insertion or resizing, to meet timing and power constraints.

### Cross Talk

Cross talk in VLSI (Very Large Scale Integration) refers to the unwanted interference or coupling of signals between adjacent conductors or traces on a printed circuit board (PCB) or within an integrated circuit (IC). This interference can lead to incorrect or degraded signal integrity and can potentially result in malfunctions or errors in the functioning of the circuit.

Cross talk can lead to various issues:

**Signal Degradation:** The interference can distort the original signal, potentially making it difficult for the receiver to correctly interpret the data.

**Timing Violations:** Cross talk can lead to timing violations, where signals may arrive at the receiver with incorrect timing, violating setup and hold time requirements.

**Increased Noise:** The interference can introduce additional noise into the system, reducing the signal-to-noise ratio and potentially leading to errors.

**Reduced Signal Integrity:** In extreme cases, cross talk can lead to complete signal integrity failure, resulting in malfunctioning of the circuit.

### Clock Net Shielding

Clock net shielding is a technique used in VLSI (Very Large Scale Integration) design to minimize the interference and cross talk that can occur between the clock signal and other adjacent signal traces on a printed circuit board (PCB) or within an integrated circuit (IC). It involves physically isolating the clock signal traces from other signal traces by placing a shield, typically a metal layer, between them. This shield acts as a barrier, reducing the capacitive and inductive coupling that can occur between neighboring traces. By implementing clock net shielding, designers can improve the integrity and reliability of the clock signal, ensuring that it reaches its destination with minimal distortion or interference, which is critical for the proper functioning of synchronous digital systems.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/c26eda2c-3647-4816-a7fe-6749c35bae81)

## LAB Work
```
run_cts
```
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/8a26df72-22ba-453e-9103-ebd0a65e5176)

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/2027a709-0daf-48b9-94c3-4916e88cb332)

Here we can observe that there is no violation.From now on post cts analysis is performed by openroad within the openlane flow .In openroad, execute the following commands
```
openroad
read_lef <path of merge.nom.lef>
read_def <path of def>
write_db pico_cts.db
read_db pico_cts.db
read_verilog /home/parallels/OpenLane/designs/picorv32a/runs/RUN_09-09_11-20/results/synthesis/picorv32a.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
read_sdc /home/parallels/OpenLane/designs/picorv32a/src/my_base.sdc
set_propagated_clock (all_clocks)
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
Here below we can see the hold and setup slack.

![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/b70f371d-caac-42f8-a434-3bfa15993d46)
![image](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/4b6dcaf0-e2b8-4bdd-9290-dab55f79d49f)

</details>

<details>
    
<summary>DAY-5</summary>

Maze routing is a method used in electronic design automation (EDA) and integrated circuit (IC) routing to find a path for interconnects (wires or traces) between different components on a chip. The term "maze" refers to the grid-like structure that represents the routing area.

Lee's algorithm, also known as Lee's Wave Algorithm, is a widely used algorithm for maze routing. It's named after its creator, Chung Laung Lee. Here's an explanation of both concepts:

**Maze Routing:**

In electronic design, the routing phase involves establishing connections between various components like transistors, gates, and other functional blocks. This is done using metal traces or wires that carry signals between these elements. Maze routing deals with finding an optimal path through a maze-like grid of obstacles to connect a source point to a destination point.

**Lee's Algorithm:**

Lee's algorithm is a path-finding algorithm used in maze routing. It's a breadth-first search (BFS) based algorithm. The basic idea is to start from the source point and explore the adjacent cells in layers, expanding outward until the destination point is reached. The algorithm works as follows:

**Initialization**: Mark the source cell with a value of 0. Then, mark all adjacent cells with a value of 1, and continue this process, incrementing the value by 1 for each layer of adjacent cells.

**Wave Expansion:** Propagate the wavefront outwards from the source cell, incrementing the value of each cell as the wavefront expands.

**Routing:** Once the wavefront reaches the destination cell, follow the decreasing values back from the destination to the source, which traces the optimal path.

![Screenshot from 2023-09-17 19-24-35](https://github.com/amith-bharadwaj/iiitb_Open_Lane_Project/assets/84613258/a8fa8ce3-2f11-4c49-b755-9da501df488c)

## Design Rule Check

Design Rule Checking (DRC) is a crucial step in the process of designing integrated circuits (ICs) and other electronic devices. It involves a thorough examination of the layout or design of a chip to ensure that it adheres to a set of predefined rules and constraints specified by the semiconductor fabrication process. These rules encompass various aspects, including minimum feature sizes, spacing between elements, metal layer configurations, and other geometric constraints. The purpose of DRC is to catch and rectify potential errors or violations that could lead to fabrication issues or electrical malfunctions. It serves as a quality control measure to guarantee that the design meets the precise specifications required for successful manufacturing and reliable performance of the final IC.

## Power Distribution Network


    
</details>
