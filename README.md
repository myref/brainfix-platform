# brainfix-platform
The brainfix platform is the basis for a number of braingames.

I got inspired to create the platform when my daughter was recovering from a severe concussion at CognitiveFX in Provo, Utah. They do wonders there! But as we needed to fly out to the US for her to recover, we need something at home. The Brainfix platform is intended as a starting point for the recreation of some of the tools they used during recovery.

The platform is based upon ESP32, as it has wifi on-board and can be expanded using standard Arduino extensions and code.

The idea is to create a platform that generates useable measurements that cannot be traced to a person, but does allow for progress tracking. In order to do so, each build using the platform is equipped with an rfid reader, so that the user can easiy identify him/herself by holding de rfid tag over the sensor. This way the user only has to provide data once.

## Data generation
In order to measure progress and prevent the need for complicated hardware to store performances, the data must be pushed to a cloud server. In order to prevent that the data can be traced back to a person, personal identifying data is not stored. 

the data is sent in JSON format
