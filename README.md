# Advanced-Physical-Design-Using-OpenLANE-Sky130

The workshop deals with the whole process of ASIC design using open source EDA tools. The whole process of ASIC design is stated in the image below.

![ASIC process](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a0ffda01-d37b-41e9-b701-2b8c85c140fb)

# Table of Contents

[Day 1](#day-1)

[Day 2](#day-2)

[Day 3](#day-3)

[Day 4](#day-4)

[Day 5](#day-5)

# Day_1 Inception of Open-Source EDA, OpenLANE & Sky130PDK

<details>
 <summary> How to Talk to Computers
 </summary>


How to Talk to Computers

Inception of open-source EDA, OpenLANE and SKY130PDK

Basic terminologoies

1. **PADS**- A pad is the exposed region of the metal on a circuit board that the component lead is soldered to. Pads are the points through which connection of peripherals on a board is made with the chip/porcessor, and transfer of data takes place.

2. **Foundary IP's**- A foundry is a company that provides IC (integrated circuit) manufacturing services - basically, you give them your design, and they manufacture the chip for you. Intellectual Property. In this context, it’s the design for the parts of a chip. Nowadays, many chips are not wholly designed by the company that’s “designing” them. For example, in a typical mobile phone application chip:

   * The main CPU will probably be bought as IP from ARM.
   * The graphics processor (GPU) will be bought from one of a number of companies (e.g. ARM, Imagination Technologies, etc.)
  
The company “designing” the chip will take these IPs, combine them with some more stuff of their own design, and then send the whole thing off to the foundry for manufacturing. Now, there are a number of foundries (the main ones are TSMC, UMC and GlobalFoundries). They each make chips in slightly different ways, meaning that their processes are different.

3. **Core**- A core in a chip is a well-partitioned piece of logic capable of independently performing all functions of a processor. All the logic building blocks are present here.

4. **Macros**- Macro is an essential component in the VLSI design cycle before the final packaged chip is ready to use. Macro cells are the memory cells, intellectual property which an analog design team has designed. To break down the understanding of macro cells, consider macro cells as pieces of logic blocks, mainly intellectual properties (IP), which can be used in a design without the need to (of) building them from scratch. Thus, these memory cells are instrumental in reducing the total time for the design engineers that is required to complete their entire design.

5. **PDK**- PDK stands for Process Desgin Kit, its an interface between FAB and the designers, its a collection of files used to model a fabrication process for the EDA tools used to design an IC. Apart from this a PDK consists of

   * Process design rules i.e DRC
   * Device models
   * Digital Std. cell library
   * I/O library 

The layout of RISCV processor is shown below.

![Screenshot (84)](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7fc8f83d-d54d-4eba-ac3a-e3f3284808f4)

A generic view of IC is shown below

![Screenshot (85)](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b9557c3c-a619-4921-a992-8f7bf8547af7)

</details>

<details>
 <summary> SoC Design & OpenLANE
 </summary>

SoC Design & OpenLANE

The following are the the three important parameters needed to design a ASIC chip.

1. **RTL IP's**- RTL IP stands for Register Transfer Level.1 It refers to a product in electronic format that represents an integrated circuit function that can be instantiated in an integrated circuit design. An IP Core is a product in electronic format that represents an integrated circuit function that can be instantiated in an integrated circuit design, including the circuits and modules of such integrated circuit design(s) and associated firmware, application programming interfaces, Software drivers, application-specific Software, and all register transfer language (RTL), verilog, and other source materials to instantiate, modify, support, and maintain any of the foregoing.

2. **EDA Tools**- Electronic Design Automation (EDA) tools are software tools used to design electronic systems such as integrated circuits and printed circuit boards. They have three key functions: simulation, design, and verification. EDA tools work together in a design flow that chip designers use to design and analyze entire semiconductor chips. They allow teams to predict circuit behavior, assemble circuit elements, and anticipate chip performance. EDA tools are used to verify that a design will meet all the requirements of the manufacturing process, known as design for manufacturability (DFM). Deficiencies in this area can cause the resultant chip to either not function or function at reduced capacity, and there are reliability risks.

3. **PDK Data**- PDK data consists of primarily
   
   * Process design rules i.e DRC
   * Device models
   * Digital Std. cell library
   * I/O library 

**Simplified RTL to GDSII flow.**

The overall process of RTL to GDSII flow is show below, followed by elaboration of each step.

![RTL to GDSII flow](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/cc1e82e0-bbdc-41ad-bff6-5a73550b1947)


1. **Synthesis**- Converts RTL to a circuit out of components from the standarad cell library(SCL).
   
![Synthesis](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/541a0914-e788-43a0-80c8-40f94415bab3)

2. **Chip Floor planning**- Partition the chip die between different systems building blocks and place the I/O pads.

![Floor Planning ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/892adc06-336c-4c3f-a4b9-4f4fedd5ff7e)

![macro floor planning](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5653ddf2-81c7-4158-9ee9-ad45aea6048f)

![Power planning](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5be5357b-dfd4-4038-95f8-a72b5c611674)

3. **Placement**- Place the cells on floor plan rows, aligned with the sites. Typically done in two steps i.e. Global & detailed 

![Power planning](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/28fc184a-6e17-4ce7-aa8c-231981f103a4)

4. **Clock Tree Synthesis**

![CTS](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/3e4fc5b6-cd6f-41b9-86aa-b1e4f9c41c7d)

5. **Routing**

![Routing ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7c001364-1be4-4392-a5e7-b22bd3b0f751)

![routing2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/15312715-e42e-4df9-9e34-8b6ed18ca9a0)


6. **SignOff**

    ![Signoff](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/3c834724-f524-455b-91cd-6536e4429487)

   **Challenges in ASIC design through Open source softwares**

   1. Tools Qualification
   2. Tools Calibration
   3. Missing Tools

   **Introduction to OpenLANE**

* Started as an Open-Source Flow for true Open source Tape-Out experiment.
* Strive is the family of open source everything SoCs,
  OpenPDK, Open EDA, Open RTL.

![Strive Family](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/4fad51fa-c834-49b4-9df5-61e35f158dce)

* Obejective of OpenLANE is to produce a clean GDSII with no human intervention, i.e No LVS violations, No DRC violations, Timing viloations
* It is tuned for SkyWater 130nm Open PDK, also supports XFAB180 and GF130G
* It is containarized
  * Functional out of the box
  * Instructions to build and run natively will follow.
* Can be used to harden Macros and chips
* Two modes of operation
  * Autonomous & Interactive
* Design space expolration
  * Find the best set of flow configuration
* Large number of design exmaples
  * 43 Designs with their best configuration and more details to be addedd
 

**Introduction to OpenLANE detailed ASIC design flow**

The below image represents the steps involved in OpenLANE ASIC design flow

![ASIC flow openlane](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b81d4a24-2f26-4d08-9219-b5bad001de0f)

The base of Openlane is formed through several opensource projects few of them are listed below in the image

Each tool is used to perform a task at different level of design flow.

![based openlane](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/9af60d72-53a8-4a06-bbdb-3e4ad9877a4f)

1.**Synthesis Exploration**

This step involves generation of reports, different design can use different approach to achieve the objective for that we have systhesis exploration.

![Synth Exploration](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/11bbc2a3-00d0-42a5-834a-02b1b8d15a00)

2. **Design Exploration**

This step is used to sweep the design configuration, its very useful in finding best configuration for openLANE for any given design. A sample of generated report is shown below

![design exploration](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/289a8a9f-ca12-4906-8b6e-6f60566d1380)

3.**OpenLANE regression testing** 


![openlane reg testing](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/74ccf1eb-5153-403e-94bf-4d81cebfe633)

4. **Design for test**

The following step is performed using fault. 

![DFT](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ef3b3b5d-f641-4846-b4d8-d4b5db9cb613)

5. **Physical implementation**

 Involves several steps given in the image below, all the steps is performed using openRoad.

 ![Physical Verification DRC   LVS](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/395907a8-0ac1-460e-bf2c-d59c928355ac)


 6. **Logic Equivalence check**

LEC is very important step in flow of ASIC design, its basically checking logic synchronisation between physical implementation, and netlist generated using Yosys. 

![LEC ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/175d95cf-9638-4b02-8d3c-dfbcc789295d)

7. **Dealing with Antenna rules violations**

![Antenna rules violations ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/99350095-3d0b-44b7-a2c8-6ab8560ea747)

The above problem of wire acting as antenna is resolved through 

![Antenna solns](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/677f2657-31c8-450f-8073-5448d979dc5e)

![openlane soln for antenna viol](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7a83275e-08ff-4b32-ad0a-dd5944a3455d)

8. **Static Timing Analysis**

Static Timing Analysis (STA) is a technique used to validate the timing performance of a design by checking all possible paths for timing violations. It breaks a design down into timing paths, calculates the signal propagation delay along each path, and checks for violations of timing constraints inside the design and at the input/output interface. STA does not depend on any data or logic inputs, applied at the input pins. The input to an STA tool is the routed netlist, clock definitions (or clock frequency), and external environment definitions.

![STA ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e1acf762-f38b-480e-b0a0-b13dae8c6183)

</details>

<details>
 <summary> Getting Familiar to opensource EDA tools
 </summary>
 
**OpenLane Installation**
 
**Step 1- Installation of required packages**

```
sudo apt-get update
sudo apt-get upgrade
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```

**Step 2-Docker Installation**

```
# Remove old installations
sudo apt-get remove docker docker-engine docker.io containerd runc
# Installation of requirements
sudo apt-get update
sudo apt-get install \
   ca-certificates \
   curl \
   gnupg \
   lsb-release
# Add the keyrings of docker
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
# Add the package repository
echo \
   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
# Update the package repository
sudo apt-get update

# Install Docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin

# Check for installation
sudo docker run hello-world

```

**Step 3-Installing OpenLANE**

```
git clone https://github.com/The-OpenROAD-Project/OpenLane
cd OpenLane
make
make test

```
The following image shows the installation of openlane

![OpenLane](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b8f93fc6-64fb-42e9-b2a0-06c74a81b3be)

Tools Available in Openlane Folder


![tools available](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ac2ab737-8a74-4ac8-a0e2-c16a2fa1f52b)

Now we will run synthesis

```
run_synthesis

```

![Synthesis SS](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/9b942dc2-67d0-4a03-ac46-7676a39880c1)

The synthesis Timing report is as followed

![log file 1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ffd6cb0e-d442-46b8-9f19-199edbdded2b)

The synthesis power report is as follows

![power log file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ccbb3fef-c4b3-4569-846e-ba5995e7ed4d)

</details>


 # Day_2 Good Floor plan & bad floor plan & Introduction to library cells

  <details>
 <summary> Chip Floor Planning Considerations
 </summary>

**Chip Floor Planning Considerations**

**Die**- A die which consists of core is a small semiconductor material specimen on which the fundamental circuit is fabricated.

![Die ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/39d31df3-4436-4053-9d49-2b4b6bb3f9ef)


**Utlisation Factor** == Total area occupied by the netlist / Total area of the core. 

Usually the utlisation factor is around 0.5 to 0.6. 

**Aspect ratio**-- Height of core / Width of core

![utlisation factor](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/915820fa-af9a-468a-b4de-bfb7a71e4343)

**Concept of Pre-placed cells**

**Pre-Placed cells**- There are few IP's/blocks have user defined locations, and hence placed in chip before automated placement and routing and are called preplaced cells.

**Floor Planning**- The arrangement of these IP's in a chip is refered as floor planning.

Automated placement and routing tools places the remaning logical cells in the design onto the chip.

**Decoupling Capacitor**- 

Decoupling capacitors are essential components in electronic circuit design that help maintain a stable power supply, filter out noise, and improve the overall performance and reliability of electronic systems, particularly in digital and mixed-signal applications. Proper selection, placement, and sizing of decoupling capacitors are critical for their effectiveness in reducing noise and maintaining voltage stability.

![decoupling cap](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/944d547d-3008-4fb1-9da4-f170ec5b276d)

![decoupling cap 2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/9dda34a1-4168-4d63-965c-f2f5c55d0663)

**Noise Margin** 

Noise margin is a concept used in digital electronics and integrated circuit (IC) design to quantify the tolerance of a digital signal to noise and voltage variations. It provides a measure of the robustness of a digital circuit by defining the range of acceptable voltage levels for logic values (0 and 1) and ensuring that signals can be reliably interpreted in the presence of noise. Noise margin is typically expressed in terms of voltage or voltage range.


![noise margin](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/df6ae763-87d0-451b-b718-90c615ca5728)

**Power Planning**
Power Planning in integrated circuit (IC) design is a crucial aspect of ensuring proper power distribution to various components on the chip. While pre-placed macros (blocks) may have dedicated decoupling capacitors (decaps) for noise filtering and stabilization, the entire chip can't have individual decaps. To address this, effective power planning involves creating a network of VDD (power supply) and VSS (ground) pads for each block, strategically connecting them to horizontal and vertical power and ground lines. These lines form a power mesh, which acts as a distributed power delivery network. This approach ensures that each block receives a stable and clean power supply, reducing noise and voltage fluctuations, and contributes to the overall reliability and performance of the integrated circuit. The power mesh effectively distributes power throughout the chip, preventing voltage drops and ensuring consistent operation of all blocks.

**Ground bump**- When n numbers of capacitors discharge at the same time, there would be a disturbance of voltage at the ground, shown in the picture below, if the ground bump is within noise margin its fine but if it exceeds then it would lead to some random value in the circuit.

![ground bump](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/8eaf2eea-3251-4869-bd19-09346d7c9f12)

**Voltage droop**- When n numbers of capacitors charge at the same time, there would be a disturbance of voltage at the power supply, indicate in the picture below

![voltage droop](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/82e7767b-fff0-4843-ad5c-da7a8792ce26)

**Pin Placement**
Pin Placement in integrated circuit (IC) design involves determining the physical locations of input and output (I/O) pins that connect to the logic gates within the chip.
The netlist specifies how the logic gates within the chip are interconnected. It provides information about which gates are connected to one another and how signals flow through the design.
After the I/O pad positions are determined, the design process includes logical placement blocking of pre-placed macros. This step involves arranging pre-placed macros (blocks of predefined logic) in a way that distinguishes them from the area reserved for the I/O pins. This separation ensures that the macros do not interfere with the connectivity and signal paths associated with the pins.

**Generating the floor using Magic**

To generate the floorplan following commands is used 

```
run_floorplan

```
## Initial Place Design

Optimize Placement Using Estimated Wire Length And Capacitance representation is shown below in the image:

![initial place design](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/d3ab7403-b451-4d12-b2dc-b1b6423250c0)

```
run_placement
```

Following process shown in the image will run in the terminal

![commands to generate floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a6e0de31-21ae-4954-82ad-957e348e2c60)

Now to view the generated floorplan, I invoked magic in the directory where the floorplan is present

```
cd /home/divyam/OpenLane/designs/picorv32a/runs/RUN_2023.09.09_13.22.30/results/floorplan/
```

Invoking magic 

```
 magic  /home/divyam/.volare/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.min.lef def read picorv32.def
```

Below shows the commands runned in the command

![magic invoke](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/6dba6fe5-fb90-4683-9a52-2b686470b4fe)

The floorplan is shown below

![floorplan basic](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/9cbc9460-6196-40dd-bdc7-da4e1e46a6cf)

To **zoom in** the floor plan press Z, below is the zoomed image of the floorplan

![zoomed floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ccd2a5d4-700c-44d7-80de-b4d5a75d6982)


To **zoom out** the floor plan press shift+Z, below is the zoomed image of the floorplan

</details>

<details>
 <summary> Library Binding and Placement 
 </summary>

**Netlist binding and initial design**
 
**Library** consists of cells, shapes & sizes of cells, various flavours of the same cell, timing/delay information.

The netlist or the circuit is made using the component available in library, where each element is represented as a box.

![lib to netlist](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/4887d41c-a227-47df-b30a-c92b8a800019)

**Placement** is the process of placing the cells in the core area of the chip as shown below. 

The next step in the OpenLANE ASIC flow is placement. The synthesized netlist is to be placed on the floorplan. Placement is perfomed in 2 stages:

1.Global Placement: It finds optimal position for all cells which may not be legal and cells may overlap. Optimization is done through reduction of half parameter wire length.

2.Detailed Placement: It alters the position of cells post global placement so as to legalise them.

![netlist_placement](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e40e5c6c-a71d-454e-8cba-4b24530cc44b)

**Need for librabries and characterisation**

**Library characterization** is the process of characterizing electronic components and gates, such as logic gates, flip-flops, and other building blocks, to create models that accurately represent their behavior under various conditions. This characterization provides information about how components respond to different inputs, delays, power consumption, and more.

**Library modeling** involves creating mathematical or algorithmic representations of the behavior and characteristics of components. These models are used by EDA tools to simulate, analyze, and optimize digital circuits during the design phase.

![PROCESS](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/40c9befb-f387-4038-af20-02d250d4936a)

![NEED FOR LIBRARY](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/98fc611c-0d59-47cb-8869-ef3fca4c9500)

**Logic synthesis** is a crucial step in the design of digital integrated circuits (ICs) and plays a central role in transforming a high-level hardware description into a gate-level representation that can be fabricated in silicon.

**Floorplan** is one the critical & important step in Physical design. Quality of your Chip / Design implementation depends on how good is the Floorplan. A good floorplan can be make implementation process (place, cts, route & timing closure) cake walk. On similar lines a bad floorplan can create all kind issues in the design (congestion, timing, noise, IR, routing issues). A bad floorplan will blow up the area, power & affects reliability, life of the IC and also it can increase overall IC cost (more effort to closure, more LVTS/ULVTS).

**Placement** is the process of determining the locations of circuit devices on a die surface. It is an important stage in the VLSI design flow, because it affects routabil- ity, performance, heat distribution, and to a less extent, power consumption of a design.

**Clock Tree Synthesis** is a technique for distributing the clock equally among all sequential parts of a VLSI design. The purpose of Clock Tree Synthesis is to reduce skew and delay.

**Routing** in VLSI is making physical connections between signal pins using metal layers. Following Clock Tree Synthesis (CTS) and optimization, the routing step determines the exact pathways for interconnecting standard cells, macros, and I/O pins.

**Optimise placement using estimated wire length and capacitance**

**Repeaters**- Element introduced in the core area to maintain the signal integrity.
The below image shows how the repeaters are placed in the core 

![final repeaters](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5a2f396e-9ac9-4fb4-b407-14480a4b468e)



**RUN Placement in openlane**

Following command was used 

```
run_placement
```

![wsl run placement](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/481599a1-bf1a-411c-9599-58d08436c5e3)

![placement xoomed](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/68612de9-7be6-4aaa-bca1-82cba14e7e72)

![placement floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/05ef5fd1-6a61-41f5-a3af-4ce81821d752)


 </details>

 <details>
 <summary> Cell design and characterization flows
 </summary>

## Cell Design Flow

Below is the representation of cell design flow

![cell design ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/481e207c-bff3-44dc-a1da-e9b060c0b096)

**Cell design flow**, also known as standard cell design flow, is the process of creating and optimizing standard cell libraries used in digital integrated circuit design. These libraries contain fundamental building blocks, such as logic gates and flip-flops, that are used to design complex digital circuits.

* **Specification and Requirements**: Begin by defining the specifications and requirements for the standard cell library. This includes factors like technology node, voltage levels, speed requirements, and power constraints.
  
* **Cell Architecture Selection**: Choose the architecture and topology for the standard cells. This involves deciding on the logical functions each cell will implement and the number of input and output pins.

* **Schematic Design**: Create schematic designs for each standard cell. This involves designing the logical function of the cell using gates and interconnections. Tools like schematic capture software are used for this step.

* **Simulation and Verification**: Simulate the designed cells to verify that they meet the specified functionality and timing requirements. This step may include functional simulation, static timing analysis (STA), and power analysis.

* **Layout Design**: Create physical layouts for the cells based on the schematic designs. This involves specifying the dimensions, placement of transistors, and routing of metal layers.

* **DRC and LVS Checks**: Perform Design Rule Check (DRC) and Layout vs. Schematic (LVS) checks to ensure that the layout adheres to the manufacturing rules and is consistent with the schematic.

* **Extraction and Characterization**: Extract parasitic components from the layout, including resistances and capacitances. These parasitics impact the timing and power characteristics of the cells. Characterize the cells by measuring their performance under various conditions, such as different input vectors and operating voltages.

* **Timing Characterisation**: Conduct detailed timing analysis to determine parameters like propagation delay, setup time, hold time, and clock-to-q delay for flip-flops

* **Library Validation**: Validate the entire standard cell library by using it in test chip or design test cases to ensure that it meets performance and functionality requirements.

Below is the flow:

![cell design 1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/58dabbee-bdc0-4259-8af8-577835d7803d)

Below shown the different functionality of different size of library that consists of gates dffs and latches.

![cell design 2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/cf41532b-32eb-4768-bee6-b865e9155546)

![cell design 3](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e750f943-c0c8-4117-bfb2-6e9ad56c68c5)

Stick diagram layout representation is show below

![stick diagram](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7d81050a-6039-4fed-bea9-1a094ac6dcf6)

## Characterisation flow

**Characterization** in VLSI refers to the process of analyzing and documenting the electrical behavior of electronic components, such as transistors, logic gates, memory cells, and standard cells, under various operating conditions. Characterization is essential for accurate circuit simulation and helps ensure that integrated circuits (ICs) meet their performance, power, and timing requirements.

Let's see below flow representation:


![ch1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e858762a-e7d7-445b-bd8f-538ab39e43d9)

![ch2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/34bb2182-24c1-40b7-b06b-faccf1959727)

![ch3](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/bef80248-0189-495b-9579-f1bbb9444096)


</details>

<details>
 <summary> General timing characterisation parameters
 </summary>
 
**Timing Characterisation**

The definations is understood by taking a circuit as a reference 

![timing charact  ckt](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b9f3b27d-3cd0-48d4-bbc5-848b18c63045)


**slew_low_rise_thr**- Its generally taken as a point in the rising wavform, the point is at rising edge generally at 20% value from the initial point.

**slew_high_rise_thr** - Its generally taken as a point in the rising wavform, the point is at rising edge generally at 20% value from the final point of the waveform, also it can also be considered as 80% from initial point of the waveform.

**slew_low_fall_thr**- Its generally taken as a point in the falling wavform, the point is at rising edge generally at 20% value from the initial point.

**slew_low_fall_thr** - Its generally taken as a point in the falling wavform, the point is at rising edge generally at 20% value from the final point of the waveform, also it can also be considered as 80% from initial point of the waveform.

![inop1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/24922247-a8b7-42c7-8f19-3315f8be5f8b)


**in_rise_thr** - It is generally taken the 50% value point in the input rise waveform. 

**in_fall_thr** - It is generally taken the 50% value point in the input fall waveform. 

**out_rise_thr** -  It is generally taken the 50% value point in the output rise waveform.

**out_fall_thr**-  It is generally taken the 50% value point in the output fall waveform.

The concept is shown in the image below


![com](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7794cd40-f580-4443-ab91-134d111c4fdf)

**Propagation delay and transition time**

**Propagation delay** is the difference out_thr and in_thr. Choosing correct out_thr and in_thr is very important for getting correct propagation delay.

![propdelay](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a1768be2-0827-4ebc-9fac-8a91ed738043)

**Transition time** is the difference between slew_high_fall_thr and slew_low_fall_thr. 

![transition time](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a030403f-1132-4700-9e13-4bb5089e703c)

 </details>

 
 # Day_3 Design library cell using Magic Layout and ngspice characterisation

 <details>
 <summary> Labs for CMOS inverter ngspice simulations
 </summary>
  
## Lab steps to gitclone vsdstdcell design

**Inverter**

**A CMOS inverter**, short for Complementary Metal-Oxide-Semiconductor inverter, is a fundamental digital electronic circuit that performs the basic logical operation of inversion. In other words, it takes an input signal and produces an output signal that is the logical complement of the input. If the input is high (logic 1), the output will be low (logic 0), and vice versa.

The input signal is applied to the gate terminals of both the NMOS and PMOS transistors. The output is taken from the connection point (the drain of NMOS and the source of PMOS) between these two transistors.

**NMOS Operation**: When the input is logic high (1), the NMOS transistor turns on because a positive voltage is applied to its gate. This establishes a low-resistance path between the output and ground, causing the output to be pulled to logic low (0).

**PMOS Operation**: Conversely, when the input is logic low (0), the PMOS transistor turns on because a low voltage is applied to its gate. This establishes a low-resistance path between the output and the power supply voltage (VDD), causing the output to be pulled to logic high (1).

Below shown the inverter diagram :

![inverter](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/fd964375-988d-4b3b-b8a6-4fa52b7e6a2e)

Nodes are shown below:

![Nodes](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/be2807d2-e912-4beb-bd29-fd137c278f97)

Here is spice deck simulation shown:

![model description](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/af257b8b-e995-45a0-8abc-e7c19515cc91)

The cir file is shown below

![cir file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b944f013-ba10-4926-9efa-1c3814d477dd)

![cmos cir](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/310fc45c-0f18-4656-9243-92eb55b050cf)

to run it open ngspice and in command give
```
source cmos.cir
```

![cmos cir](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e79c82b2-9054-41da-8314-d448fb0ddf17)


Below is the model file :

```
* SPICE 3f5 Level 8, Star-HSPICE Level 49, UTMOST Level 8

.lib cmos_models 
* DATE: Feb 23/01
* LOT: T0BM                  WAF: 07
* Temperature_parameters=Default
.MODEL nmos  NMOS (                                LEVEL   = 49
+VERSION = 3.1            TNOM    = 27             TOX     = 5.8E-9
+XJ      = 1E-7           NCH     = 2.3549E17      VTH0    = 0.3907535
+K1      = 0.4376003      K2      = 8.265151E-3    K3      = 4.214601E-3
+K3B     = -3.7220937     W0      = 2.517345E-6    NLX     = 2.310668E-7
+DVT0W   = 0              DVT1W   = 0              DVT2W   = 0
+DVT0    = 0.2411602      DVT1    = 0.3707226      DVT2    = -0.5
+U0      = 316.5922683    UA      = -9.89493E-10   UB      = 2.154013E-18
+UC      = 2.474632E-11   VSAT    = 1.254499E5     A0      = 1.2735648
+AGS     = 0.2428704      B0      = 2.579719E-8    B1      = -1E-7
+KETA    = 4.87168E-4     A1      = 0              A2      = 0.5196633
+RDSW    = 120            PRWG    = 0.5            PRWB    = -0.2
+WR      = 1              WINT    = 2.357855E-8    LINT    = 1.210018E-9
+DWG     = 2.292632E-9
+DWB     = -9.94921E-10   VOFF    = -0.1039771     NFACTOR = 1.3905578
+CIT     = 0              CDSC    = 2.4E-4         CDSCD   = 0
+CDSCB   = 0              ETA0    = 3.894977E-3    ETAB    = 7.800632E-4
+DSUB    = 0.0307944      PCLM    = 1.7312397      PDIBLC1 = 0.999135
+PDIBLC2 = 4.850036E-3    PDIBLCB = -0.0866866     DROUT   = 0.8612131
+PSCBE1  = 7.995844E10    PSCBE2  = 1.457011E-8    PVAG    = 0.0099984
+DELTA   = 0.01           RSH     = 5              MOBMOD  = 1
+PRT     = 0              UTE     = -1.5           KT1     = -0.11
+KT1L    = 0              KT2     = 0.022          UA1     = 4.31E-9
+UB1     = -7.61E-18      UC1     = -5.6E-11       AT      = 3.3E4
+WL      = 0              WLN     = 1              WW      = -1.22182E-16
+WWN     = 1.2127         WWL     = 0              LL      = 0
+LLN     = 1              LW      = 0              LWN     = 1
+LWL     = 0              CAPMOD  = 2              XPART   = 0.4
+CGDO    = 3.11E-10       CGSO    = 3.11E-10       CGBO    = 1E-12
+CJ      = 1.741905E-3    PB      = 0.9876681      MJ      = 0.4679558
+CJSW    = 3.653429E-10   PBSW    = 0.99           MJSW    = 0.2943558
+CF      = 0              PVTH0   = -0.01          PRDSW   = 0
+PK2     = 2.589681E-3    WKETA   = -1.866069E-3   LKETA   = -0.0166961      )
*
.MODEL pmos  PMOS (                                LEVEL   = 49
+VERSION = 3.1            TNOM    = 27             TOX     = 5.8E-9
+XJ      = 1E-7           NCH     = 4.1589E17      VTH0    = -0.583228
+K1      = 0.5999865      K2      = 6.150203E-3    K3      = 0
+K3B     = 3.6314079      W0      = 1E-6           NLX     = 1E-9
+DVT0W   = 0              DVT1W   = 0              DVT2W   = 0
+DVT0    = 2.8749516      DVT1    = 0.7488605      DVT2    = -0.0917408
+U0      = 136.076212     UA      = 2.023988E-9    UB      = 1E-21
+UC      = -9.26638E-11   VSAT    = 2E5            A0      = 0.951197
+AGS     = 0.20963        B0      = 1.345599E-6    B1      = 5E-6
+KETA    = 0.0114727      A1      = 3.851541E-4    A2      = 0.614676
+RDSW    = 1.496983E3     PRWG    = -0.0440632     PRWB    = -0.2945454
+WR      = 1              WINT    = 7.879211E-9    LINT    = 2.894523E-8
+DWG     = -1.112097E-8
+DWB     = 9.815716E-9    VOFF    = -0.1204623     NFACTOR = 1.2259401
+CIT     = 0              CDSC    = 2.4E-4         CDSCD   = 0
+CDSCB   = 0              ETA0    = 0.3325261      ETAB    = -0.0623452
+DSUB    = 0.9206875      PCLM    = 0.833903       PDIBLC1 = 9.948506E-4
+PDIBLC2 = 0.0191187      PDIBLCB = -1E-3          DROUT   = 0.9938581
+PSCBE1  = 2.887413E10    PSCBE2  = 8.325891E-9    PVAG    = 0.8478443
+DELTA   = 0.01           RSH     = 3.6            MOBMOD  = 1
+PRT     = 0              UTE     = -1.5           KT1     = -0.11
+KT1L    = 0              KT2     = 0.022          UA1     = 4.31E-9
+UB1     = -7.61E-18      UC1     = -5.6E-11       AT      = 3.3E4
+WL      = 0              WLN     = 1              WW      = 0
+WWN     = 1              WWL     = 0              LL      = 0
+LLN     = 1              LW      = 0              LWN     = 1
+LWL     = 0              CAPMOD  = 2              XPART   = 0.4
+CGDO    = 2.68E-10       CGSO    = 2.68E-10       CGBO    = 1E-12
+CJ      = 1.864957E-3    PB      = 0.976468       MJ      = 0.4614408
+CJSW    = 3.118281E-10   PBSW    = 0.6870843      MJSW    = 0.3021929
+CF      = 0              PVTH0   = 6.397941E-3    PRDSW   = 30.410214
+PK2     = 2.100359E-3    WKETA   = 5.428923E-3    LKETA   = -0.0111599      )
*
.endl

```
To execute it :

``run`` Then using ``setplot`` you can set the dc plot.
Also you can see by usign ``display``

Now using ``plot out vs in`` Below graph will be seen:

![plot1f](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a05a4a4c-6e8e-4e9e-868e-7118f6783e16)

Now if we increase the width of pmos which is 0.9375 below graph is seen and you can compare it with the above graph :

![plot2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/8086a75f-2594-47f6-a287-d481e44ace99)

Here is a representation illustrating the switching threshold, including the relationship and calculation between Wp/Lp and xWn/Ln.

![calculation](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7f9b0787-45cc-4e45-9edc-28918f2bff76)

Here is the updated CMOS file:

![cmos2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/4b39d6f4-5165-4a1e-96f9-46fa827b82cd)

Here is the graph of ``out vs time``

The transient Analysis graph obtained in the ngspice is shown below

![transient analysis](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/53b707e3-b39b-4dcf-a6d3-8846e070674c)

The terminologies of the transient analysis are shown below

![transient stats](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/99db6042-08a7-4d4b-9701-40048681d8b2)

Here's the graph depicting the relationship between output and time.

![in vs out](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/778eca09-2747-40b6-86e2-1c6b0f2233f9)


**Note** To calculate the difference between two points on the graph, simply drag your mouse to zoom in and then click on the graph to select the two points for comparison.

 </details>

 <details>
 <summary>Inception of CMOS fabrication Process
 </summary>

 
Here's an explanation of the 16-mask CMOS fabrication process:

* **Substrate Selection**: Selecting a substrate is a important step in semiconductor manufacturing and integrated circuit (IC) fabrication. The substrate is the foundational material upon which the entire IC will be built. Typically, silicon (Si) is the most commonly used substrate material for most modern ICs due to its favorable properties, but other materials like gallium arsenide (GaAs) or silicon carbide (SiC) are also used in specific applications.

* **Creating active region for transistors**: Creating active regions for transistors involves isolating specific areas on a silicon substrate where transistors will be located. This isolation is achieved by depositing layers of silicon dioxide (SiO2) and silicon nitride (Si3N4) on the substrate. Then, using photolithography and etching techniques, patterns are defined on the silicon nitride layer. These patterns determine where the active regions for transistors will be. The remaining SiO2 and exposed silicon regions become the isolated pockets where transistor components will be fabricated. This isolation is crucial to prevent unwanted electrical interactions between transistors and ensure their proper functioning.

* **N-well and P-well formation**: The formation of N-well and P-well regions in CMOS technology involves ion implantation using specific dopants. Boron is utilized for P-well formation, while Phosphorus is employed for N-well creation. These dopants are implanted into the silicon substrate to define the N-well and P-well regions, which are essential components for building complementary NMOS and PMOS transistors, respectively.

* **Creation of the gate terminal**: The gate terminals for NMOS (N-channel Metal-Oxide-Semiconductor) and PMOS (P-channel Metal-Oxide-Semiconductor) transistors are created through photolithography techniques. In this process, precise patterns are defined on the semiconductor substrate using masks and light exposure. These patterns correspond to the gate electrodes of the transistors, and they play a fundamental role in controlling the transistor's conductivity and operation. By carefully implementing photolithography, the gate terminals for both NMOS and PMOS transistors are formed with high precision, enabling the subsequent steps in transistor fabrication.

* **Formation of LDD (lightly doped drain)**: In the LDD process, additional ion implantation steps are introduced after the formation of the main source and drain regions of the transistor. The key idea is to create lightly doped regions adjacent to the main source and drain regions. These lightly doped regions serve as a buffer between the channel and the heavily doped source and drain regions. The purpose of the LDD regions is to reduce the strength of the electric field near the drain, particularly in the region where the channel meets the drain. This helps to prevent the acceleration of electrons to high energies, which can lead to the hot electron effect. The hot electron effect can cause damage to the gate oxide and result in long-term reliability issues for the transistor.

* **Formation of Source & Drain**: The formation of the source and drain regions in a semiconductor device is a critical step in the fabrication process. To ensure proper performance and avoid issues like channeling during ion implantation, several techniques are employed, including the use of a screen oxide layer, arsenic implantation, and annealing.
   * **Screen Oxide**: Before performing the source and drain ion implantation, a thin layer of screen oxide is deposited or grown on the semiconductor wafer's surface. The screen oxide serves as a protective layer during the implantation process. It helps to disperse and slow down the implanted ions, reducing the likelihood of channeling.
 
   * **Arsenic Implantation**: Arsenic (As) ions are implanted into the regions of the silicon substrate where the source and drain are to be formed. Arsenic is a common dopant used for N-type (electron-conducting) regions in CMOS technology. The implantation process introduces a controlled amount of arsenic atoms into the silicon lattice, creating N-type doping in the source and drain regions.
 
   * **Annealing**: After the arsenic implantation, the wafer is subjected to an annealing process. Annealing involves heating the wafer to high temperatures for a specified duration. During annealing, the implanted arsenic ions are activated, and any damage to the silicon crystal lattice caused by the implantation process is repaired. Annealing helps to ensure that the source and drain regions have the desired electrical properties.

* **Formation of Local Interconnect**: Local interconnect formation is a important step in semiconductor device fabrication, enabling the creation of electrical connections between different components on a chip.
  
   * **Screen Oxide Removal (HF Etching)**: After various processing steps, including source and drain formation, a screen oxide layer is typically deposited or grown on the semiconductor wafer's surface. This screen oxide layer serves as a protective barrier during ion implantation. However, it needs to be removed to allow for the formation of local interconnects.
     
   * **HF Etching**: Hydrofluoric acid (HF) is commonly used to selectively etch away the screen oxide. HF is highly effective at removing silicon dioxide (SiO2) while leaving other materials like silicon (Si) and metal layers unaffected
 
   * **Deposition of Ti (Titanium)**: Once the screen oxide is removed, the next step involves depositing a layer of titanium (Ti) onto the wafer's surface. Titanium is chosen for its excellent adhesion properties and low electrical resistance.
 
   * **Chip Protection**: This top SiN layer acts as a passivation layer, shielding the underlying components from external influences. It also helps prevent contamination and ensures the long-term reliability of the integrated circuit.
 
Final Representation is shown below

![fabrication](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/2fe79a8e-8560-408f-9eba-e2da7131f424)


 First, clone the required mag files and spicemodels of inverter,pmos and nmos sky130. The command to clone files from github link is:

```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
```
once I run this command, it will create ``vsdstdcelldesign folder`` in openlane directory.

For layout we run magic command

``magic -T sky130A.tech sky130_inv.mag &``

![gitclone and command](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ea098dd4-c06f-4cdd-865f-dc4fb42fb837)


Ampersand at the end makes the next prompt line free, otherwise magic keeps the prompt line busy. Once we run the magic command we get the layout of the inverter in the magic window

![Magic vsdvsd](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/bce8a323-7970-4c2b-af9c-51586c9f9914)

 

**Lab introduction to sky130 basic layers layout and LEF using inverter**

To select the area we need to press S, and type what in the command window which inturns gives the details about the selected area.

![knowing the element in the floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/705b633d-6b09-43c0-8bee-e95905f6a9fc)

![knowelement ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/62e7b87a-e76a-4dda-a472-97747af2387b)

![knowing the element in the floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/cc7e826b-4f5e-4d4b-8313-079c69286bd1)

**Steps to create standard cell layout and extract spice netlist**

Following commands were used in the magic command window to generate the spice file.

```
extract all

ext2spice cthresh 0 rthresh 0

ex2spice
```
The above commands will generate a ``.spice file`` in the directory.

![steps to generate the spice extract file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b4a48bf6-5963-4619-b375-682751d41417)


 </details>

 <details>
 <summary> SKY130 Tech File Labs
 </summary>

**Lab steps to create final SPICE deck using sky130tech**

In this we edit the ``.spice`` file making the connection as required in the circuit. The file is customised in accordance to the model file available in the sky130PDK. 

Screenshot of the model file available in the SKY130PDK

![model file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5b3983d5-e0c5-476e-9b5d-e43484443b4b)

The edited ``.spice`` file is shown below

![gedit edited file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/936a58e3-d03f-4eb9-84c8-dbec9895cac7)

The ngspice transient results obtained are as follows

![ngspice results](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/33f44a50-bac3-47b8-9721-8317a9087e85)

**Lab steps to characterise inverter using sky130 model files**

After this we obtained the output waveform of the circuit, following commands were used 

```
plot y vs time a
```
![output wave form](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/907c5fd0-7a49-4e24-acbd-ece4160b379e)

To zoom in the waveform select the area and select the point in the zoom portion of the graph to obatin the coordiantes of the point.

![zoomed ngspice](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/c869067d-ebe3-4610-8448-ce394a1ad1af)

**Lab introduction to sky130 pdk's and steps to download labs**

Here using the following commands I downloaded the folder having sample layouts
```
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

tar xfz drc_tests.tgz

cd drc_tests

ls -al

```
Following files were obtained 

![command and file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/aa6395ec-edfc-4d6d-a545-cd57dc32a66c)

To open the magic window following command was used

```
magic -d XR
```
![magic invoke](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7bd166c3-e611-4a1d-ad64-584210881101)

**Lab introduction to Magic and steps to load sky130tech-rules**

The commands for DRC rule check can be refered to the following page

```
https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html#m3

```

![periphery rules](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/90ae8387-9f41-4db3-91f3-eb60c707fefb)

Following commands are used 

![DRC command window](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/79c129f0-3c20-4d41-b648-a6e1b473438c)

**Right click** - Outside the box to increase the box area in the magic layout, inside the box to decrease the area of the box.

**Left click** - Used to move the box from once place to other.

To get the metal connections following steps needed to be followed

* First select the area under which the metal connection needed to be established, using the right and left click.
* Now paint the area using any metal colour from the window, here we used m3 i.e. metal 3.
* Now press P this will generate the metal connections in the box created.
* A sample of the above process is shown in the below process

  ![metal details](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/4c1a94eb-8137-41cf-9433-fc76e1b1625f)

**Lab excercise to fix poly.9 error in Sky130 tech-file**

To load the poly.mag :

``load poly.mag``

It will open layout of the file in magic:

![error poly9 layout](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/3934f5d9-af9a-4a60-8077-522d62fcd38e)

To know more about the poly.9 error refer the website, a snapshot of which is shown below

![poly9werr](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/bf75fc2b-3075-4b1d-a8d4-60585f576781)

To overcome this error open the file ``sky130A.tech``

These changes are needed to be made 

Change the following

```
spacing npres *nsd 480 touching_illegal \
	"poly.resistor spacing to N-tap < %d (poly.9)"
```
to

```
spacing npres allpolynonres 480 touching_illegal \
	"poly.resistor spacing to N-tap < %d (poly.9)"
```

![poly1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/cc7f754b-af75-4c6e-a33f-bbf80d486bc7)

Now change 

```
spacing xhrpoly,uhrpoly,xpc alldiff 480 touching_illegal \

	"xhrpoly/uhrpoly resistor spacing to diffusion < %d (poly.9)"

```

To this

```
spacing xhrpoly,uhrpoly,xpc allpolynonres 480 touching_illegal \

	"xhrpoly/uhrpoly resistor spacing to diffusion < %d (poly.9)"
```

![poly2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/06c8ef70-07d6-4da3-a85e-de51ef8a3aef)

Now save it. You dont have to close the magic after the modifying the sky.tech file. Type the below command in magic's terminal:

``tech load sky130A.tech``
In the warning click on yes.
Then type below command:
``drc check``

### NOTE- Since the tech file got loaded behind the curtains, DRC engine needs to be told that check everthing again.

Following layout will be obtained after making the changes
 
![drc check skytech130A](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/15addf98-8044-4328-afb2-09efd1b7f5a0)

**Lab excercise to implement poly resistor spacing to diff & tap**

Copy the three resistors by selecting (Edit > select area) and then press 'c' on keyboard.
You can move the copied resistors by pressing 'm' key and arrow key.

Now create n diffusion and p diffusion by creating box and selecting the ndiff and pdiff from the sidebar(by clicking the middle button of the mouse).

Then modify the sky130A.tech file by just modifying the *nsd to alldiff.
Now type below command in magic's terminal and all the rules will correctly identify 

``drc check``

Below image shows the changes appeared on the layout

![implement poly resistor](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ef38ac99-9a95-49f4-ac8c-1976bddf50d8)


**Lab Challenge excercise to describe DRC error as geometrical construct**

Open sky130A.tech file and search cifmaxwidth below is the representation:

![cifwidth](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/e9828f79-8ee0-41f7-b888-bd0e9f1a3857)

Below is the rule shown for nwell (which can be access by skywater sky130 pdk website) :

![pp rules1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/48240a45-9643-4d1f-8fe9-47761ffce865)

Also refer this dnwell rules:

![pp rules2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/3b86d0c1-b3b8-4c83-95ca-c8dc95c683f8)

Refer this style drc in sky130A.tech file :

![gedit lab challenge](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/871a780f-3dcb-4a83-beb3-168ee125317e)

First create a box around cell nwell6 , Now in tkcon terminal type below commands:

![mag 6](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7de5b2f5-1115-426b-9e04-395ce160d7dc)

```
cif ostyle drc
cif see dnwell_shrink
feed clear
cif see nwell_missing
feed clear
```

![mag 6 2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/2fa7281c-1a8e-4545-b732-d6b3c65976d9)
![mag 6 3](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/76bfb69d-d26a-43c6-8627-2cd41284bd3d)



**Lab challenge to find missing or incorrect rules & fix them**

Modify the sky130A.tech file according to below:

change the cifmaxwidth code to this :

```
cifmaxwidth nwell_untapped 0 bend_illegal \

	"Nwell missing tap (nwell.4)"
```
Following changes are made in the sky130A.tech 

![gedit 2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/733405ab-88d2-4083-972b-22932984fe3e)

![gedit3](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/f3b3703f-790e-45bb-900d-22bbfea1bfbb)

After modification give commands 
```
tech load sky130A.tech
drc check
drc style
drc(full)
drc check
```

Below is the result for modified code and corresponding change in the layout

![Modified nwell 6](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/251730da-b71a-4e9f-9335-9513b4459f32)

Now tapp using nsubstratencontact shown below it will change DRC:

![final image day3](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/f34e6b13-2b53-44a9-b7a8-162758aae0f4)

  
 </details>

 
 # Day_4 Pre Layout timing analysis and importance of good clock tree

 <details>
 <summary> Timing modelling using delay tables
 </summary>

**Lab steps to convert grid info to track info**

Since ``.mag`` file consists each and every details of the layout i.e power & gnd info., port info, logic part. But for placement and route part all we need is input-output info and power & gnd info. Hence we would be using ``.lef`` file 

From PNR point of view we need to follow few guidelines given below

* I/O port should lie at the intersection of vertical and horizontal tracks
* The width of the std cell should be in odd multiple of the track pitch & height should be odd multiple of the vertical pitch

To get the track info use the following command in the directory 

```
less tracks.info
```
output of which is shown below

![track info](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/1c6a4186-a613-405f-9a02-962fdea96dd5)

Here we are eventually converting grid defination to track defination

The command used in the layout window is given below

```
grid 0.46um 0.34um 0.23um 0.17um
```

Before conversion

![after grid command](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b6ecccfe-6031-451c-a14a-2144ca3bd6db)

After conversion

![io intersection](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/0c2794f2-1d4e-494a-ade5-edbf54899dbb)

I/O port that lies at the intersection of vertical and horizontal tracks

![before grid command](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/980f0391-4a9c-450a-a3b2-6fe39d6a9277)


**Lab steps to convert magic layout to std cell LEF**

Port defining in the magic, below image shows the steps involved in defining the port 

![port defining A](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/bf0874fe-c853-438e-b9ae-02af19967bab)

Steps for generating the ``lef`` file following command is used

![lef file command](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/3b9c8b39-5297-4c02-b0fa-c2ea3a21bc3a)

Below is generated lef file in the directory

![lef file ss](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/0b01ab5e-b57e-4e3b-94b4-61d0c579c704)

**Introduction to timing libs and steps to include new cell in synthesis**

Here we want to generate the custom cell of the ``.lef`` file generated for which we need libraries here we have three diff types of library i.e typical, fast, slow. 

![lib types](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/897ff1cb-4564-4faf-bae6-24046a1c5f2d)

![library](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/06001528-5b5c-4ceb-bddd-a031cff53bfe)

Now we will make the following changes in the config. json file 

```

{
    "DESIGN_NAME": "picorv32",
    "VERILOG_FILES": "dir::src/picorv32a.v",
    "CLOCK_PORT": "clk",
    "CLOCK_NET": "clk",
    "GLB_RESIZER_TIMING_OPTIMIZATIONS": true,
    "RUN_HEURISTIC_DIODE_INSERTION": true,
    "DIODE_ON_PORTS": "in",
    "GPL_CELL_PADDING": 2,
    "DPL_CELL_PADDING": 2,
    "CLOCK_PERIOD": 24,
    "FP_CORE_UTIL": 35,
    "PL_RANDOM_GLB_PLACEMENT": 1,
    "PL_TARGET_DENSITY": 0.5,
    "FP_SIZING": "relative",
    "LIB_SYNTH":"dir::src/sky130_fd_sc_hd__typical.lib",
    "LIB_FASTEST":"dir::src/sky130_fd_sc_hd__fast.lib",
    "LIB_SLOWEST":"dir::src/sky130_fd_sc_hd__slow.lib",
    "LIB_TYPICAL":"dir::src/sky130_fd_sc_hd__typical.lib",
    "TEST_EXTERNAL_GLOB":"dir::/src/*",
    "SYNTH_DRIVING_CELL":"sky130_vsdinv",
    "MAX_FANOUT_CONSTRAINT": 4,
    "pdk::sky130*": {
        "MAX_FANOUT_CONSTRAINT": 6,
        "scl::sky130_fd_sc_ms": {
            "FP_CORE_UTIL": 30
        }
    }
}


```
![config](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/97cd3cbb-29ee-4731-a040-f06eb89d91a9)

To incorporate the standard cell into the OpenLANE workflow, follow these steps after launching OpenLANE as you normally would:

* Initialize OpenLANE as usual.
* Proceed with the following actions:
  * Reconfigure the standard cell integration within OpenLANE.
  * Execute the necessary tasks to seamlessly include the standard cell in the workflow.

```
prep -design picorv32a -tag RUN_2022.08.17_16.22.21 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
Below is the obtained floorplan and sythesis report of the custom made cell

![new floorplan](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7f496385-a032-4ff0-a488-fb288e626690)

![log file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7c0d97d8-90d6-4d82-a569-df8452fd39c9)

**Introduction to delay tables**

# Delay tables

We observe that the buffer we insert to maintain signal integrity has some constraints. We observe that size of buffer in every level should have same size and have different delays depending on load driven by them. So VLSI engineers came up with concept of delay tables which consists of 2D array of values input slew & load capacitance defined for cell for different sizes. These delay tables became timing models. The algorithm takes these values and computes delay values. If delay is not available directly, it takes nearest data and determines through extrapolation.

![Delay table](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/f02f5764-e917-44bf-bc25-476116b1e434)

</details>

<details>
 <summary>Timing Analysis with ideal clocks using openSTA
 </summary>


# Setup & hold time concepts

It is here that we introduce SETUP and HOLD time. Setup time is defined as the minimum amount of time before the clock’s active edge that the data must be stable for it to be latched correctly. Any violation may cause incorrect data to be captured, which is known as setup violation.

![S HT1](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/2df7daed-20a6-4329-b377-ea3af416ff81)

Hold time is defined as the minimum amount of time after the clock’s active edge during which data must be stable. Violation in this case may cause incorrect data to be latched, which is known as a hold violation. Note that setup and hold time is measured with respect to the active clock edge only.

![S HT2](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/53d2547a-206b-4228-b215-0c3b6aeea644)

# Clock jitter concept

Circuitry in the clock generator, noise, changes in the power supply, interference from surrounding circuitry, etc. are the usual causes of clock jitter. The design margin called for in the timing closure specification includes jitter as a factor.

Period jitter is the difference between a clock signal's cycle time and the ideal period over a large number of randomly chosen cycles, such as 10K cycles. The clock period deviation can be supplied as either an average value across the chosen cycles (RMS value) or as the difference between the chosen group's highest and minimum deviations (peak-to-peak period jitter).

The difference between two consecutive clock cycles across a random number of clock cycles is known as cycle to cycle jitter, or C2C. (say 10K). Typically, this is described as the peak value for the random group.By doing so, the high frequency jitter can be calculated.

The effect being measured in the frequency domain is phase noise. In the frequency domain, phase noise is the representation of fast, short-lived, random variations in the phase of the waveform. These fluctuations can be converted into jitter values for digital design.

![clock jitter](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/65b0b057-5260-454b-805b-4da1e332be88)

After putting command

```
set ::env(SYNTH_MAX_FANOUT) 4
```
we got positive slack in sta analysis.


**Lab Steps to configure post synthesis analysis**

Before synthesis we had file name sta.config which gives info about synthesis & my_base.sdc file

![my_base sdc](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/71e4dd36-5df7-4600-b953-51aac4641cdc)


![presta](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/05de3a35-f2b6-4d98-ab0b-5dc1928ef588)


 </details>

 <details>
 <summary> Clock tree synthesis TritonCTS and signal integrity 
 </summary>



# Clock tree synthesis

The goal of constructing a clock tree is to make sure that the clock input reaches all the elements and that there is no clock skew. The H-tree is one of the most used methods in CTS. If you have ever tried to reduce slack in a previous run, you may have noticed that the netlist has been changed by cell replacement techniques. Before trying to run a CTS in tritoncts tool.

The goal of the Clock Tree Synthesis is to reduce the routing resources of the clock signal, reduce the area of the clock repeaters, while maintaining a reasonable clock skew, reasonable clock latency, reasonable clock transition time, minimum Pulse Width, and duty cycle requirements for all the sequence elements in the design, and reasonable clock power within the spec. Clock Skew refers to the difference in the clock arrival time between two registers

Below is an example of bad tree

![clock tree](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/ec506293-59a4-4a69-a7e9-8876d0cf79d1)


# Cross talk & cross net shielding

Crosstalk noise is noise generated on the clock network by aggressor nets surrounding the clock signal. This noise can delay or make the clock signal faster or even cause spurious transitions known as glitches. To maintain the signal integrity of the clock signal, physical designers protect the clock wires using a power net. They may also use NDR rules that route the clock signal by leaving one empty track next to the clock route. This helps to reduce the impact of noise on the clock network. The function of the clock signal is to control and synchronize trigger events within a synchronous design. Therefore, maintaining the signal integrity is essential to meet your design functional specification.

![cross talk](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/bdc9c311-15e5-4d70-99b4-c2cf1dd1adbd)

 **Clock tree Synthsis lab**

 We use the following command to execute CTS within OpenLane:

 ```
run_cts
write_verilog ./designs/picorv32a/picorv32a_cts.v

```

Since clock buffers are added during the CTS run, buffer delays are now a factor, and real clocks will be used for the remainder of our research. Now, setup and hold time slacks may be examined in OpenROAD's post-CTS STA analysis for the openLANE flow:

open openroad tool using following in openlane command prompt.

```
openroad
```
```
read_lef ./designs/picorv32a/runs/RUN_2023.09.15_09.02.59/tmp/merged.nom.lef 
read_def ./designs/picorv32a/runs/RUN_2023.09.15_09.02.59/results/cts/picorv32a.def
write_db ./designs/picorv32a/picorv32a.db
read_verilog ./designs/picorv32a/picorv32a_cts.v
read_liberty $::env(LIB_SYNTH_COMPLETE)
read_sdc ./designs/picorv32a/runs/RUN_2023.09.15_09.02.59/results/cts/picorv32a.sdc
report_checks -path_delay min_max -format full_clock_expanded -digits 4
```
It's evident that the slack constraints have been satisfied.

![slackmeeting](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/f3ad4837-c02f-40b4-9d88-f9b2d1846cb2)

 </details>

 
 # Day_5 Final steps for RTL2GDS using tritonRoute and openSTA

<details>
 <summary> Routing and Design Rule Check(DRC)
 </summary>


**Routing**- Routing is the process of connecting two elements in the circuit. The software here decides the best possible path to connect the two elements.

**Maze Routing**- The **Lee algorithm** is one possible solution for maze routing problems. It always gives an optimal solution, if one exists, but is slow and requires large memory for dense layout.

The algorithm is a breadth-first based algorithm that uses queues to store the steps. It usually uses the following steps:

* Choose a starting point and add it to the queue.
* Add the valid neighboring cells to the queue.
* Remove the position you are on from the queue and continue to the next element.
* Repeat steps 2 and 3 until the queue is empty.
  
  One key concept to understand is that breadth-first searches go wide, while depth-first searches go deep.

  The following image show the two different ways to connect the element in the core using the Lee's algorithm.

  ![Lee algorithm](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/d8fa3d7b-2612-43f6-a5bc-f399a1781b3f)

  **Design Rule Check(DRC)**

  Few of the DRC are listed below

  1. Via Width- The via width refers to the width of this vertical interconnection structure. It is defined as the minimum allowable width for a via, which ensures that the via can be properly manufactured and that it meets the required electrical and thermal specifications.
  
  2. Via Spacing -The via spacing rule is defined to guarantee that there is enough separation between vias to avoid issues such as shorts or unintended connections during the manufacturing process. Violating via spacing rules can lead to manufacturing problems and potential electrical performance issues in the final chip.
  
  3. Wire Pitch- Wire pitch" refers to the minimum allowable distance between two adjacent metal wires or conductive traces on a semiconductor layout.
     
  4. Wire width- Wire width" refers to the minimum allowable width of metal wires or conductive traces on a semiconductor layout.
     
  5. Wire Spacing- Wire spacing refers to the minimum allowable distance between two adjacent metal wires or conductive traces on a semiconductor layout.
 
     ![drc](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/2b1d7999-3ee4-428c-85b7-89fbeda02a56)


 </details>

 <details>
 <summary> Power distribution Network and routing 
 </summary>

In contrast to the standard ASIC flow, the generation of the Power Distribution Network (PDN) is not included as a step in the floorplan process within OpenLANE. PDN generation must take place after the Clock Tree Synthesis (CTS) and subsequent post-CTS Static Timing Analysis (STA) assessments.

You can verify whether the Power Distribution Network (PDN) has been created or not by checking the current "def" environment variable:
 ``echo`` ``$::env(CURRENT_DEF)``

 prep -design picorv32a -tag Run 2023.09.16.
```
gen_pdn
```

![commands](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b145936c-97c0-49d0-b407-282c6bc08072)

![log file](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/56a0fd22-df1f-469d-8ff8-b086ed6803af)


 

 </details>

<details>
 <summary> TritonRoute Features
 </summary>

TritonRoute - TritonRoute is an open-source, fully-automated, and hierarchical detailed router used in electronic design automation (EDA) for integrated circuit (IC) physical design.

**TritonRoute feature 1 -Honours pre-processed route guides**

* Performs initial details route
* Honours the preprocessed route guides(obtained after fast route) i.e. attempts as much as possible to route within route guides.
* Assumes route guides for each net satisfy inter-guide connectivity.
* Works on proposed MILP based panel routing scheme with intra-layer parallel and inter-layer sequential routing framework.

![preprocessed routing guides](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5a5574f0-cb5d-47ec-9a51-b5434437b132)

**Interguide Connectivity**
* Two guides are connected if
   * They are on same metal layer with touching edges, or
   * They are neighboring metal layers with a non zero vertically overlapped area.
* Each unconnected terminal(i.e pin of standarad cell instance should have its pin shaeped overlapped by a route guide)
  
**TritonRoute Feature 2&3 -Inter-guide connectivity and intra & inter-layer routing**

Problem Statement
**Input**- LEF,DEF, Preprocessed route guides 

**Output** - Detailed routing solution with optimised wire length and via count

**Constraints** - Route guide honoring, connectivity constraints and design rules.

![inter   Intra layer](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/a4a1ac53-9e1f-465c-a48b-1e6056da4cfb)


**TritonRoute method to handle connectivity**

![handling connectivity ](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/d9dceea7-e123-442d-bcf5-2f4fa6fa6a08)


**Routing topology algorithm and final files list post-route**

![routing algo](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/5725cac3-93d5-42cd-92ad-776b0ae2a0c4)

</details>

# References

<details>
 <summary> References
 </summary>
	
I sincerely thank Mr. Kunal Gosh, the Founder of VSD, for his invaluable assistance in guiding me through the completion of this workflow with seamless ease.

I would also like to express my gratitude to Pruthvi Bhai Parate & Bhargav D.V. for there outstanding technical expertise, which was instrumental in helping me identify and resolve errors.

</details>



 
 















