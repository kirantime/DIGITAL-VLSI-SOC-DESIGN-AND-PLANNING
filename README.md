# DIGITAL VLSI SOC DESIGN AND PLANNING
DAY 1
# OpenLANE Directory structure in detail
  
  # Basic Linux Commands

cd : opens the particular folder

ls or ls -ltr : lists the content of the folder with permission 

pwd : shows the present working directory or its path 

mkdir : to make a new directory

command --help : if need any help use 

man command : man -f or -k [option]

clear : clears present terminal screen

history : To know history : 
  
  # introduction
  
  # what is openlane :
  
  OpenLane is a cutting-edge platform for silicon implementation that utilizes open source technologies for chip development. It encompasses various RTL designs and open-sourced EDA Tools. The missing component in the complete open source chip development was provided by the SKY130 PDK from Skywater Technologies and Google. Several EDA Tools played specific roles in the design cycle, but there was a lack of a clean design flow, and the Skywater PDKs were only compatible with industry tools. OpenLane addressed these issues by offering a completely automated RTL to GDSII flow. OpenLane is not just a tool, but a comprehensive flow that incorporates numerous EDA tools, such as Yosys for synthesis, OpenSTA for STA analysis, and automation scripts, all tailored to work seamlessly with the Skywater PDKs and open-source EDA tools.
  
# SkyWater sky130 Open Source PDK :

 Open Source PDK is a collaboration between Google and SkyWater Technology Foundry to provide a fully open-source Process Design Kit and related resources. This kit can be used to create manufacturable designs at SkyWater’s facility. We are currently working on the sky130A_sky130_fd_sc_hd_config is skywater130nm PDK variant. In this context, "sky130" refers to the process name or node technology, "fd" represents the foundry name (SkyWater foundry), "sc" denotes standard cell library files, and "hd" stands for high density, is one type of variant.
 
 # Design Preparation Step :

 in this lab we'll dive into the synthesis process for the specific design, picorv32a, utilizing the OpenLane flow. Our objective is to generate the netlist and other essential reports following the synthesis step. Before proceeding, it's very important to ensure the smooth operation of the virtual machine environment of ubuntu or any other linux os. Once everything is confirmed to be functioning optimally, as installed required openlane packages into your terminal, we'll observe a terminal interface within the virtual machine environment, resembling the following: image 1

 ![flow_tcl_interactive](https://github.com/kirantime/DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING/assets/158084817/092814ef-bbb2-49d4-81cc-c1ad3be5901c)

  
  when we are entering in the OpenLANE, we are having to use ./flow.tcl because as a name says it is going to follow the flowing methods using the script. -Interactive switch In addition, for the step by step process, it will be implemented as follows. otherwise it will run complete flow as translate right from RTL to GDSII, if it does not have the ability of an -interactive switch. That means, OpenLANE is now open and we can also see that the prompt will change now.
