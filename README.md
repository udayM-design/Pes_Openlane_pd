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
</details>


<details>
<summary>DAY 3 :Design Library Cell</summary>
<br>

#### Inverter Layout using Magic
```
git clone https://github.com/nickson-jose/vsdstdcelldesign.git
/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign$ magic -T sky13A.tech sky130_inv.mag 
```
![day3_1](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/3ca5df5d-a2f2-4467-8722-c8c353057d57)
![day3_2](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/152829db-9b45-429d-9a79-f099779be2ea)

#### DRC Check
![Screenshot from 2023-09-16 21-37-22](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/bfc82e43-3ca1-4178-a2e5-9d4ad476194e)

#### Extracting PEX to SPICE with MAGIC
![Screenshot from 2023-09-16 21-39-52](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/c23cffc4-e40b-4185-b20d-1309b23cf6c8)
![Screenshot from 2023-09-16 21-41-28](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/0b800af2-fe8e-45ca-a67b-332003af9512)

#### Grid Size
![Screenshot from 2023-09-16 21-44-24](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/f28d6bae-7ad2-47e1-a978-79925720649b)

![Screenshot from 2023-09-16 21-44-38](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/2d8f1392-be1d-46a2-91e2-31beb2aed309)

#### Modified Spice netlist
![Screenshot from 2023-09-16 21-46-37](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/0026879d-8380-456d-a515-8e14fc45535d)
![Screenshot from 2023-09-16 21-47-25](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/f8724ea2-5567-4b6b-bdff-0f311fd3b379)
![Screenshot from 2023-09-16 21-47-51](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/f92fd164-047f-4f4a-9e6f-d43d123d5cd7)


```
The results obtained from the graph are :

    Rise Transition : 0.0395ns
    Fall transition : 0.0282ns
    Cell Rise delay : 0.03598ns
    Cell fall delay : 0.0483ns
```

</details>

