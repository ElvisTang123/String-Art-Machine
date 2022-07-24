<!---
<img src="media/1.gif" alt="" width="200"/>
<img src="media/2.gif" alt="" width="200"/>
<img src="media/3.gif" alt="" width="200"/>
<img src="media/4.gif" alt="" width="200"/>

<img src="media/2.jpg" alt="" width="200"/>
<img src="media/3.jpg" alt="" width="200"/>
<img src="media/1.jpeg" alt="Cat_Original" width="200"/>
<img src="media/4.jpg" alt="Cat_String" width="200"/>
<img src="media/5.jpg" alt="" width="200"/>
<img src="media/6.jpg" alt="" width="200"/>
<img src="media/7.jpg" alt="" width="200"/>
<img src="media/8.jpg" alt="" width="200"/>
<img src="media/9.jpg" alt="" width="200"/>
<img src="media/10.jpg" alt="" width="200"/>





![](media/8.jpg)
![](media/9.jpg)
![](media/10.jpg)
-->


<p align="center">
  <img src="media/1.jpg" alt="" width="70%"/>
</p>

<div align="center">
  <h1>String Art Machine</h1>
  <p><strong>By:</strong> Ahkar Kyaw, Elvis Tang</p>
</div>

In this tutorial we will learn how to build a machine that can replicate an image using strings. We built this machine for our ME405 class. It is still a work in progress with many rooms for improvement but we are very pleased with how far it has come and we are excited to share the project with you. 

# Introduction
String art, often referred to as pin-and-thread art, is a form of art that weaves colored string, wool, wire, or yarn between hammered nails to make geometric patterns. String art is not new and its origins go all the way back to the 19th century. It started off as an educational tool to introduce mathematical ideas to children but came back in the late 1960s as a decorative craft in a form of books and kits. 

Inspired by the beauty and complexity of this art style, we decided that we want to build a machine that can replicate any image using lines and recreate it physically in a form of string art. This was a very challenging project and due to time constraint, we were unable to perfect it to our desired standard. However, it works and we are thrilled to share our project with you. Hopefully you will be inspired to recreate a project like this yourself. 


| ![](media/2.jpg) | ![](media/3.jpg)|
| ---------------- | --------------- |

# Table of Contents
* [Product Specification](#product-specification)
* [System Design](#system-design)
* [Demo](#full-run)
* [Conclusion](#conclusion)

# Product Specification
## Hardware Components
| **Components** | **vender**     | **Dimension** |
| :-----------:  | :-----------: | :-----------: |
| MDF board | [Amazon](https://www.amazon.com/dp/B07QWSTMWJ?ref_=cm_sw_r_cp_ud_dp_WGG48NSVNE196GH4DMZJ) | 14-in(L) x 11-in(W) x 0.25-in(T)|
| Nails | [Amazon](https://www.amazon.com/Projects-Antique-Repairing-Decorative-Accessories/dp/B082J2JXZD?tag=cf09c0-20&geniuslink=true&th=1) | 23mm(L) |
| String | [Amazon](https://www.amazon.com/dp/B07LC1YDVR?ref_=cm_sw_r_cp_ud_dp_Z0H458M8TY3VP6MC05YG) | 200m |
| 80/20 Aluminum Extrusion | [McMASTER-CARR](https://www.mcmaster.com/80//t-slotted-framing-rails/) | 20mm x 20mm |
| T8 Lead Screw Nut Set | [Amazon](https://www.amazon.com/dp/B07GV72326?ref_=cm_sw_r_cp_ud_dp_XBR2BX6C1A7YK6SPVKN0) | 200mm(L), 8mm(D) |


## Electronic Components
| **Components** | **Vender** | **Datasheet**  |
| :-----------:  | :-----------: | :----------- |
| NUCLEO (STM32L476RG) | [MOUSER](https://www.mouser.com/ProductDetail/STMicroelectronics/NUCLEO-L476RG?qs=PRtH0mD6DWbM6mRV5DKjBQ%3D%3D) | https://www.st.com/resource/en/datasheet/stm32l476rg.pdf |
| Shoe of Brian | [OSHPARK](https://oshpark.com/shared_projects/e6X6OnYK) |  http://wind.calpoly.edu/ME405/doc/shoe_info.html |
| Mini Hand Drill DC Motor | [Amazon](https://www.amazon.com/AUTOTOOLHOME-Electric-Drill-Motor-Drills/dp/B01LZYWFE4/ref=asc_df_B01LZYWFE4/?tag=hyprod-20&linkCode=df0&hvadid=309735728871&hvpos=&hvnetw=g&hvrand=12073945360090893366&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=1014232&hvtargid=pla-461591041401&psc=1)| https://www.sears.com/autotoolhome-mini-dc-12v-electric-hand-drill-motor/p-A098205228 |
| NEMA 17 Stepper Motor | [Amazon](https://www.amazon.com/dp/B07QV1ZVJR?tag=rpantiques-20&linkCode=ogi&th=1) | http://www.autoflexible.com/file_upload/product/attach/NEMA%2017.pdf |
| LCD 1602 (I2C port) | [Amazon](https://www.amazon.com/dp/B019K5X53O?ref_=cm_sw_r_cp_ud_dp_NDRGXARM7KG02A7N59Y2) | http://www.handsontec.com/dataspecs/module/I2C_1602_LCD.pdf |
| TMC4210 | [MOUSER](https://www.mouser.com/ProductDetail/Trinamic/TMC4210-I?qs=TiOZkKH1s2TH5TqjeGBn1g%3D%3D) | https://www.trinamic.com/fileadmin/assets/Products/ICs_Documents/TMC4210_Datasheet_Rev.1.06.pdf |
| TMC2208 | [Amazon](https://www.amazon.com/Printer-TMC2208-Screwdriver-Controller-Ramps1-4/dp/B082LSQWZF/ref=sr_1_3?keywords=tmc2208&qid=1654876252&sr=8-3) | https://www.trinamic.com/fileadmin/assets/Products/ICs_Documents/TMC220x_TMC2224_datasheet_Rev1.09.pdf |


## Manufacturing / Machining Tools
| **Tool** | Source Files |
| :-----------:  | :-----------:  |
| 3D Printer | [ME405_StringArt/CAD Files/3D Printing/](https://github.com/AhKyaw/ME405_StringArt/tree/main/CAD%20Files/3D%20Printing) |
| Laser Cutter | [ME405_StringArt/CAD Files/Laser Cutting/](https://github.com/AhKyaw/ME405_StringArt/tree/main/CAD%20Files/Laser%20Cutting)  |

# System Design
## Mechanical Design
To begin with, let’s take a look at the mechanical components of this machine. The overall frame of this machine is made entirely out of 80/20 aluminum extrusion. The machines moves using 3 stepper motors and a DC motor with a drill attached to the tip. These motors are then mounted onto the frame using custom 3D printed parts. CAD files for these 3D printed parts can be found under Manufacturing - 3D Printer Source files. 

For the drawing board, we used a laser cut MDF board. The DXF file for laser cutting can be found under Manufacturing - Laser Cutter Source files. Once the board is cut, we attached it onto the 3D printed braket #4 and the lazy susan, which will be attached to the machine's frame. For the art canvas we want it to be easily removeable so we mounted another similar MDF board onto this existing platform using the pre-cut alignmnet holes. 

The full CAD model for the assembly of the machine can be found in the CAD folder under our GitHub Repository. 

<div align="center">
  <img src="media/Hardware_Design.png" alt="Hardware_Design" width="600"/>
</div>

## System Operating Procedure
<p>The figure below shows how the string art machine works. First, we need to convert the image to string art and generate its pin sequence via the Python file StringArt_Gen.py on our computer. After the pin sequence is generated, we will transfer this data to the Nucleo STM32 board. And based on the finite state machine and pin sequence, the Nucleo board will communicate with the motor driver through the SPI protocol and further control the motor to perform desired actions.</p>
<div align="center">
  <img src="media/System Operating Procedure.png" alt="Hardware_Design" width="1000"/>
</div>

## Software Design
### String Art Generator
Our current StringArt_Gen.py file is heavily based on this github repository: [kaspermeerts/stringart.py](https://gist.github.com/kaspermeerts/781f0137b361b51224dcab722ae387b4), and also the knowledge in this paper: [String Art: Towards Computational Fabrication of String Images](https://www.dmg.tuwien.ac.at/geom/ig/publications/stringart/stringart.pdf).
<p>The two figures below show the image before and after string art conversion. And before we input the image into the string art generator, we need to crop the image into square shape to make the program run normally.</p>


| ![](media/1.jpeg) | ![](media/4.jpg) |
| :-----------------: |:----------------:|
| Original Image         | String Art        |

## Firmware Design
### Finite State Machine

<div align="center">
  <img src="media/Finite_State_Machine.png" alt="Hardware_Design" width="600"/>
</div>

There are a total of three states in this project. The first state is the wait state, in this state the system will initiate the motor setup and wait until the button is pressed. After pressing the button, the system enters the drilling state.</br>

In the drilling state, there are three subroutines, the board rotates to the desired pin, the drill stepper motor rolls the DC drilling motor down to drill holes in the board, and lifts the DC motor up after drilling to the desired depth. The system will loop through these subroutines until there are holes in all desired nail locations. Because we need to put the nails into the holes manually, the system will stay inside the drilling state till we finish inserting nails onto the board and press the button.</br> 

While finishing inserting the nails and pushing the button, the system will enter the looping state. There are four subroutines in the looping state, first, the board will rotate to the degree of desired nails + theta (theta is half of the degree difference between the two nails), and the needle will move outside the edge of the circle that constructs by the nails. After the needle moves outside the circle, the board will rotate to the degree of desired nails - theta. And the needle will move back inside the circle. These are the four subroutines that the system keeps looping through till the maximum number of lines is achieved.</br> 

| ![](media/Drill_FSM.png) | ![](media/Loop_FSM.png) |
| :-----------------: |:----------------:|
|     Drilling State     | Loop State        |

## Motor Control

We use TMC4210 and TMC2208 as our motion controller and motor driver. STM32 will communicate with the TMC4210 through the SPI protocols, and TMC4210 will generate respective steps and direction signals to TMC2208. After the TMC2208 receives those two signals, it will send the respective power to the motor and the motor will do the desired action.

<div align="center">
  <img src="media/Motor Control.png" alt="Hardware_Design" width="1000"/>
</div>

# Results Demonstration
Here you will see our machine in action. There are 3 main stages to making a string art on this machine. First stage involves drilling holes for the nails to be slotted in and we call it the drilling stage. The second stage is where you manually put nails into these holes and attaching the string onto one of the nail. We call this stage a nailing stage. Last but not least, we have the looping stage where the needle move around and spin the board to loop the strings around the nails.

## Drilling
What you see below is a short timelapse of the machine drilling a hole and spinning the board around one step at a time. 

![](media/1.gif)

## Nailing
This is a very simple and manual stage where you manually put nails into each holes that the machine just drilled. Ideally, the holes will be deep enough such that they will be strong and stable to withstand the tension created by the string. However, we bought a quarter inch MDF board for our project and it turns out, quarter inch was insufficient to withstand the load so we had to go an extra step and used some hot-glue to make the base contact a little stronger. After all the nails are slotted in, tie the end of the string onto one of the nail and position this nail directly under the needle. Ideally, we want to use limit switches so that the alignment process is automated. For now, we manually aligned the first nail with the needle tip. 

## Looping
### Without Interference
The gif you see below is a short timelapse of the machine looping the string around the nails without any human interference. It is pretty successful for the most part but as you can see, on the sixth loop, the nail was a little shorter than the designed height so the string slipped out, forcing us to restart the machine. 

![](media/2.gif)

### Mechanism
| This is a close up, real-time video showing how the needle and the strings are attached such that it can loop around the nail without getting tangled up.  | ![](media/3.gif) | 
| :---------------- |:----------------|

# Challenges
Due to our lack of experience developing mechanical systems and budget constraint, most of the problems for the project arises in the mechanical side of the design. Since this is the first time developing such complex mechanical system for both of us, we spent too much time getting things right in the designing stage. We designed many of the parts from bottom up and that cost us a lot of time. By the time we finished a prototype to test with the program, we only have two weeks left. Therefore, we did not have much time to buy new parts and redesign the system to fix the problems. Ideally, we should have focused on getting the mechanical design ready using off the shelf components as early as possible so that we get more time to perfect the design. 

### Inconsistent Nail Height:<br>

| ![](media/5.jpg) | The first problem we encountered was the height inconsistency among the nails that we purchased. Even though we managed to drill all the holes to be exactly the same depth, the point of contact between each nail and the looping needle is different. Therefore, the string occasionally slip over the top if the nail is too short compared to others. To fix this problem, you need an alternative string feeding mechanism where the string is fed directly from the top instead of the side like what we have. This way, you the needle can loop the strings along a much lower plane without having to worry about the string getting tangled up. |
| ----------------- |:----------------|


### String Getting Tangled Up:<br>
| ![](media/6.jpg) | The second problem we encountered was with regards to the string getting tangled up after looping around the nail. There are two main reasons for why this happen. First is due to the lack of tension and retraction system for the string. This causes the string to droop down after the needle pulls the string to loop around the nail everytime. When the board rotates after, the loose part causes the strings to get tangled up. To fix this problem, you could modify the string feeding system so that it goes through several pulley to maintain the tension in the string. You could also add a retraction system to the spool of string so that it will prevent the string from drooping down after pulling it too far. The second reason is due to the nails not being slanted enough. We knew all along that if all the strings loop around along the same height, it will cause them to crash with each other causing the stings to get tangled up when rotating the board. Therefore, we tiltted the drill bit to be at a 5 degrees angle from the vertical, hoping that the slope will cause the strings to slide down the nail after each loop. However, the slope was not steep enough, causing the strings to get tangled up. For future development, the drill should be angled at least 10 degrees from the vertical. |
| ----------------- |:----------------|

### Insufficient Nail Depth:<br>
| ![](media/7.jpg) | The third problem we encountered was with regards to the having insufficient nail depth. We bought a quarter inch MDF board thinking it was sufficient depth for the nails. However, quarter inch was too shallow and the nails were not pinned deep enough so when the tension in the string gets high, the torque causes the nails to get ejected from the hole. Therefore for this project, we used some hot-glue to pin it to the base. A permanent solution to this problem would be to use at least a half inch MDF board. |
| ----------------- |:----------------|

# Full Run (With Intervention)
In the end, we managed to do a full run on the machine with a little bit of human intervention. We slowed the speed of string looping so that there is sufficient time for us to make sure the string is looped correctly. Most of the time, we used a small tweezers to push the string down on the nail so that they do not end up interfering with one another. Occasionally, we have to manually loop the strings onto the nail. This was the result of some nails being not long enough to reach the design height as mentioned previously. 

<div align="center">
  <img src="media/4.gif" alt="Machine in Action (with intervention)" width="800"/>
</div>

# Conclusion
Overall, it was a very fun project and we learned a lot from this experience. The machine still has many rooms for improvement and we are planning to continue working on it even after the class ends. We hope you like the project and hopefully it inspired you to build one of your own. 
