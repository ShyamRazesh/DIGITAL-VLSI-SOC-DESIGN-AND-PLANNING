# DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING

Author: Srinivasa Yashwanth

Acknowledgements: SoC design Program by [Mr. Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836) , [VLSI System Design](https://www.vlsisystemdesign.com)

## OpenSource Physical Design
This repository contains all the information studied and created during the [Advanced Physical Design Using OpenLANE / SKY130](https://www.vlsisystemdesign.com/advanced-physical-design-using-openlane-sky130/) workshop. It is primarily foucused on a complete RTL2GDS flow using the open-soucre flow named OpenLANE. [PICORV32A](https://github.com/YosysHQ/picorv32) RISC-V core design is used for the purpose.

## Introduction To RTL to GDSII Flow
RTL to GDSII Flow refers to the all the steps involved in converting a logical Register Transfer Level(RTL) Design to a fabrication ready GDSII format. GDSII is a database file format which is an industry standard for data exchange of IC layout artwork. The RTL to GSDII flow consists of following steps:

- RTL Synthesis 
- Static Timing Analysis(STA)
- Design for Testability(DFT)
- Floorplanning
- Placement
- Clock Tree Synthesis(CTS)
- Routing
- GDSII Streaming

All the steps are further discussed in details in the repository.

## About Google SkyWater PDK
Google and SkyWater Technology Foundry in collaboration have released a completely open-source Process Design Kit(PDK) in May, 2020. The current release target to a SKY130 (i.e. 130 nm) process node is available as [SkyWater Open Source PDK](https://github.com/google/skywater-pdk). The PDK provides Physical VLSI Designer with a wide range of flexibility in design choices. All the designs and simulations listed in this repository are carried out using the same SkyWater Open Source PDK.
## List of All Open-Source Tools Used

| Name of Tool | Application / Usage       |
| :--------  | :-------------------------------- |
| [Yosys](https://github.com/YosysHQ/yosys)	       |Synthesis of RTL Design |
| ABC	          |Mapping of Netlist |
| [OpenSTA](https://github.com/The-OpenROAD-Project/OpenSTA)	       |Static Timing Analysis |
| [OpenROAD](https://github.com/The-OpenROAD-Project/OpenROAD)	    | Floorplanning, Placement, CTS, Optimization, Routing |
| [TritonRoute](https://github.com/The-OpenROAD-Project/TritonRoute)    |	Detailed Routing |
| [Magic VLSI](http://opencircuitdesign.com/magic/)     |	Layout Tool |
| [NGSPICE](https://github.com/imr/ngspice)	     | SPICE Extraction and Simulation |
|SPEF_EXTRACTOR  |  Generation of SPEF file from DEF file  |

## Setting Up Environment
The above list of tools shows that, many different tools are required for various tasks in Physical VLSI Design. Each tool in itself have number of system requirements and require various supporting tools to be installed. Installing each tool one-by-one seems in-efficient. This is made easy by some custom scripts that setup the required tools and environment for them in just a few easy steps. To install all the required tools, one can refer to the below mentioned repositories:

- [VSDFlow](https://github.com/kunalg123/vsdflow) - Installs Yosys, Magic, OpenTimer, OpenSTA and some other supporting tools
- [OpenLANE Build Scripts](https://github.com/nickson-jose/openlane_build_script) - Install all required OpenROAD and some supporting tools

## Day-1 Inception of open-source EDA, OpenLANE and Sky130 PDK

## Digital ASIC Design

It is the process of designing an ASIC chip that uses digital logic components, as opposed to analog.

![digital asic design jpeg](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/378454d8-ab00-4e81-9f67-cbfae6892e88)


## Open Source Digital ASIC Design

![open source asic digital design](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b0c58076-7eae-476e-90a8-b0fed72cbe38)


RTL2GDS Flow
--------

![Screenshot 2024-03-31 110337](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/497c6756-2812-45e1-917c-920b445359ec)


1. **Synthesis**:
   - **RTL Analysis**: Conduct RTL analysis to ensure the correctness and completeness of the RTL design. Identify and address any issues related to combinational loops, clock domain crossings (CDC), and other potential synthesis issues.
   - **Logic Synthesis**: Translate the RTL design into a gate-level netlist using logic synthesis tools. Optimize the netlist for area, power, and timing based on specified constraints.
   - **Technology Mapping**: Map the synthesized logic gates to cells from the target technology library. This step involves selecting the appropriate cells and optimizing the mapping for timing and area.

2. **Floor Planning with Power Planning**:
   - **Floor Planning**: Define the physical layout of the chip by allocating space for different functional blocks, such as logic cores, memory blocks, I/O pads, and power grid structures. Consider factors such as chip size, aspect ratio, and placement of critical components.
   - **Macro floor planning**: This includes defining of the dimensions, pin locations, row etc.
   - **Power Planning**: Design the power distribution network (PDN) to ensure stable and reliable power delivery to all parts of the chip. Place power pads and create power rails, power straps, and decoupling capacitors to minimize voltage drop and noise.

3. **Placement**:Using a post-synthesis netlist and floor-planning/physical design limitations, arranging the standard cells on the chip to create a physical layout.
   - **Global Placement**: Perform global placement to assign initial positions to cells on the chip while considering factors such as timing, congestion, and wirelength.
   - **Detailed Placement**: Refine the placement by optimizing cell positions to minimize wirelength, reduce congestion, and meet timing constraints. Ensure proper placement of critical paths and avoid hotspots.

4. **Clock Tree Synthesis (CTS)**:
   - **Clock Tree Synthesis**: Design and optimize the clock distribution network to ensure consistent and reliable clock signals across the chip. Generate a balanced clock tree that minimizes clock skew and meets timing requirements for all clock domains.Involves providing clock signals to all the sequential elements in the design to obtain minimum skew usually in the form of a tree(H, X, pi tree, Fish Bone).

5. **Routing**:
   - **Global Routing**: Create the initial routing topology by determining the paths for signal wires, clock lines, and power/ground connections. Resolve conflicts and congestion to achieve a feasible routing solution.
   - **Detailed Routing**: Perform detailed routing to physically implement the routing paths generated during global routing. Optimize wire lengths, minimize parasitic effects, and ensure signal integrity. Use techniques such as via insertion, wire spreading, and metal layer assignment. Includes making wires to connect the various cells to create a physical layout.

6. **Signoff**:
   - **Design Rule Checking (DRC)**: Run design rule checks to verify that the layout adheres to the manufacturing rules and constraints specified by the foundry.
   - **Layout vs. Schematic (LVS) Verification**: Perform layout vs. schematic checks to ensure the layout matches the intended circuit functionality.
   - **Timing Analysis**: Conduct static timing analysis (STA) to verify timing constraints, including setup time, hold time, and clock skew, and ensure that timing requirements are met across the chip.
   - **Power Analysis**: Analyze power consumption and distribution to ensure that power constraints are satisfied and that the PDN is robust.
   - **Physical Verification**: Perform full-chip physical verification to ensure the layout is free from manufacturing defects and meets reliability criteria.

     OpenLANE and strive chipset
     -----
      ![Screenshot 2024-03-31 111302](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/180a7cfc-4550-420a-8d90-9e2d7f922dd3)
      ![Screenshot 2024-03-31 111426](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2e50b2b9-130b-4a83-8776-d2cff1271b4f)


     ## OpenLANE ASIC Flow
     
       ![Screenshot 2024-03-31 111559](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/77abde6f-334f-4823-835a-0954dd5afb71)

     OpenLANE Directory structure
     ----------
     
     Basic Linux Commands cd: opens the particular folder ls: lists the content of the folder pwd: shows the present working directory mkdir: to make a new directory command --help: shows the complete use 
     of that command clear: clears the terminal screen
  
      Exploring OpenLANE Directory
     ----
     
     Working on sky130A(pdk) which contains libs.tech which has respective files on tools such as magic, netgen etc., and libs.ref which has files related to the specific technology.
  
     # Open the working Directory
     
     ![Screenshot 2024-03-31 200154](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f5df534b-d7d7-4157-9934-7c3f03060d32)

     ```bash
        cd Desktop
        cd work/tools
        cd openlane_working_dir
        cd openlane
     ```
   
     ## To open the Openlane
   
     After getting into the directory, enter the commands
   
    ![Screenshot 2024-03-31 200453](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/56fb6185-cccd-4e55-9842-dc2611691f3e)

    ```bash
       docker
       pwd
       ls -ltr
    ```
   
   ## Interactive Mode
   
       To open the openlane in interactive mode,
   
    ![Screenshot 2024-03-31 201104](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ef2765ef-0632-4b26-87df-4f5981438323)
   
   You may run the interactively by using the  `-interactive`  option:
   
      ```bash
        ./flow.tcl -interactive
      ```
            
     To prepare the openlane,
      
    ![Screenshot 2024-03-31 215317](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7b5327ac-3f75-400e-ad07-423f20fb66f8)

     ```bash
        package require openlane 0.9
        prep - design picorv32a
     ```
   ![Screenshot 2024-04-02 215510](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/42b6eb6a-cff5-4f1a-b4d3-ae21f76fead8)
     
   ![Screenshot 2024-04-02 220124](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/231000b3-00fc-4802-baca-fabc02f89698)

 ### Synthesis
   
 To run the Synthesis
   
    ```bash
       run_synthesis
    ```
   
   ![Screenshot 2024-03-31 220804](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e9199ee6-71ee-46e0-829a-e0b36a9e4dbe)
         
 ## Report generated after synthesis
   
   Before running, we saw that the result folder was empty. But now, after running the synthesis, we can see that all the mapping has been done by ABC.
   And in the report, we can see when the actual synthesis has been done. and the actual statistics synthesis report is shown below, which is the same as what we have seen before.
   
 ![Screenshot 2024-03-31 223408](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/4ee153b4-d2b7-4001-bfa5-82ac17cbba3f)
 
   Particularly we are interested in finding the Flop ratio. This can be calculated by using the formula:
   
       Flop Ratio = No. of D FlipfLops/Total No. of cells
      
                   =1613/14876
      
                   =0.10842
      
        Percentage of D FF's = 10.842%
   
 ![Screenshot 2024-03-31 222449](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/6abcfc62-192c-4797-8917-9b597bbd8a62)
        
 ![Screenshot 2024-03-31 222608](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/32c5635d-7f1b-483f-b8af-d03c27e39192)

 ![Screenshot 2024-03-31 232041](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f9fe058c-63e1-47b1-aadc-940fecd28e13)

   Chip area for the module = 147712.9184
      
 ## Synthesis Report directory
   
The Synthesis Report are found in the directory
      
 ![Screenshot 2024-03-31 231746](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/264ac2e8-72f6-4d88-b0d7-0c971ab2b6d9)

      
      ```bash
         ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-04_19-21/reports/synthesis/1-yosys_4.stat.rpt
      ```
      
The synthesis Results are found in the directory
         
         ```bash
         ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-04_19-21/results/synthesis/picorv32a.synthesis.v
         ```

 ## Day2 Good floorplan vs bad floorplan and introduction to library cells
   
 ## Floorplanning and Intro to Library Cells

 The LAB gives the complete flow of the Floorplanning and the placement process
 After the Synthesis process, type the command for running the Floor planning
     
 ![Screenshot 2024-04-02 214540](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b19981d4-6de8-493f-ae65-20d0c7e363a8)

The configuration files are inside the location
   ```bash
     /Desktop/work/tools/openlane_working_dir/openlane/configurations/README.md
   ```
   Before run the floorplanning, we required some switches for the floorplanning. these we can get from the configuration from openlane.
   
![Screenshot 2024-04-02 215656](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a32e4a2b-d6ae-4a9f-bef2-96ef4aa8f72a)

Here we can see that the core utilization ratio is 50% (bydefault) and aspect ratio is 1 (bydefault). similarly other information is also given. But it is not neccessory to take these values. we need to change these value as per the given requirments also.

Here FP_PDN files are set the power distribution network. These switches are set in the floorplane stage bydefault in OpenLANE.

![Screenshot 2024-04-02 220209](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f6a1802a-8d4b-446a-9e08-d23328bce59f)

 Here, (FP_IO MODE) 1, 0 means pin positioning is random but it is on equal distance.

In the OpenLANE lower priority is given to system default (floorplanning.tcl), the next priority is given to config.tcl and then priority is given to PDK varient.tcl (sky130A_sky130_fd_sc_hd_congig.tcl).

In the run folder, we can see the connfig.tcl file. this file contains all the configuration that are taken by the flow. if we open the config.tcl file, then we can see that which are the parameters are accepted in the current flow.

 ![Screenshot 2024-04-02 220647](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/26f3c80a-bd45-4e08-8caf-00b629f5c91e)
 In this particular location from the floorplan.def file, we can able to see the area of the chip
 
 ![Screenshot 2024-04-02 010306](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b0a351d-71ef-442b-91c3-7de5a83b12bb)

![Screenshot 2024-04-02 214343](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/87f882b4-f642-4d13-a16b-9c3c46c7c360)

         1000 unit distance = 1 Micron

         Distance in micron = value
                            ----------
                               1000

        Die width in micron = 660685 
                             ---------
                               1000
                            
       Die height in micron =  671405 
                              ---------
                                1000

      Area of die in micron = 660.685*671.405 Square micron 
      
   Locate to this directory
   
     ```bash 
        ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/01-04_19-21/results/floorplan
     ```   
  To see the actual layout after the flow, we have to open the magic file by adding the command   `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef 
  read ../../tmp/merged.lef def read picorv32a.floorplan.def &`   

- Floorplan def in Magic

![Screenshot 2024-04-02 221927](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5ccd59b0-d3e1-4c3b-955e-913f1a7e46a2)

 ![Screenshot 2024-04-02 222243](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/474dafb8-a87f-4a35-9d2f-4aba4b5e0fbc)
 
- The side rows,the Decap cells are arranged at the border of the side rows.
  
![Screenshot 2024-04-02 222333](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c49e41a0-7e96-4f97-bbe1-cc036e30ba01)

- Horizontal metal layer
![Screenshot 2024-04-02 222516](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/89dafdf7-4b1a-43dd-af26-e533dc85b83e)

- Vertical metal layer
   
![Screenshot 2024-04-02 222949](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/aaef8b08-aaa6-4b7f-a44c-dede7e38fe43)

- Subcells   
![Screenshot 2024-04-02 223201](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/4d2a9f25-4b5c-4421-915c-08a333e86209)
    
![Screenshot 2024-04-02 223245](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/18f55b1e-b96c-4479-a1db-e3b7fc90c871)

- Standard cells
![Screenshot 2024-04-02 223601](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/353f37fd-c98f-4524-8010-569f938ef377)

- To watch how Placementplane looks, we have to go in the results.
 ![plac def](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b611e4f-acd7-4dd1-be03-2dea3bfc1701)

- These switches are set in the Placementplane stage bydefault in OpenLANE.
 ![Screenshot 2024-04-02 220252](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bc6f0358-59a2-4810-b514-c7fa54e116c5)

 - Before run the Placement, we required some switches for the Placement. these we can get from the configuration from openlane.      
![p](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a41e1a83-d708-473e-9e74-3fb0673a13ee)

 To run the Placement, the command is
    `run_placement`
  The Magic file to see actual view of standerd cells placement.And the actual view in the magic file is given below.  
  Commands to load placement def in magic
     `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &`
    
![Screenshot 2024-04-02 224536](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e5c18ac5-f486-47c4-88cb-6622452c2edd)

![Screenshot 2024-04-02 224656](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ed624fcf-c2d4-491f-b0cf-0e937af32919)

- If we zooom into this, we can find the buffers, gates, flip flops in this.
![Screenshot 2024-04-02 225033](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/67ec7994-57bb-4db7-85d0-4e929c7c6d0c)

- Via      
![Screenshot 2024-04-02 225354](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e42ecad0-704c-4356-b1bb-689ffce3067d)

- Vertical metal layer., metal 4      
![Screenshot 2024-04-02 225442](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/aa3616e5-1381-4d34-a7b6-b9680af7c395)

- Horizontal metal layer i.e., metal 5      
![Screenshot 2024-04-02 225534](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7b509b47-7e89-4bb2-927e-f6a621e9f22a)

## Day 3 - Design library cell using Magic Layout and ngspice characterization

- Topmost cell in window picorv32a      
![Screenshot 2024-04-02 225940](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/73104a12-a25b-465a-b386-10f808d48fc5)

Every Design is represented by equivalent cell design. All the standard cell designs are available in the Cell Library. A fully custom cell design that meets all rules can be added to the library. To begin with, a CMOS Inverter is designed in Magic Layout Tool and analysis is carried out using NGSPICE tool.

Go to this directory to git clone the files
 `/Desktop/work/tools/openlane_working_dir/openlane`
 
Git clone the files from GitHub to your local pc
   `git clone https://github.com/nickson-jose/vsdstdcelldesign.git`
![Screenshot 2024-04-03 001705](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/0bfaece1-48a0-4ae2-bb9d-d8b2dbb58f74)
open another terminal and go to the location

  `/home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic`
  
copy the sky130A.tech file from this location to the git cloned location.
![Screenshot 2024-04-03 002158](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a22c00a1-6b30-4825-a767-3d1bbccbb6b2)

Now, we can see that this file is copied in the vsdstdcelldesign folder.
![Screenshot 2024-04-03 002314](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/904785bc-6228-48a2-a789-20724d1d25c1)

Now initialize magic
  `  magic -T sky130A.tech sky130_inv.mag & `
![Screenshot 2024-04-03 002627](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9497e5a8-4cf4-4785-b27c-93339f3d417d)

In sky130, every color is showing the different layer. here the first layer is for local interconnect shown by blue_purple color, then second layer is metal 1 which is shown by light purple color, and the
metal 2 is shown by pink color. N-well is shown by solide das line. green is N-diffusion region. and red is for polysilicon gate. similarly the brown color is for P-diffusion.
- Inverter layout
![Screenshot 2024-04-03 002733](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bf1ee59b-946f-404a-93da-0699b61589bd)

![Screenshot 2024-04-03 003136](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f848da20-282e-48e4-a63a-1fb90aeb2d8c)

- nmos
![Screenshot 2024-04-03 003303](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/92c2b2b3-3d9a-4edf-bd1e-e675210b3563)

 we will check for the output terminal also.(by double pressing "S" to select the entire thing at output Y).
  so, we can see that "Y" is attached to locali in cell def sky130_inv.
we can check the source of the PMOS is connected to the ground or not. and similarly we can check it for NMOS also.
![Screenshot 2024-04-03 003759](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9f8d39be-4e0c-43b0-aca0-5fb56df46113)

- Connection between source and VDD in Pmos
![Screenshot 2024-04-03 003854](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f04c1791-c9cb-4f92-8e89-b51260f84c37)

- Connection between source and Ground in Nmos
![Screenshot 2024-04-03 003938](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/766c98b8-ed95-479f-a8ad-31bf4cd757cb)

Now open the tkcon window and type the commands for extracting the files. Bute before that see lets see its location 
        `pwd`  
To extract the file from here, we have to write the command in tckon window and the comand is `extract all`
![Screenshot 2024-04-03 004306](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/95b54116-8561-49b3-952c-a20f206303e9)

we will use this .ext file to create the spice file to be use with our ngspice tool. for that we have apply the command `ext2spice cthresh 0 rthresh 0`,this will not create anything new.
now again we have to type `ext2spice` command in tckon window.
![Screenshot 2024-04-03 004650](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ea00f51b-ff01-47a6-8e58-4f97bb40a8a2)

so, now we are checking the location and at there spice file has been created.
![Screenshot 2024-04-03 004729](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b5140209-0503-4f61-9217-6371237f721e)

let's see what is inside the spice file by "vim sky130_inv.spice".
![Screenshot 2024-04-03 005032](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f79b84f1-2371-40cc-853b-a56ffe985850)
Now we have to include the PMOS and NMOS lib files. it is inside the libs folder in the vsdstdcellsdesign folder.
![Screenshot 2024-04-08 161011](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/92f8f506-beb9-49b3-abe9-d4ba067e633a)
let's see inside PMOS lib file.
![Screenshot 2024-04-04 153800](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5ef356eb-c8cd-46fa-839f-2e613b722506)
Measuring unit distance in layout grid
![Screenshot 2024-04-05 185633](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/6838aa04-32bd-4036-b4d7-4cb5740149e7)

![Screenshot 2024-04-08 153747](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/06df880d-8dc4-488a-99f6-2c16461b3bba)

run the spice file in ngspice

  ` ngspice sky130_inv.spice`
  
To plot the graph between Voltage and time type the command in ngspice

   `plot y vs time a`
   
after running this file we get output of ngspice like this,
![Screenshot 2024-04-06 002259](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5c88402b-5401-4b30-b3b5-09b4b9c10788)

- Transient response output V = 3.3v
   80% of V is 2.64v
   20% of V is 0.65v
![Screenshot 2024-04-06 002339](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7dfd5fad-be9e-4029-bb45-bdbaae1bda18)

![Screenshot 2024-04-06 003511](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a750f5cc-6246-4856-b00a-53465b1c0888)

![Screenshot 2024-04-06 004214](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/fea69f33-08bf-49e5-8a08-6c2e8912f6a3)

![Screenshot 2024-04-06 004138](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/528a5661-6598-4a36-8d28-51943b112092)

![Screenshot 2024-04-06 004913](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/fc739aad-bd22-47a8-9687-0958ca2ad199)

![Screenshot 2024-04-06 005056](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/19e84e70-45ae-45d0-996a-028a46e0281f)

![Screenshot 2024-04-06 154821](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/639eea30-56d0-438d-9cfa-a4b61377cb2e)

![Screenshot 2024-04-06 154939](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b41cdc3e-adb9-4768-a378-077c102b70c4)

![Screenshot 2024-04-06 155011](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f2e2b1a5-9980-47d0-90e1-1fa05a03c6c8)

![Screenshot 2024-04-06 155121](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9a4f5476-4b14-4abf-ac17-049f0a5c1962)

![Screenshot 2024-04-06 005559](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7e3521ff-063b-452e-9760-227053aaa747)

![Screenshot 2024-04-06 010332](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/23e5496d-b772-43d3-8749-30225e796455)

![Screenshot 2024-04-06 010449](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bc8cd182-4f06-4770-b83a-37ea9d10c2f8)

![Screenshot 2024-04-06 010646](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/4394d68e-b013-41dd-9722-98ffff5633b9)

![Screenshot 2024-04-06 011114](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8d7323ce-f036-4a6f-83dd-f00da617b8de)

![Screenshot 2024-04-06 011144](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f3b343fe-1277-4d30-80a0-4dc44d2be1ef)

![Screenshot 2024-04-06 011431](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/380a7f32-5a4f-4e02-a08b-9ad07a7f1378)

![Screenshot 2024-04-06 011553](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e663d62f-d18a-471a-8748-c8d6525a93de)

![Screenshot 2024-04-06 012239](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/57b5c278-46e4-42fa-9f70-61d88b5e8a37)

![Screenshot 2024-04-06 012239](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/03c81be0-6b6c-430a-9cd2-b753d7321f37)

![Screenshot 2024-04-06 012348](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d6d37c41-abe9-45a5-9c52-c5c06a3468fc)

![Screenshot 2024-03-31 215317](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/aae4c69d-5bf1-4d03-bb60-a8443886ade1)

![Screenshot 2024-04-06 014555](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/23a4c539-317b-49b0-b69e-890573a57b35)

![Screenshot 2024-04-06 142503](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bfa6c5df-ae6f-4fd0-86f4-719fb9752304)

![Screenshot 2024-04-06 143302](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2f7e5949-32c1-4f85-835e-569ea079976c)

![Screenshot 2024-04-06 145505](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d4b7ab17-dedc-4c6b-982a-13843d6c2de8)

![Screenshot 2024-04-06 145607](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/180134f8-7459-43b1-9e30-5c3817b5d2eb)

![Screenshot 2024-04-06 145825](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9cf64b34-5ff0-4804-9766-82f01452a56c)

![Screenshot 2024-04-06 150235](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/12fa6efb-a1d1-44f3-93e9-a9477df95920)

![Screenshot 2024-04-06 150401](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/1e48c44c-38a7-4102-8dff-8c6fa7ebcd9f)

![Screenshot 2024-04-06 150453](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/facab920-65c4-4c05-8588-0fb7fdf71014)

![Screenshot 2024-04-06 150531](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f2a7baba-dd6b-4c26-8e7d-ccf44b2712e6)

![Screenshot 2024-04-06 150629](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/0b97be34-b66d-4e78-8ce9-1a8583b90e52)

![Screenshot 2024-04-06 150814](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c746d413-06d4-4b70-a110-ef4de1ceca8f)

![Screenshot 2024-04-06 151452](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/25538310-8805-499b-b144-2b88ace99bfc)

![Screenshot 2024-04-06 151535](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e6188e19-a829-40d0-b9b4-34f43a3af6d2)

![Screenshot 2024-04-06 151636](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e2087d10-cd10-46ef-a5e4-c061e7391745)

![Screenshot 2024-04-06 151806](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/09aba464-d544-4d08-befb-68f19ff7c0d4)

![Screenshot 2024-04-06 151949](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c1d61609-47a8-419e-9d32-1059230b1593)

![cts](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b562788f-fb4c-491c-b0f0-83820777232d)

![c tcl](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/71bab7b2-16ca-4d61-ae22-046f2d1902af)

![Screenshot 2024-04-07 114529](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b7d943b5-a439-440f-873e-4889de1485fa)

![Screenshot 2024-04-07 114617](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e91dae15-4970-47e6-9066-04705fc6f982)

![Screenshot 2024-04-07 114707](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/616a2d1f-82eb-4aab-b971-f15222b5aa38)

![Screenshot 2024-04-07 114819](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7e9b39a9-83fe-4647-852c-1f370c5c9e64)

![Screenshot 2024-04-07 114935](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f0e42b26-0030-4196-811b-b2ecb2379211)

![Screenshot 2024-04-07 115016](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/042dd58c-7014-4b82-9b28-fdc13b2e4ede)

![Screenshot 2024-04-07 115113](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ee59e352-e755-4702-9925-e4a6603c1f3a)

![Screenshot 2024-04-07 115147](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ee626e67-79be-4f50-b1cc-f61971ca2cdc)

![Screenshot 2024-04-07 115242](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/91dfc935-202f-432b-82bb-e50455805e59)

![Screenshot 2024-04-07 122156](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/cdeba130-6af2-4b61-87cf-214c652147eb)

![Screenshot 2024-04-07 122306](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/50ec9f3d-3aaf-4210-ad61-ef22c171dc09)

![Screenshot 2024-04-07 122657](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2848e87a-1ae9-43ca-afa8-4173c5776bed)

![Screenshot 2024-04-07 122840](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/323c806f-16f3-4911-89e8-9c825b78c969)

![Screenshot 2024-04-07 123012](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b72dac5e-c5d4-4cd8-8365-a4eef129c5dd)

![Screenshot 2024-04-07 123210](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/af919464-c861-4f71-8161-1f39cdd55d43)

![Screenshot 2024-04-07 124001](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f7b1cd63-f423-4e12-a4f2-567a530df6d5)

![Screenshot 2024-04-07 124137](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2852155c-6104-4455-bbef-b74f5859b1d6)

![Screenshot 2024-04-07 124220](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e32fe091-a9b2-4848-9b0f-d5f5726e3635)

![Screenshot 2024-04-07 124510](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c846a389-7fbf-4fb8-970e-8ec2678058a4)

![Screenshot 2024-04-07 125028](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b7ae1697-0dd8-4748-a2a3-d1036288db12)

![Screenshot 2024-04-07 125131](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8adece7d-d61d-4cba-bf23-ffb8364b3089)

![Screenshot 2024-04-07 125225](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/09fa51f1-6f3c-4de8-9171-46374e86429f)

![Screenshot 2024-04-07 125605](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c7d1c616-0128-4bf3-bca8-249d878bb051)

![Screenshot 2024-04-07 125704](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8a7fce0a-df7b-4c6e-bc1a-ad03b47e0ccb)

![Screenshot 2024-04-07 125726](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/3b9f4e83-d42e-4118-b1d1-6fb6bfa2207c)

![Screenshot 2024-04-07 125858](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/eb32e6a3-dd9f-4465-b720-6ad60713a6a9)

![Screenshot 2024-04-07 130359](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/3efb77e5-de23-4981-80eb-47f8fcdb42e5)

![Screenshot 2024-04-07 130456](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/042e0432-ab0a-4334-88ff-c0f47a1dad34)

![Screenshot 2024-04-07 130602](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2a5fd557-3fd4-4121-99cd-969b41b494cc)

![Screenshot 2024-04-07 131107](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/0ae684db-9376-4412-b595-ab613c83c244)

![Screenshot 2024-04-07 131150](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/72a0edc0-56a0-4bd0-bb35-7229109104f7)

![Screenshot 2024-04-07 225814](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/1e8f79ed-55f3-4340-ad1d-bf6ab1a2439a)

![Screenshot 2024-04-07 230459](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9151b6f7-8ffa-4daf-b7eb-902b58867a1a)

![Screenshot 2024-04-07 231259](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9b692062-527d-484c-8bac-40cb4bb02df4)

![Screenshot 2024-04-07 231409](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7bd7c56c-1494-4cd5-affc-4184b3875a20)

![Screenshot 2024-04-07 232758](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/39d42b79-a495-4699-bd3b-aefcd9a5ed67)

![Screenshot 2024-04-07 233207](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e50849f9-8e70-497a-8e59-fceda61490b9)

![Screenshot 2024-04-07 233404](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/1f765b74-0424-4876-b532-b5331a50487f)

![Screenshot 2024-04-07 233615](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/98274535-28e4-468f-b74a-374a485dfe74)

![Screenshot 2024-04-07 233705](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ffa0ef1b-5eac-4dcf-a002-2a2504cab663)

![Screenshot 2024-04-07 233934](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/1b467030-d98a-44f2-ba4c-9ce5b3add9f4)

![Screenshot 2024-04-07 234009](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b8cf020-46a9-4ee7-9d98-b2422f73d1bf)

![Screenshot 2024-04-07 234601](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/764048ac-036e-4853-ac6e-6120601d436a)

![Screenshot 2024-04-07 234519](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/921afe22-86ce-4d29-aace-77313f2e7fba)

![Screenshot 2024-04-07 235728](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/563f4b8b-581b-4743-97f0-534ef2895d54)

![Screenshot 2024-04-08 163333](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/fdfbbb40-2289-4896-9a53-ebc2641446df)

![Screenshot 2024-04-08 163428](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b8b3df0d-d984-49ca-8fb3-853e469f6813)

![Screenshot 2024-04-08 163453](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d52d961a-4fc2-4a8d-a3af-1b92c98ada42)
## Section 5 - Final steps for RTL2GDS using tritonRoute and openSTA

Perform generation of Power Distribution Network (PDN) and explore the PDN layout.
Commands to perform all necessary stages up until now
```bash
   # Change directory to openlane flow directory
   cd Desktop/work/tools/openlane_working_dir/openlane
   
   # alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
   # Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
   docker
   # Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
   ./flow.tcl -interactive
   
   # Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
   package require openlane 0.9
   
   # Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
   prep -design picorv32a
   
   # Addiitional commands to include newly added lef to openlane flow merged.lef
   set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
   add_lefs -src $lefs
   
   # Command to set new value for SYNTH_STRATEGY
   set ::env(SYNTH_STRATEGY) "DELAY 3"
   
   # Command to set new value for SYNTH_SIZING
   set ::env(SYNTH_SIZING) 1
   
   # Now that the design is prepped and ready, we can run synthesis using following command
   run_synthesis
   
   # Following commands are alltogather sourced in "run_floorplan" command
   init_floorplan
   place_io
   tap_decap_or
   
   # Now we are ready to run placement
   run_placement
   
   # Incase getting error
   unset ::env(LIB_CTS)
   
   # With placement done we are now ready to run CTS
   run_cts
   
   # Now that CTS is done we can do power distribution network
   gen_pdn
```
Screenshots of power distribution network run
![Screenshot 2024-04-08 164124](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9af544ce-97e4-4950-9920-a6f574c78f1f)

![Screenshot 2024-04-08 164251](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/0df5d473-6865-41b6-88e5-4dee146cab80)

![Screenshot 2024-04-08 165534](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/66f3d5b5-3f98-4635-b462-7e3bb66c7586)

![Screenshot 2024-04-08 165618](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/60ab5bf3-7373-4f73-bc83-7d14e48b3e63)

![Screenshot 2024-04-08 165655](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/47d7ead1-acc3-4e1c-90e0-0dff66089413)

![Screenshot 2024-04-08 165725](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c061dbce-ae6b-40bf-8690-e80c96c98918)

![Screenshot 2024-04-08 165759](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/fde12726-9de9-4292-aacc-57e03d64dfd7)

![Screenshot 2024-04-08 165827](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5af648c1-8da7-47e9-95f1-8c6f50d92c81)

![Screenshot 2024-04-08 165909](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/45e48fcd-4493-44b8-9927-23d8c3058e41)

![Screenshot 2024-04-08 170225](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/cd1df0f4-7aae-4bea-9f8b-bdd080cf6f1c)

![Screenshot 2024-04-08 171326](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e9de6d93-ec27-4019-8d1c-62df1716542a)

![Screenshot 2024-04-08 171409](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/825f4232-4465-47e4-913b-ae545dd13ec4)

![Screenshot 2024-04-08 171511](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e025be35-5471-4846-8e75-ac7509e659ba)

![Screenshot 2024-04-08 171732](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/297f36f8-effc-404b-bfa6-7d42790e6d63)

![Screenshot 2024-04-08 172050](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/223351a7-6a58-4135-89cc-3338e65e7ac0)

![Screenshot 2024-04-08 172455](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d5585379-771e-4dcc-9885-89a5336d21c7)

Commands to load PDN def in magic in another terminal
```bash
   # Change directory to path containing generated PDN def
   cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/tmp/floorplan/
   
   # Command to load the PDN def in magic tool
   magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```
Screenshots of PDN def
![Screenshot 2024-04-08 214953](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5643d170-6924-4e0e-bec4-ea718dd241a3)

![Screenshot 2024-04-08 215115](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a852a80c-bce7-49dc-9d11-044e121031b8)

![Screenshot 2024-04-08 215248](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d92be306-c7d7-456e-aa3f-5fd150b0eab3)

Basics of global and detail routing and configure TritonRoute
The final step of physical design is Routing.
The usage of the `def` command in the image above is to indicate that the latest completed step was the generation of PDN.

The resulting file `17-pdn.def` contains the information from `cts.def` as well as the power distribution network.

If one wants to learn about the various switches available for routing, they can refer to the README.md file located in the configuration folder of the OpenLANE directory.
![r](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b5f38ad9-e107-4151-a4a7-8554ca193ee5)

![r tcl](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b02e49e-0180-4804-8a09-3ab5ce41bda2)
By executing specific commands, we can determine the type of global and detailed routing that will be performed.
In case we want to change the routing type, we can use the `set` command followed by the parameter names mentioned in the routing section of the README.md file.

## Perform detailed routing using TritonRoute and explore the routed layout.
Command to perform routing
       ```bash
         # Check value of 'CURRENT_DEF'
         echo $::env(CURRENT_DEF)
         
         # Check value of 'ROUTING_STRATEGY'
         echo $::env(ROUTING_STRATEGY)
         
         # Command for detailed route using TritonRoute
         run_routing
      ```  
Screenshots of routing run
![Screenshot 2024-04-08 221336](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/d7558d42-d2f1-4a39-bd5d-6ac2663f8ad6)

![Screenshot 2024-04-08 221446](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/fad6abd3-b21a-47fc-9925-4b7647c2d138)

Commands to load routed def in magic in another terminal
```bash
   # Change directory to path containing routed def
   cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/26-03_08-45/results/routing/
   
   # Command to load the routed def in magic tool
   magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
![Screenshot 2024-04-08 221735](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/adaeaa58-c15e-4303-8f12-ea4ed01fc093)

![Screenshot 2024-04-08 222713](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e106ccff-1226-4540-824e-f2273a218fc1)

![Screenshot 2024-04-08 222836](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7eaf0f43-bae2-4f7c-8892-95aa17cc038d)

![Screenshot 2024-04-08 222325](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c76e17d9-bbd4-49cd-bf3d-63edacd2e743)

![Screenshot 2024-04-08 222509](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5c938a7d-2411-4af8-b89a-0211bdc3f7bb)

Screenshots of routed def
![Screenshot 2024-04-08 222615](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/470a7bf1-0db0-41e3-8925-04f68886ee79)



Screenshot of fast route guide present in `openlane/designs/picorv32a/runs/01-04_19-21/tmp/routing` directory
![Screenshot 2024-04-08 223242](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/dba0a2da-3d11-4b52-997e-bd89de810d20)




   
## References
- RISC-V : https://riscv.org/
- VLSI System Design: https://www.vlsisystemdesign.com/
- OpenLANE: https://github.com/The-OpenROAD-Project/OpenLane
- Skywater 130 PDK: https://github.com/google/skywater-pdk
- Open_PDKS:  http://www.opencircuitdesign.com/open_pdks/
- Dgital VLSI Soc Design and planning: https://vsdsquadron.vlsisystemdesign.com/digital-vlsi-soc-design-and-planning/
  
## Acknowledgement
- [Kunal Ghosh](https://github.com/kunalg123), Co-founder, VSD Corp. Pvt. Ltd.
- [Nickson Jose](https://github.com/nickson-jose)
   
