# Glowing ring
## Problem Statement
 To design a ring which glows when it is worn to the finger.
### Constraints:
* The ring should be as small as possible so that it can be worn to the finger comfortably.
* It should be powered with small source.
#### Components Required:
  * **LED**
  * **Two 1.5V coin batteries**--->These are the smallest batteries we can get. So we use these batteries to power the circuit.
  * **TTP223 Touch Pad** ---> It is really simple to use TTP223 touch pad, which is small in size(15mm x 11mm) and does not reqiure any microcontroller. Its range is upto 5V.The output pin is directly connected to led and other two pins are connected to battery.This touch pad is placed inner part of the ring and outer part is coated with non conducting material.So that when the person wears it the led glows.

# Control Systems for Reinforcement Learning - Hexapod
### Microcontroller:
  For this prject we use Arduino-Mega as microcontroller.
###### why MEGA and why not UNO.?
It simply doesn’t have enough SRAM memory to do all the calculations required for the inverse kinematics model to work. Most of these calculations are done with floating-point numbers. Each of these numbers will take 4 bytes of memory when it’s being used. That is 2 times as much as integer numbers. While it might not seem like much, UNO only has 2 kB of RAM, some of which will be taken by global variables. If we reserve 0.5 kB for all the globals and other local variables, we will be left with 1.5 kB of free memory, and it will only take 384 float numbers to waste all that. 384 might seem like a lot, but it is not enough for the amount of data the IK model will produce (read the “The Algorithm” section below to find out why), so we have to get more memory somehow.
The easiest way to achieve this is to change the UNO to MEGA. MEGA and UNO are compatible, so there will be no changes to the schematics. Plus, not only we will get four times more RAM for all the calculations, it will also mean eight times more flash memory to store our programs. We most likely won’t use all of that, but it is always nice to have a reserve space.
### Sensor:
* For this, there are servo motors which help in the movement of the hexapod. The movement of the hexapod is sensed by IMU sensors, 3 on * We use MPU6050 as the IMU sensor.
* The MPU6050 is interfaced with the microcontroller through the I2C protocol. But the problem with the set-up is that all MPU6050 have the same address of 0x68.
* For this purpose, the MPU6050 has a AD0 pin which allows the address to be changed when there are more than one MPU6050 used in a circuit. When AD1 is made high, the address of the MPU6050 becomes 0x69.
* Thus all MCU6050 pins have their AD0 pin at default HIGH. When a particular MCU6050 wants to communicate, its AD0 pin becomes LOW. Thus the microcontroller receives information from the device which has an address 0x68. This way, only one IMU sensor has the address 0x68 at a time.
### Pipeline:
Movement of the bot => Captured by IMU sensors => Processed by using Arduino and feeding it to AutoCAD software => The AutoCAD software now contains the orientation of the bot.
 

