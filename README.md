# Folder directory description

* HEA-computer
  * data-txt
    * GPU.txt
    * CPU.txt
    * Mainboard.txt
    * Memory.txt
    * SSD.txt
    * Case.txt
    * Radiator.txt
    * Power.txt
    * computer_assembly_scheme.txt
  * data-neo4j
    * computer.dump
* IDFR-fishingRod
  * fishingRod.dump



## HEA-computer

In household electric appliance (HEA),  taking computer as an example,  we built the knowledge graph based on the AIC model to support retrieval of computer assembly schemes and component replacement (**BOM modification**).



### data-txt

Based on the Python Scrap framework, obtain data on computer assembly schemes and components at JD, including GPU, CPU, Mainboard, Memory, SSD (including HDD), Case, Radiator and Power.  The obtained data is stored in the following files in a txt file format：

| file name                    | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| GPU.txt                      | Data of the graphics processing unit (GPU), a key component of the computer, including attributes such as video storage frequency, video storage type, and video storage capacity. |
| CPU.txt                      | Data of the central processing unit (CPU), a key component of the computer, including attributes such as interface, model, and matching motherboard. |
| Mainboard.txt                | Data of the Mainboard, a key components of the computer, including attributes such as matching main board, memory card slot, power interface, brand type. |
| Memory.txt                   | Data of the Memory, a Key computer components, including attributes such as DDR algebra, total capacity, memory frequency, and memory quantity. |
| SSD.txt                      | Data of the solid state disk (SSD), a key component of a computer, including attributes such as sequential read speed, flash type, cache, and sequential write. |
| Case.txt                     | Data of the Case, a key components of the computer, including attributes such as panel interface, box weight, and material. |
| Radiator.txt                 | Data of the Radiator, a key components of the computer, including attributes such as power interface, heat sink size,  and compatible interface. |
| Power.txt                    | Data of the Power, a key components of the computer, including attributes such as  model, rated power, power supply and product size. |
| computer_assembly_scheme.txt | Data containing computer assembly schemes                    |



### data-neo4j

Based on the industrial knowledge structure defined by the AIC model, combined with the above txt file, open source knowledge extraction tools and algorithms are used to form the knowledge graph in the computer field. The exported knowledge graph source file：

> computer.dump





## IDFR-fishingRod

In the fishing gear industry, taking fishing rod assembly as a scene, we implemented an interactive design of fishing rod (IDFR) system, which covers the possible errors in the design process of fishing rod，including  **outError**,  **overlapError**,  **adaptError**,  **typeWarn**.  Thereby achieving interactive customization verification of fishing rod (**BOM verification**). A  knowledge graph of fishing rod has been constructed. 

> fishingRod.dump



# Data usage instructions

1. Create a new folder in the appropriate location, using the database name as the file name

   ```linux
   mkdir databasename
   ```

2. Create a new temporary container and enter

   ```linux
   docker run --rm -it -v /neo4j_data:/data neo4j:latest /bin/bash
   ```

3. Import data： *computer.dump*  or  *fishingRod.dump*

   ```linxu
   neo4j-admin load --from=/data/computer.dump --database=databasename --force
   ```

4. Exit Container

   ```
   exit
   ```

5. Modifying the configuration file conf outside the container

   ```
   dbms.activate_database=databasename
   ```

6. Restart the previous container

   ```
   docker restart containerID
   ```

   
