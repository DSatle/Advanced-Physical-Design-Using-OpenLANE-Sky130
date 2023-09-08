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
  
















