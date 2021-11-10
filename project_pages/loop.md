## UMDLoop
<img src="../images/loop.png?raw=true"/>
**Project description:** UMDLoop is an undergraduate engineering team that has previously competed in SpaceX's Hyperloop Competition, placing in the top 5 in the world. This year, we participated in The Boring Company's Tunnel Boring Competition - aimed at developing tunnel boring machine technology to be faster than current industry standards. The UMDLoop team was selected as one of twelve international teams to build our design out of over 400 applicants. At the competition, we were granted the Safety Award and were one of the top 4 teams.

### 1. Embedded Systems Development

Our system utilizes a distributed system of STM32 microcontrollers for control over our tunnel boring machine. Communication is done via CAN Bus, ethernet, and a COSMOS-based command and control platform. I worked on validating our distributed system design by conducting tests using CAN Bus communication between subsets of our nine microcontroller system and verifying functionality. For safety reasons, keep-alive messages were transmitted between microcontrollers at a rate of 10Hz and controls were implemented to emergency shutdown the system if keep-alives were missing.
<img src="../images/uc.png?raw=true"/>

### 2. Low-Voltage Peripherals
I spent extensive time defining system requirements and evaluating peripherals. I worked with our other core teams (propulsion, navigation, etc.) to identify necessary sensors and determined power consumption and constraints with regards to our system. I also engaged in testing these various sensors from a laser time-of-flight sensor (using RS-422) to analog combined pressure-temperature sensors. As part of this testing, I created wiring harnesses as well as worked to test software programs.
<img src="../images/sensor.png?raw=true"/>

### 3. CAD, Electrical Mounting, 3D Printing, Custom Laser Target
In order to mount our custom-PCBs, I designed lightweight yet strong mounts to be 3D-printed. These 3D-printed mounts also provided good electrical insulation for the sensitive components which were to be mounted on steel plates. I created the models for these using Siemens NX and printed them using PETG. I also accounted for wire strain prevention and wire harnesses in my design. I also designed a custom laser target which consisted of a 3D archimedes spiral mounted to a stepper motor on the back of the machine. Using the time-of-flight laser sensor readings, this innovative design allowed us to determine our deviation away from our centerline without using any other sensors.
<img src="../images/mount.png?raw=true"/>

More Info: 
https://www.umdloop.com/
https://dbknews.com/2021/03/07/umd-loop-engineering-competition-tunnel-boring-machine/
