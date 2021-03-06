BeaconNetAir
============

This is the airborne half of the system used to monitor and manage an entire network of balloons - designed specifically to generate the BEACONNet tracking messages

The BEACONNet tracking message is defined as an NMEA0183-compatible proprietary message, currently defined as:
$PEDGE,[BalloonID],[GPSDate],[GPSTime],[GPSLat],[GPSLon],[GPSAlt],[GPSSpd],[GPSCourse],[GPSNumSats],[GPSHDOP],[A1],[A2],[A3],[A4],[A5],[CPM]*[CKSUM]
All GPS fields are taken from GPGGA and GPRMC sentences.  Onboard data (An) is defined as follows:
A1: Rail voltage (should be within a couple of bits of max)
A2: Temperature
A3: Pressure
A4: Humidity
A5: Battery voltage (scaled through a 1/4 voltage divider)
CPM: Radiation counts per minute - not yet implemented, will remain at 0

The goal of the BEACONNet message is to make it individually packetizable, so as to minimize network overhead and maximize the reliability of received sentences.  In order to achieve this, some padding and other magic may be necessary.  The sentence definition above will be updated with further info as it evolves.