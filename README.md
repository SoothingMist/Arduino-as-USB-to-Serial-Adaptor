# USING ARGUINO UNO R3 AS A PROGRAM EXECUTION MONITOR
Have often wished it were possible to monitor program execution when the serial port is exchanging data with another device. An LCD display could be used for that but those are somewhat difficult to employ with the Arduino line, in my personal opinion. From what I can see: There are lots of jumper wires and soldering involved, in the examples I have seen, and there does not appear to be an LCD shield that plugs directly into Arduino devices. The little "display" embedded on the Arduino Uno R4 is cute but does not suffice for my purposes.

An alternative is to use an Arduino Uno R3 for monitoring the device in question. Doing so does require three jumper wires to be installed but purchasing, installing, and programming of some other device, like an LCD display, is not required. Also not required are any other parts, just the microcontroller boards themselves and three jumper wires. This is perfect if one has a spare Arduino Uno R3.

Found out about this innovative idea from these three videos:

  * https://www.youtube.com/watch?v=4cYJjqx-iUo

  * https://www.youtube.com/watch?v=qOztsbEfg1g

  * https://www.youtube.com/watch?v=jWoeuAKRCKI

You can watch those videos to get different perspectives. This posting is an effort to present an entire project that applies the innovation to an actual debugging problem.

Equipment required for basic demonstration:

  * 1 Arduino Uno R3
  * 1 Arduino Mega 2560
  * 3 Jumper Wires

Additional equipment required for advanced demonstration:

*  1 other Arduino microcontroller board (other board types may also be useful)
   This project used an Arduino MKR WAN 1310 due to the eventual need for LoRa broadcasting.

For Both Demonstrations

On the Arduino Uno R3: Connect the GND pin to the RESET pin.
Between the Mega and Uno: Connect the Mega TX1 pin to the Uno TX pin. Connect the Mega RX1 pin to the Uno RX pin.


# License
GNU Affero General Public License v3.0

Permissions of this strongest copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights. When a modified version is used to provide a service over a network, the complete source code of the modified version must be made available.

This is not legal advice. Learn more about repository licenses: https://docs.github.com/articles/licensing-a-repository/#disclaimer. Additional license information is here: https://github.com/SoothingMist/Remote-Soil-Moisture-Sensing/blob/main/LICENSE.
