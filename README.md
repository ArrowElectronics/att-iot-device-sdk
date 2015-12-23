# att-iot-device-sdk

Welcome to the AT&T IoT Device SDK.
This guide covers the simple steps to connect your DragonBoard410c to the AT&T m2x IoT Service using the AT&T M2X library.

The AT&T M2X library aims to provide a simple wrapper to interact with the AT&T M2X API for C using the MQTT protocol. It provides all the needed operations and methods to connect your devices to AT&T's M2X service.

**Note:** While this guide focuses on the installation of the c-client library, AT&T offers the library in many other languages as well.

# 1. Create an M2X Account
Signup for an M2X Account [here](https://m2x.att.com/)
* Once logged in, select devices and press the create-new button. Create a new device.
In the form fill out all the requested information:

**DeviceName:** In order to identify your device amongst many other devices you can specify a unique DeviceID or even add additional device meta-data.

**Stream:** For now just setup a example stream called “temperature”. Then click got to device. This


* Open your account settings and obtain your Master Key from the Master Keys tab. Note the Master key as you will need it at a later step.

# 2. Install the M2X library on the device
With the account setup complete we can now turn to the device.
The following steps require you to type a few commands in a terminal window on the device.
So lets start a terminal window:
* Download the M2X library onto the device:
```sh
mkdir ~/m2x
cd ~/m2x
git clone https://github.com/attm2x/m2x-c-mqtt
cd m2x-c-mqtt
git submodule update --init
```
* Install dependencies:
```sh
sudo apt-get update
sudo apt-get install libcurl4-openssl-dev
```
* Build the library and examples:
```sh
make
make examples
```

# 3. Use the m2x library to connect to the m2x-IoT-Service
Congratulations! Now that the library is installed on the device you can start calling its API-functions to connect to the m2x IoT service.

To see the library in action let’s checkout one of the many examples that ship with the library:
* Edit the list_devices example with your favorite editor:
```sh
cd examples
leafpad list_devices.c
```
Edit the M2X_KEY variable with your unique Master-key:
```sh
const char *M2X_KEY=” your Master-key here ”
```
* Recompile the example:
```sh
make 
```

* Execute the example:
```sh
./list_devices
```
* You should see the following output:
```sh
Response code: 200
Feed ID	: <your feed ID>
Name	: <your device name(s)>
```


For the full API documentation please refer to: https://m2x.att.com/developer/documentation/overview

For further information and additional examples please see the Arrow GitHub repository for AT&T M2X:
https://github.com/ArrowElectronics/att-iot-device-sdk
