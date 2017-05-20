---
title: Architecture
---
# System architecture

![](img/sys stru.jpg)

## 	Hardware architecture
### Computional nodes:
* **Smartphone**: 
    * Android phone (OS version>4.4) must held by the user while using the bike.
    * Function:Provide login and logout, exchange data with on bike Raspberry Pi by Bluetooth, provide GPS location and present bike information.
* **Raspberry Pi**:
	* Installed on the bike and connected with the Bluetooth module, all the sensor and the lock.
	* Function:  reason when to sound the siren, calculate the position (pitch, roll, yaw) from the accelerometer.
			Calculate the pollution level from the raw data from the gas concentration sensor.
			Control the motor of the lock and Bluetooth serial port.
	
### Devices:
#### Sensor system:
* **Accelerometer**:
	* Installed on the bike and connected with the on bike Raspberry Pi. 
	* Function: provide anti-thief function, and trigger the siren when bike is moved.
* **Gas concentration sensor**:
	* Installed on the bike and connected with the on bike Raspberry Pi.
	* Function: detect the concentration level of pollution gas.
#### Actuator system:
* **Bluetooth module**:
	* Installed on the bike and connected with the on bike Raspberry Pi.
	* Function: exchange data and command with the smart phone.
* **Smart lock**:
	* Composed of a common lock and a motor to drive the lock, Installed on the bike and connected with the on bike Raspberry Pi.
	* Function: lock the bike.
* **Siren**:
	* Installed on the bike and connected with the on bike Raspberry Pi.
	* Function: make some noise to get attention.
#### Supporting system
* **Bike**
	* Normal city bike.
	* Function: holder for the Pi and all the sensor.
* **Battery**
	* Power bank installed on the bike 
	* Function: power the on bike circuit.
### User interface
   The smart phone works both as a computational node but also as an user interface.

## Software architecture

### Mobile Application
* Running on the android smart phone.
* **With user**:
    * provide login and logout interface,
    * showing the location of the bikes,
    * getting commands for locking and unlocking the bike.
* **With the web server**:
    * checking the database for the logged user,
    * storing the credential of the user.
    * Upload and download the location of the bike.
* **With the google map service**:
	* Sending GPS coordinates of bike or user.
	* Get map of the current location.

### Database
* Running on the remote computer.
* Store and retrieve the bike location username and password on the cloud.
* Using standard database API.

### Google map service
* Running on cloud.
* Return map of the location sent, including image pins on the location of the bike

### Position and Pollution level calculation on the raspberry Pi
*	Calculate the position (pitch, roll, yaw) from the accelerometer.
*	Calculate the concentration of gas from the gas sensor.

### Selected components
####Off the shelf
|Product name| Description | Price| 
|------------|:------|:------|
|Arduino Uno Rev3| microcontroller board based on the ATmega328P | €20.00|
|HC05 Bluetooth module| serial transfer, able to work as master or slave device |€ 4.07|
|Adafruit 10-DOF IMU Breakout | LSM303 accelerometer | $29.95|
|ULN2003APG driver board with BJY48 stepper motor | 4 phase stepper motor for the smart lock | €5.80|
|Mq9 pollution sensor |  high sensitivity and fast response gas sensor | €11.60|
|Android phone | OS version greater than 4.4.| no need to buy|

### Software Components
* The libraries for the Bluetooth module, the Adafruit 10-DOF IMU breakout, and the stepper moter is provided by the hardware manufacture company. And they are compiled in the Arduino software.
* The Android App Grab-a-bike uses standard andriod software developing library, and is developed using Andriod studio (version 2). 
* The google map service is used in the smart phone, for detiails check (https://developers.google.com/maps/documentation/android-api/)


