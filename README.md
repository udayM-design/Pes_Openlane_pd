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

<details>
<summary>Day 4 - Pre-Layout timing analysis and importance of good clock tree</summary>
<br>

#### Extraction of LEF
```
The track.info file can be found within the following directory path: ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info
less track.info
```
![Screenshot from 2023-09-17 21-12-00](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/c5924e71-705e-4a46-bc4f-aa016a42492f)

####  Setting grid values using above file info
```
grid 0.46um 0.34um 0.23um 0.17um
```
![Screenshot from 2023-09-17 21-13-43](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/69ad4a51-cefa-467e-aac4-3659fe79a65d)

##### Layout view after setting grid info 
![Screenshot from 2023-09-17 21-14-52](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/ace8162b-8276-4d6e-9a9e-4cc38a6b6bc8)

### LEF Generation
```
save sky130_vsdinv.mag
```
![Screenshot from 2023-09-17 21-16-43](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/978a7939-d8f2-4adb-a786-b75411a9cfb5)
```
magic -T sky130A.tech sky130_vsdinv.mag &
```
![Screenshot from 2023-09-17 21-21-45](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/1fff814a-8c91-4f3c-b2ec-2503c45a41c7)

```
lef write
```
![Screenshot from 2023-09-17 21-22-52](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/3904bd70-f5fd-47e7-898c-01ca935aee28)

#### Plug the generated lef file into PICORV32a
```
vim sky130_vsdinv.lef
```
![Screenshot from 2023-09-17 21-24-27](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/10081422-2ea8-48dc-961d-c3425ec3bd1d)

```
cp sky130_vsdinv.lef /home/vsduser/Desktop/work/tools/openlane_working_dir/designs/picorv32a/src/
cp sky130_fd_sc_hd__* /home/vsduser/Desktop/work/tools/openlane_working_dir/designs/picorv32a/src/
config.tcl

```
#####  to invoke openlane.
```
cd Desktop/work/tools/openlane_working_dir/openlane/
docker
./flow.tcl -interactive
```
![Screenshot from 2023-09-17 21-28-24](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/a16b4c92-c679-44d4-8e1d-2b55ec2369e0)

##### Make sure the lef file is added
```
package require openlane 0.9
prep -design picorv32a -tag unique_timestamp -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
![Screenshot from 2023-09-17 21-29-43](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/a0fda4a9-6750-406b-9f2a-656f45fcc690)

![Screenshot from 2023-09-17 21-30-11](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/98c3b27a-85ab-4feb-9a09-0ffeb25527dc)
![Screenshot from 2023-09-17 21-30-38](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/818005cf-1389-4e85-bcc3-c2079d4ac334)

#### We need to run run_synthesis again
![Screenshot from 2023-09-17 21-32-13](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/c2f33386-170b-4a13-b635-bd18704a59b6)
![Screenshot from 2023-09-17 21-33-10](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/4da0f663-f7b2-4372-aa19-4bd8c5c94395)
![Screenshot from 2023-09-17 21-33-35](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/8b3a1276-5576-4b31-b8a9-e8846884175f)
##### Enable cell buffering & performing manual cell replacement on our WNS path with the OpenSTA tool
![Screenshot from 2023-09-17 21-34-22](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/9cc6613c-f533-4371-94d7-c0bfd146acd6)

#### Optimize the fanout value with OpenLANE tool
![Screenshot from 2023-09-17 21-35-43](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/35999aeb-9822-4ebd-b8c2-ccc163a8b5e6)

#### Post CTS- STA Analysis
```

    Launch OpenRoad.
    Load the LEF file from the "tmp" folder in your OpenLANE runs.
    Load the DEF file from the CTS results.
    Create and save the .db database file.
    Load the generated .db file.
    Read the CTS-generated Verilog file.
    Import both the minimum and maximum liberty files.
    Define clock domains.
    Generate timing reports to analyze the design further.
```
![Screenshot from 2023-09-17 21-37-28](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/19301d08-9fb9-474f-8c9c-fad0eeba1275)
![Screenshot from 2023-09-17 21-37-51](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/e3ba11b0-4f35-4922-8b6b-c8d9a61afd25)
![Screenshot from 2023-09-17 21-38-12](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/20f11e18-4d73-4080-8c0f-451110e30d26)
![Screenshot from 2023-09-17 21-39-20](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/5d366276-c692-4a79-8ee7-d34fa47aef29)
![Screenshot from 2023-09-17 21-39-44](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/bd5c52e7-f9b6-4552-9a7b-9d36dda60862)
![Screenshot from 2023-09-17 21-40-14](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/c77afc34-c442-4862-b4bf-da90f6feb657)
![Screenshot from 2023-09-17 21-40-56](https://github.com/udayM-design/Pes_Openlane_pd/assets/93391726/bca43d61-a3be-4dae-9ba8-4e0de9ace839)
</details>


