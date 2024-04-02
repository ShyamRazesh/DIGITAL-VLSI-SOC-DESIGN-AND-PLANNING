# DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING

Author: Srinivasa Yashwanth

Acknowledgements: SoC design Program by [Mr. Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836) , [VLSI System Design](https://www.vlsisystemdesign.com)

Day-1
-------------------
## Digital ASIC Design

It is the process of designing an ASIC chip that uses digital logic components, as opposed to analog.

  ![digital asic design jpeg](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/441d867a-4a99-4e58-9be7-5c7ed66cacf3)

## Open Source Digital ASIC Design

  ![open source asic digital design](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/6ccff321-4bb6-48ec-8024-1931d86120f6)

RTL2GDS Flow
--------
   ![Screenshot 2024-03-31 110337](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/5975a14f-7840-418b-8c4f-f868e28a2890)


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
     ![Screenshot 2024-03-31 111302](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/262ddba9-bef6-40ec-a329-87cfdb14fd6b)
     ![Screenshot 2024-03-31 111426](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/ee8d8cf9-8062-4fc4-80ff-945a4e157f1f)

     OpenLANE ASIC Flow
     ----------
     ![Screenshot 2024-03-31 111559](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/e8418512-486b-4340-99ba-793631f07663)

     OpenLANE Directory structure
     ----------
     Basic Linux Commands cd: opens the particular folder ls: lists the content of the folder pwd: shows the present working directory mkdir: to make a new directory command --help: shows the complete use 
     of that command clear: clears the terminal screen
  
      Exploring OpenLANE Directory
     ----
     Working on sky130A(pdk) which contains libs.tech which has respective files on tools such as magic, netgen etc., and libs.ref which has files related to the specific technology.
  
     # Open the working Directory
     
     ![Screenshot 2024-03-31 200154](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/0b7d4eef-fc59-44f4-947a-7e9784568edd)


     ```bash
        cd Desktop
        cd work/tools
        cd openlane_working_dir
       cd openlane
     ```
    ![Screenshot 2024-03-31 200453](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/1058fb06-bc72-45ae-8b99-178001dceb9a)
   
   ## To open the Openlane
   
        After getting into the directory, enter the commands
        
    ![Screenshot 2024-03-31 201104](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/0161131d-48e7-4196-b155-a958aa2a3274)
   
            ```bash
              docker
              pwd
              ls -ltr
            ```
   ## Interactive Mode
   
          To open the openlane in interactive mode, 
      
      ![Screenshot 2024-03-31 215317](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/519d0e5a-7307-4032-8cc0-5857dc928b3b)
      
   You may run the interactively by using the  `-interactive`  option:
   
      ```bash
        ./flow.tcl -interactive
      ```
            
      To prepare the openlane,
      
   ![Screenshot 2024-03-31 220804](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/4a9bebde-b9cb-4b69-8c0e-31f086e0ec24)
   
       ```bash
          package require openlane 0.9
          prep - design picorv32a
       ```
            
      ### Synthesis
     To run the Synthesis
   
            ```bash
             run_synthesis
            ```
   
      ![Screenshot 2024-03-31 220804](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/bc3b73b0-4abc-43e0-a515-3d362969ebfe)
            
      ## Report generated after synthesis
   

       Before running, we saw that the result folder was empty. But now, after running the synthesis, we can see that all the mapping has been done by ABC.
   And in the report, we can see when the actual synthesis has been done. and the actual statistics synthesis report is shown below, which is the same as what we have seen before.

      ![Screenshot 2024-03-31 223408](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/0d45266c-f1c0-4c45-b025-5a97a763b751)
      
      Particularly we are interested in finding the Flop ratio. This can be calculated by using the formula:
   
       Flop Ratio = No. of D FlipfLops/Total No. of cells
      
                   =1613/14876
      
                   =0.10842
      
        Percentage of D FF's = 10.842%
      
   ![Screenshot 2024-03-31 222449](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/8392d8fe-fc26-470b-bdc0-0f6ea7f84e6d)

   ![Screenshot 2024-03-31 222608](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/de7f0707-46d4-4ed0-869d-e24a30ae0a54)

      ![Screenshot 2024-03-31 232041](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/3d0038c0-6d6b-4f96-9054-cbc9b00ccdc1)
   
   Chip area for the module = 147712.9184
      
      ## Synthesis Report directory
   
      The Synthesis Report are found in the directory

    ![Screenshot 2024-03-31 231746](https://github.com/ShyamRazesh/Digital-VLSI-SOC-Design-and-Planning/assets/138649249/bec9aa9e-43fd-4d3a-a0f9-59b7e21dbaa8)
      
      ```bash
         ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/reports/synthesis/1-yosys_4.stat.rpt
      ```
      
      The synthesis Results are found in the directory
         
         ```bash
            ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/results/synthesis/picorv32a.synthesis.v
         ```

   ## Day2
   
    ## Floorplanning and Intro to Library Cells
