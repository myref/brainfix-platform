# brainfix-platform
The brainfix platform is the basis for a number of braingames.

I got inspired to create the platform when my daughter was recovering from a severe concussion at CognitiveFX in Provo, Utah. They do wonders there! But as we needed to fly out to the US for her to recover, we need something at home. The Brainfix platform is intended as a starting point for the recreation of some of the tools they used during recovery.

The platform is based upon ESP32, as it has wifi on-board and can be expanded using standard Arduino extensions and code.

The idea is to create a platform that generates useable measurements that cannot be traced to a person, but does allow for progress tracking and scientific analysis. In order to do so, each build using the platform is equipped with an RC522 rfid reader, so that the user can easiy identify him/herself by holding a rfid tag over the sensor. This way the user only has to provide data once.

The setup must not be technical or more complicated than enabling a smart lightbulb. So on first setup it uses [wifimanager](https://github.com/tzapu/WiFiManager) to create an openingpage to connect the system to the local wifi network. Once that is done, the system should present a simple web page to select the game and if needed alter parameters.

## Data generation
In order to measure progress and prevent the need for complicated hardware to store performances, the data must be pushed to a cloud server. In order to prevent that the data can be traced back to a person, personal identifying data is not stored. 

The data is sent in JSON format. The following fields should at least be in there:
```
{
device (uuid),
setup (uuid),
user (uuid),
game (uuid),
data []  
}
```
The device UUID must be entered in the code in order to identify on which device the measurement is taken. This allows to easily filter on device in case a device seems to provide inaccurate data. The default UUID c6214a0d-007a-4c7d-ba50-c37e2d95ba42 is entered in the code on github and filtered out on ingress to prevent people from using the default code and pollute the data. A unique UUID can be generated for example on [uuidgenerator](https://www.uuidgenerator.net/).

## Setups and Games
For the time being, the following setups are envisioned:

| Name             | Description                                                  | UUID                                 |
|------------------|--------------------------------------------------------------|--------------------------------------|
| Metronome        | A metronome that chimes at 54 BPM for neuromotoric exercises | eadc9731-deb3-4097-8e6d-bf47fe649d3a |
| Leaderboard      | A game for playing the Dynavision like games                 | a75b20da-01fa-4ac2-9686-ff8ab010a3d3 |
| Cognition        | A setup to measure card sorting accuracy combined with tasks | 24bcbba0-1c46-4673-9bc5-32416a5c91a2 |
