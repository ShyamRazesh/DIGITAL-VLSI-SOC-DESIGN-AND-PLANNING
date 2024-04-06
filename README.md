# DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING

Author: Srinivasa Yashwanth

Acknowledgements: SoC design Program by [Mr. Kunal Ghosh](https://www.linkedin.com/in/kunal-ghosh-vlsisystemdesign-com-28084836) , [VLSI System Design](https://www.vlsisystemdesign.com)

Day-1
-------------------
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
         ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/reports/synthesis/1-yosys_4.stat.rpt
      ```
      
      The synthesis Results are found in the directory
         
         ```bash
            ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-03_15-37/results/synthesis/picorv32a.synthesis.v
         ```

   ## Day2
   
    ## Floorplanning and Intro to Library Cells
     
      ![Screenshot 2024-04-02 214540](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b19981d4-6de8-493f-ae65-20d0c7e363a8)

      ![Screenshot 2024-04-02 010306](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b0a351d-71ef-442b-91c3-7de5a83b12bb)

      ![Screenshot 2024-04-02 214343](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/87f882b4-f642-4d13-a16b-9c3c46c7c360)
   
      ![Screenshot 2024-04-02 215656](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a32e4a2b-d6ae-4a9f-bef2-96ef4aa8f72a)

      ![Screenshot 2024-04-02 220209](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f6a1802a-8d4b-446a-9e08-d23328bce59f)

      ![Screenshot 2024-04-02 220252](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bc6f0358-59a2-4810-b514-c7fa54e116c5)

     ![Screenshot 2024-04-02 220341](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a5ae278b-e4b3-4bc8-886a-d80e69215c51)

     ![Screenshot 2024-04-02 220647](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/26f3c80a-bd45-4e08-8caf-00b629f5c91e)

     ![Screenshot 2024-04-02 221927](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5ccd59b0-d3e1-4c3b-955e-913f1a7e46a2)

     ![Screenshot 2024-04-02 222243](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/474dafb8-a87f-4a35-9d2f-4aba4b5e0fbc)

     ![Screenshot 2024-04-02 222333](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/c49e41a0-7e96-4f97-bbe1-cc036e30ba01)

    ![Screenshot 2024-04-02 222516](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/89dafdf7-4b1a-43dd-af26-e533dc85b83e)

    ![Screenshot 2024-04-02 222906](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/2b7952d7-1402-4e19-91fa-a514685eee31)
   
    ![Screenshot 2024-04-02 222949](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/aaef8b08-aaa6-4b7f-a44c-dede7e38fe43)
   
    ![Screenshot 2024-04-02 223201](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/4d2a9f25-4b5c-4421-915c-08a333e86209)
    
    ![Screenshot 2024-04-02 223245](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/18f55b1e-b96c-4479-a1db-e3b7fc90c871)

    ![Screenshot 2024-04-02 223601](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/353f37fd-c98f-4524-8010-569f938ef377)

    ![plac def](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/8b611e4f-acd7-4dd1-be03-2dea3bfc1701)

    ![p](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a41e1a83-d708-473e-9e74-3fb0673a13ee)

    ![Screenshot 2024-04-02 224536](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e5c18ac5-f486-47c4-88cb-6622452c2edd)

    ![Screenshot 2024-04-02 224656](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ed624fcf-c2d4-491f-b0cf-0e937af32919)

    ![Screenshot 2024-04-02 225033](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/67ec7994-57bb-4db7-85d0-4e929c7c6d0c)
      
   ![Screenshot 2024-04-02 225354](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/e42ecad0-704c-4356-b1bb-689ffce3067d)
      
   ![Screenshot 2024-04-02 225442](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/aa3616e5-1381-4d34-a7b6-b9680af7c395)
      
   ![Screenshot 2024-04-02 225534](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/7b509b47-7e89-4bb2-927e-f6a621e9f22a)
      
   ![Screenshot 2024-04-02 225940](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/73104a12-a25b-465a-b386-10f808d48fc5)

   ![Screenshot 2024-04-03 001705](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/0bfaece1-48a0-4ae2-bb9d-d8b2dbb58f74)

   ![Screenshot 2024-04-03 002158](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/a22c00a1-6b30-4825-a767-3d1bbccbb6b2)

   ![Screenshot 2024-04-03 002314](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/904785bc-6228-48a2-a789-20724d1d25c1)

   ![Screenshot 2024-04-03 002627](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9497e5a8-4cf4-4785-b27c-93339f3d417d)

   ![Screenshot 2024-04-03 002733](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/bf1ee59b-946f-404a-93da-0699b61589bd)

   ![Screenshot 2024-04-03 003136](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f848da20-282e-48e4-a63a-1fb90aeb2d8c)

   ![Screenshot 2024-04-03 003303](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/92c2b2b3-3d9a-4edf-bd1e-e675210b3563)

   ![Screenshot 2024-04-03 003759](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/9f8d39be-4e0c-43b0-aca0-5fb56df46113)

   ![Screenshot 2024-04-03 003854](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f04c1791-c9cb-4f92-8e89-b51260f84c37)

   ![Screenshot 2024-04-03 003938](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/766c98b8-ed95-479f-a8ad-31bf4cd757cb)

   ![Screenshot 2024-04-03 004306](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/95b54116-8561-49b3-952c-a20f206303e9)

    ![Screenshot 2024-04-03 004650](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/ea00f51b-ff01-47a6-8e58-4f97bb40a8a2)

    ![Screenshot 2024-04-03 004729](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b5140209-0503-4f61-9217-6371237f721e)

    ![Screenshot 2024-04-03 005032](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/f79b84f1-2371-40cc-853b-a56ffe985850)
  
    ![Screenshot 2024-04-04 153800](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5ef356eb-c8cd-46fa-839f-2e613b722506)

![Screenshot 2024-04-05 185633](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/6838aa04-32bd-4036-b4d7-4cb5740149e7)

![Screenshot 2024-04-05 231732](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/b778a8ed-3039-47a1-a326-c67c9ae55a24)

![Screenshot 2024-04-06 002259](https://github.com/ShyamRazesh/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/138649249/5c88402b-5401-4b30-b3b5-09b4b9c10788)

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





   ##
   
   Skywater 130 PDK: https://github.com/google/skywater-pdk

   Open_PDKS:  http://www.opencircuitdesign.com/open_pdks/
   
   Digital VLSI Soc Design and planning: https://vsdsquadron.vlsisystemdesign.com/digital-vlsi-soc-design-and-planning/



   
