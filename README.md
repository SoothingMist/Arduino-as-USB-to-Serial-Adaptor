# USING ARDUINO UNO R3 AS A PROGRAM EXECUTION MONITOR
Have often wished it were possible to monitor program execution when the serial port is exchanging data with another device. An LCD display could be used for that but those are somewhat difficult to employ with the Arduino line, in my personal opinion. From what I can see: There are lots of jumper wires and soldering involved, in the examples I have seen, and there does not appear to be an LCD shield that plugs directly into Arduino devices. The little "display" embedded on the Arduino Uno R4 is cute but does not suffice for my purposes.

An alternative is to use an Arduino Uno R3 for monitoring the device in question. Doing so does require three jumper wires to be installed but purchasing, installing, and programming of some other device, like an LCD display, is not required. Also not required are any other parts, just the microcontroller boards themselves and three jumper wires. This is perfect if one has a spare Arduino Uno R3.

Found out about this innovative idea from these three videos:

  * https://www.youtube.com/watch?v=4cYJjqx-iUo

  * https://www.youtube.com/watch?v=qOztsbEfg1g

  * https://www.youtube.com/watch?v=jWoeuAKRCKI

You can watch those videos to get different perspectives. This posting is an effort to present an entire project that applies the innovation to an actual debugging problem.

<h2>Equipment required for basic demonstration</h2>

  * 1 Arduino Uno R3
  * 1 Arduino Mega 2560
  * 3 Jumper Wires

<h2>Additional equipment required for advanced demonstration</h2>

*  1 other Arduino microcontroller board (other board types may also be useful)
   This project used an Arduino MKR WAN 1310 due to the eventual need for LoRa broadcasting.

<h2>Basic Demonstration</h2>

Before you do any wiring, plug each of the two devices into different USB ports on your computer.

Load the following sketch into the Uno:
```
void setup()
{
  // As a Serial-to-USB converter,
  // the microcontroller board just contains a blank sketch.
}

void loop()
{
}
```
Load the following sketch into the Mega:
```
void setup()
{
  Serial.begin(9600); while(! Serial) delay(100);
  Serial1.begin(9600); while(! Serial1) delay(100);
  Serial.println("Setup Completed"); Serial.flush();
  Serial1.print("Setup Completed\n"); Serial1.flush();
}

void loop()
{
  static uint8_t counter = 0;
  Serial.println(counter);
  Serial1.print("New Number: "); Serial1.println(counter++); Serial1.flush();
  Serial1.flush();
  delay(1000);
}
```

On the Arduino Uno R3: Connect the GND pin to the RESET pin.
Between the Mega and Uno: Connect the Mega TX1 pin to the Uno TX pin. Connect the Mega RX1 pin to the Uno RX pin.

Open the Serial Monitor for both microcontrollers.

On Mega's monitor, you should see something like:

![image](https://github.com/user-attachments/assets/1df7d3f0-a040-4ab9-8463-6f88bcb50896)

On Uno's monitor, you should see something like:

![image](https://github.com/user-attachments/assets/e4929157-a7b2-47c1-94ff-3783d5d70b74)

<h2>Use with Alternative Devices</h2>

Found that the Mega can be replaced by an Arduino MKR WAN 1310.
On the MKR, use TX and RX instead of TX1 and RX1.
Everything else is the same.

<h2>Use in Debugging</h2>

A more advanced use of this idea is to help debug a process that sends/receives data between devices. In this demonstration, an Arduino MKR WAN 1310 instigates a data exchange with an Arduino Mega 2526. What is going on within the Mega is monitored by the Uno. A programmable USB hub facilitates the exchange as a way of showing how to send/receive data between devices that support interactive USB data flows but cannot be directly connected. In this case, the hub was a Windows 11 computer but the hub has also been shown to run on a Linux headless computer (Raspberry Pi v4). USB v2 or v3 work just as well.

The same connections between the Mega and Uno are employed but those have to be removed so that new code can be loaded. The same code runs on the Uno. All the devices plug into different USB ports on your computer. Here is a list of the appropriate codes:

  * ArduinoMKR_Instigator
  * ArduinoMega_Respondent
  * USB_HUB

Once all microcontrollers are ready, turn off the serial monitors for the MKR and Mega. Then start USB_HUB.

On your Python display, you should see:

![image](https://github.com/user-attachments/assets/94f0563b-5131-40f7-aa3d-3397f001980d)


On your Uno display, you should see:

![image](https://github.com/user-attachments/assets/cd53bd35-761a-477b-823e-74d9203fe1d5)


If you have comments or difficulties, please open an issue. Am always glad to receive those and will respond.

# License
GNU Affero General Public License v3.0

Permissions of this strongest copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights. When a modified version is used to provide a service over a network, the complete source code of the modified version must be made available.

This is not legal advice. Learn more about repository licenses: https://docs.github.com/articles/licensing-a-repository/#disclaimer. Additional license information is here: https://github.com/SoothingMist/Remote-Soil-Moisture-Sensing/blob/main/LICENSE.
