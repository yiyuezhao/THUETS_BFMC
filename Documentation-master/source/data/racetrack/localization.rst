Localization system
===================

The localization system used in our location is made out of MDEK1001 `MDEK1001 <https://www.qorvo.com/products/p/MDEK1001>`_. devices,
which can be reproduced in the testing location of each team. A set of 12 boards can be found for ~300 dollars. 

Each device can be set either as Anchor, Tag or Gateway and can be configured accordingly with the help of the quorvo application by using BLE. 

Another characteristic of our system is that we get the data from the Tag directly via serial communication, not 
from the Gateway. Meaning, we have a device connected directly to the MDEK board that gets the data from it, then it shares it wirelessly 
with the TrafficCommunicationServer. The TrafficCommunicationServer then serves the location to the interested cars.

To best simulate the gathering of the data, we encourage you to build your project based on this info and take as
starting point the TrafficCommunicationServer, described in the Computer section.