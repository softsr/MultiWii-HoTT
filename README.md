MultiWii Meets HoTT
==============
MultiWii is a flight control system created by [Alexinparis] mainly for MultiRotor systems.
This projects contains an extension for the current MultiWii 2.0 software to send in flight telemetry data, if 
HoTT v4 capable RxTx systems from [Graupner] are used. Licensed under [GPLv3].

How It Works
------------
Sensor data are continously gathered by the flight control software. Every 2 seconds selected sensor data (e.g. LiPo voltage) are packed into a format
that conforms to the HoTT protocol specifications and is beeing sent to the receiver via MCUs serial interface (RX0TX0 on non Mega2560 platforms, RX3TX3 on Mega2560).
Thereby the MCU acts as a HoTT capable sensor and emulates a General Electric Air Module. 

What's Needed
------------
1. HoTT v4 capable RxTx system
2. Enabled telemetry downlink channel on the receiver
3. RxTx signal cable from MCUs UART Pins to receiver input/output channel (on GR-12 it's channel 5). Be advised that the MCU
uses 5V TTL, whereas the HoTT receiver needs a 3,3V TTL (LLC is needed).
4. Update your MCU with this compiled project (please review config.h before uploading to match your settings).

Configuration
-------------
Config parameters can be found in config.h.

Available Telemetry Data
--------------
* VBAT
* Relative high over ground

Supported MCU Hardware
----------------------
Arduino ProMini, Uno, Mega2560

Supported Sensor
----------------
* freeIMU0.4.3
* BMP085
* MS561101BA

Limitations
-----------
* On MCU platforms that only have one UART, e.g. Arduino ProMini MultiWiiConf Tool can not be used when telemetry is activated.
* Increases cycle time up to 35ms every time when telemetry data are transmitted. 

[GPLv3]: https://github.com/obayer/MultiWii-HoTT/blob/master/LICENSE.txt
[Alexinparis]: http://www.multiwii.com/
[Graupner]: http://www.graupner.de/