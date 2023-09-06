# Advanced-Physical-Design-Using-OpenLANE-Sky130

Day-1

</details>

How to Talk to Computers

Inception of open-source EDA, OpenLANE and SKY130PDK

Basic terminologoies

1. PADS-

2. Foundary IP's-

3. Core-

4. Macros-

5. PDK-

The layout of RISCV processor is shown below.

![Screenshot (84)](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/7fc8f83d-d54d-4eba-ac3a-e3f3284808f4)

A generic view of IC is shown below

![Screenshot (85)](https://github.com/DSatle/Advanced-Physical-Design-Using-OpenLANE-Sky130/assets/140998466/b9557c3c-a619-4921-a992-8f7bf8547af7)

</details>

SoC Design & OpenLANE

The following are the the three important parameters needed to design a ASIC chip.

1. RTL IP's-

2. EDA Tools-

3. PDK Data-

Simplified RTL to GDSII flow.

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






 
  
















