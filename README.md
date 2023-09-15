# Pes_Openlane_pd
<details>
<summary>DAY 1:Inception of opensource-EDA, Opennlane and Skywater130</summary>
<br>
	
[](https://github.com/udayM-design/Pes_Openlane_pd)
#### Skywater-130 PDK

![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/828dc501-b87a-4439-9fa1-ac94fd662d6b)
#### Invoking OpenLane
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/f3c211f1-4b0f-4774-ba75-e65627cabf3b)
```                        
flow.tcl is the file that contains the script to run the designs
```
#### Designs presnt in openalne and Heirarchy in a Design
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/994104a5-2bed-45e4-9d16-4a2058a484d6)
```
Src folder - Contains verilog files and sdc constraint files
Config.tcl files - Design specific configuration switches used by OpenLANE
```
#### Config file example content
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/1db112a3-658d-4c7d-80f9-8b7e1e3c251b)
### Prepare the design for the flow
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/bb81518c-69a6-478f-948c-62deeda86b34)
#### Synthesis
```
run_synthesis
```
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/0d19e7b4-4010-4bb4-8a54-a7ba66ddc7dc)
</details>

<details>
<summary>DAY 2 : Good Floorplan vs Bad Floorplan and Introduction to library cells</summary>
<br>

#### Floorplan

```
run_floorplan
```
![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/30104183-7a5f-4283-9444-a341d498ae66)

Changes made in the config.tcl for floorplan purpose:

![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/6e49ff78-1172-4c66-b2a2-81906c946da7)

Now in openlane, enter run_floorplan and the results will be updated at the runs folder

![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/654df32b-fbcf-44c5-b46e-8287262dae73)

```
 magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/38d2ab84-c009-45ad-924b-2f54dddba8eb)

```
run_placement
```

![image](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/63f6e5e4-0bd8-407b-9c10-25fabf38b0a3)




