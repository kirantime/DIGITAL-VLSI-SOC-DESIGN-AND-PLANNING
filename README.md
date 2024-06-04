# DIGITAL VLSI SOC DESIGN AND PLANNING
## DAY 1 : Design Preparation :
 
 ## OpenLANE Directory structure in detail
  
  ## Basic Linux Commands

cd : opens the particular folder

ls or ls -ltr : lists the content of the folder with permission 
pwd : shows the present working directory or its path 
mkdir : to make a new directory
command --help : if need any help use 
man command : man -f or -k [option]
clear : clears present terminal screen
history : To know history : 
  
  # introduction
  
  ## what is openlane :
  
  OpenLane is a cutting-edge platform for silicon implementation that utilizes open source technologies for chip development. It encompasses various RTL designs and open-sourced EDA Tools. The missing component in the complete open source chip development was provided by the SKY130 PDK from Skywater Technologies and Google. Several EDA Tools played specific roles in the design cycle, but there was a lack of a clean design flow, and the Skywater PDKs were only compatible with industry tools. OpenLane addressed these issues by offering a completely automated RTL to GDSII flow. OpenLane is not just a tool, but a comprehensive flow that incorporates numerous EDA tools, such as Yosys for synthesis, OpenSTA for STA analysis, and automation scripts, all tailored to work seamlessly with the Skywater PDKs and open-source EDA tools.
  
## SkyWater sky130 Open Source PDK :

 Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open-source Process Design Kit and related resources. This kit can be used to create manufacturable designs at SkyWater’s facility. We are currently working on the sky130A_sky130_fd_sc_hd_config is skywater130nm PDK variant. In this context, "sky130" refers to the process name or node technology, "fd" represents the foundry name (SkyWater foundry), "sc" denotes standard cell library files, and "hd" stands for high density, is one type of variant.
 
 ## Design Preparation Step :

 in this lab we'll dive into the synthesis process for the specific design, picorv32a, utilizing the OpenLane flow. Our objective is to generate the netlist and other essential reports following the synthesis step. Before proceeding, it's very important to ensure the smooth operation of the virtual machine environment of ubuntu or any other linux os. Once everything is confirmed to be functioning optimally, as installed required openlane packages into your terminal, we'll observe a terminal interface within the virtual machine environment, resembling the following: 

 ![flow_tcl_interactive](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/092814ef-bbb2-49d4-81cc-c1ad3be5901c)
 Invoke docker: to start the docker container. that allows you to build, test, and deploy applications quickly.

When we run the docker command invoke the openlane tool, the terminal will look like above img
So, let's navigate to the directory   path: $cd Desktop/work/tools/openlane_working_dir/openlane. This is the openlane pwd, it is essential for executing the synthesis steps effectively. After gone to pwd, we will run a docker command. Docker is like a magic box that bundles up all the stuff needed to run a program or input all the packages required to run the flow., like OpenLane for chip design, ensuring everything works the same no matter where you run it. but here we running in the above path for our convenience.
  

when we are entering in the OpenLANE, we have to use ./flow.tcl because as a name says it goes with the flow using the script. using this -Interactive switch for the step by step implemented in the process, otherwise it will run complete flow as translated from "RTL to GDSII". by using command #  ./flow.tcl -interactive  switch. That means, OpenLANE is now open and we can also see that the prompt will change now.
  after that, the prompt will appear like % symbol, next we required to import all the packages to run this flow so that procees need to be done like every time "%package require openlane 0.9" 
  right now we ready to execute the command 
 
  Now, in openlane, we are going to run the synthesis, but before synthesis, we have to prepare design setup stage. for that command is  prep -design picorv32a
  ![Screenshot 2024-05-25 133920](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/15aab6a9-5889-4fb6-99bf-1a22b03d31be)

  ![view created runs as date all emty exp tmp file](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/abdd2512-1bfd-496e-801c-9a7e5ca0f208)

  here we can see the preparation completed by following {src and config.tcl} in the picorv32a file the run directory has been created with today's date. It contains the necessary folders for OpenLane. The temp file has the merged.lef file, which holds wire, layer, and cell level information. $cd 
  Desktop/work/tools/openlane_working_dir/openlane/design/picorv32a/ explore whether this file contains, you will identify some changes after the synthesis completed

Now, if we go into the design folder in openlane, there are nearly 30-40 designs are already built. Out of them, we can open any of the designs. here we are opening the picorv32a.v design. In this design folder, we can see many files are available. i.e., src[.v+_sdcfile], config.tcl[default switch info], etc. This config.tlc file contains every detail specific to the design. for example, details about enrollment, clock period, clock period port, etc.
  
  
![runsynthes successfl](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/847b8816-e47d-453b-ba8b-ddd47b2ef299)

Now there is also a config.tcl file available in addition to the design folder. This config.tcl file contains all the default parameters used by the run.

When we make changes to the original configuration and then run it, for example, if we modify the core utilization in the floorplanning and then run the floorplanning, at this point in the config.tcl file, the core utilization will change. By cross-checking it, we can verify if the modification is reflected in the execution or not.

Now moving to openlane, we are going to run the synthesis. The command run_synthesis after the preparation is completed successfully
It will take a few minutes to complete the synthesis.

![runsynthes successfl](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/35a50516-1b69-4ad8-9e71-f3392aeb811e)
## To synthesize the design:
Yosys performs RTL synthesis
ABC performs technology mapping
OpenSTA performs static timing analysis on the resulting netlist to generate timing reports

# Day1 assignment to find flip flops ratio: 
 During synthesis, the total number of D flip-flops is 1613, and the number of cells is 14876. The flop ratio, calculated as the number of flip flops divided by the total number of cells, flops ratio is 0.10842, and in percentage is 10.84%.

after that run_synthesis you will see that in the run directory another folder created as date format directory folder of picorv32a

![Screenshot 2024-05-25 160134](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/837f2cec-dd6c-4d28-9bfe-20d9d10314be)

![Screenshot 2024-05-25 161819](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/29713def-5493-47d5-9102-1fe38d4612bc)

Before running, we noticed that the result folder was empty. However, after completing the synthesis, we observed that all the mapping had been performed by ABC. The synthesis report shows the exact time when the synthesis was completed, and the statistical synthesis report is displayed below, matching what we had seen previously

# Day 2 floorplanning :  
 ## steps to run floorplan using openlane :
 
 



