# FaceDoorLock

This repository is the conclusion of my project, which I created an Embedded facial access system with a 3d printed lock, that could be notified and configured via a Telegram/messenger BOT


## Overview 

Our system will work as shown in the image below:

![Image of the system](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/overview.png)

In front of our barrier, the camera collects the image of the car and send it wirelessly our Node Red server where we trait the image and detect the plate, then we extract the numbers and compare it to our DB -Data Base-, this to send the order to open or close the barrier.

## Parts of This project 

this project is diveded into 5 parts : 

1. [The Prototype](https://github.com/RinmoDo/FaceDoorLock#1-the-prototype)
2. [The online version ](https://github.com/RinmoDo/FaceDoorLock#2-the-online-version)
3. [The Embedded version ](https://github.com/RinmoDo/FaceDoorLock#3-The-Embedded-version )
4. [Using Material](https://github.com/RinmoDo/FaceDoorLock#4-Using-Material)
5. [Conception of the barriere](https://github.com/RinmoDo/FaceDoorLock#5-Conception-of-the-barriere)

*** 

### 1. The Prototype 
    
   In This prototype I used an ESP32-CAM to collect images and then send it via MQTT to the Node Red server, where I used my script to analyze and treat the image then resize it in a way we can only see the car plate, then we move to the next part where we use an OCR (optical character recognition) - based on an KNN algorithm method - to extract the characters, and compared the text with our data base on node red to send back the order to the ESP32-CAM to Open the Barrier in case we found the plate, else it stay closed.
   
   what we used : 
   
    * ESP32 CAM 
    * MQTT protocol
    * NODE RED 
    * Plate detection (a created python module 82% accuracy)
    * OCR (TensorFlow script google version)
    * A Servo-Motor (to simulate the barriere)
    * A car toys with a ticket as plate
   
  Desc. | Image 
------------ | -------------
The Esp32 camera that detects the car plate | ![ESP32 CAM](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/esp32CAM.png) 
Simulation of a barrier with a Servo Motor | ![barriere](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/barriere.png)
Car with a plate | ![Car](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/car.png)
As results | we found in the Node red dashboard :  Text `NU70REG `   
   
   ***
   
### 2. The online version 

We do the same as the prototype, but this time we gonna use some reliable materials:

* Using a commercial wireless camera with a good quality:

 ![CAMERA](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/alhuacam.png) 
 
Then we link it the server part via MQTT (& Mosquitto broker), and we process as we did before;   
We do a test by a picture of a car and we found these results:  
  
  Node Red | Dashboard
  ------------ | -------------
![TEST](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/testreasult.png) | ![TZST](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/testDashboard.png) 
 
 ***
 
### 3. The Embedded version 

   Instead of using too many parts (camera, server...), we try to use the whole system in just one card; We were able to use the ESP32 CAM with Micropython, that's allowed us to use too many options, we were able to do the car plate detection and also the OCR inside the ESP32CAM .
   
   After some tests we decided to group the parts and create the circuit and the pcd, as you can see below: 

  Circuit | Card
  ------------ | ------------- 
![circuit](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/circuit.png) | ![pcb](https://github.com/RinmoDo/FaceDoorLock/blob/main/images/pcb.png) 

**** BUT the system failed !!

Due to the low ressources of the esp32cam, we faced an overheated, an fps drop, low accuracy problems... 

So we back to the old system, the online version and keeping the esp32CAM installed on this tiny card.  
   

### 5. Conception of the barriere

-- Comming Soon --
