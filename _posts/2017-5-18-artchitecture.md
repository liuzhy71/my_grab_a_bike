---
title: Architecture
---
# System architecture

The complete system includs on bike sub-system, user smart phone, database running on the remote server.
* The on bike system includes sensors sensing pollution data and bike posture data. And the on bike processor controls 
    the anti-thief function, pollution warning function. And the pollution data is sent to the smart phone.
* The smart phone receives the pollution data and sends the data together with the location data to the 
  remote server where the database is running.
* The server receives and stores the location and pollution data, and provides them to the mobile phone
  when the data is needed for user login and bike seeking.

![](img/sys stru.jpg)

## 	Hardware architecture
### Computional nodes:
* **Smartphone**: 
    * Android phone (OS version>4.4) must held by the user while using the bike.
    * Function:Provide login and logout, exchange data with on bike processor by Bluetooth, provide GPS location and present bike information.
* **On bike processor**:
	* Installed on the bike and connected with the Bluetooth module, all the sensor and the lock.
	* Function:  reason when to sound the siren, calculate the position (pitch, roll, yaw) from the accelerometer.
			Calculate the pollution level from the raw data from the gas concentration sensor.
			Control the motor of the lock and Bluetooth serial port.
* **Web server**
    * Running remotely, providing database of user information bike information 
    and pollution information

### Devices:
#### Sensor system:
* **Accelerometer**:
	* Installed on the bike and connected with the on bike processor. 
	* Function: provide anti-thief function, give information to the processor about the current posture of the bike.
* **Gas concentration sensor**:
	* Installed on the bike and connected with the on bike processor.
	* Function: detect the concentration level of pollution gas.
	
#### Actuator system:
* **Smart lock**:
	* Composed of a common lock and a motor to drive the lock, Installed on the bike and connected with the on bike Arduino.
	* Function: lock the bike.

#### Supporting system
* **Bluetooth module**:
	* Installed on the bike and connected with the on bike processor.
	* Function: exchange data and command with the smart phone.
* **Bike**
	* Normal city bike.
	* Function: holder for the on bike processor and all the sensor.
* **Battery**
	* Power bank installed on the bike 
	* Function: power the on bike circuit.
	
### User interface
* **Siren**:
	* Installed on the bike and connected with the on bike processor.
	* Function: Give a warning when the bike is being moved when it is locked.
* **LEDs**:
    * Installed on the handle of the bike and connected with the on bike processor.
    * Function: Give warnings when the polution in the air is too high.
* **Smart Phone**:
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
* Running on the web server.
* Store and retrieve the bike location username and password on the cloud.
* Using standard database API.

### Google map service
* Running on cloud.
* Return map of the location sent, including image pins on the location of the bike

### Position and Pollution level calculation by on bike processor
*	Calculate the position (pitch, roll, yaw) from the accelerometer.
*	Calculate the concentration of gas from the gas sensor.

### Selected components

#### Off the shelf

* **These is the components available in the market chosen for the project**

|Product name| Description | Price| 
|------------|:------|:------|
|Arduino Uno Rev3| microcontroller board based on the ATmega328P | €20.00|
|HC05 Bluetooth module| serial transfer, able to work as master or slave device |€ 4.07|
|Adafruit 10-DOF IMU Breakout | LSM303 accelerometer | $29.95|
|ULN2003APG driver board with BJY48 stepper motor | 4 phase stepper motor for the smart lock | €5.80|
|Mq9 pollution sensor |  high sensitivity and fast response gas sensor | €11.60|
|Android phone | OS version greater than 4.4.| no need to buy|

And cheaper solution can be found.

### Software Components

IDE used:
* _Arduino_
* _Android Studio 2_

Libraries:
* For the _Bluetooth module_, check [here!]()
* For _Adafruit 10-DOF IMU breakout_, check [here!]()
* For the stepper moter check [here!]()
* The Android App _Grab-a-bike_ uses andriod software developing library for Android 4.4. 
* The google map service is used in the smart phone, for detiails check [Google Map API](https://developers.google.com/maps/documentation/android-api/)


