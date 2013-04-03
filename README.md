# Hardware tutorial

An Arduino tutorial for connecting to the internet

##What you'll need
* [A WiFly Module](https://www.sparkfun.com/products/10822) ($35)
* [An Arduino](https://www.sparkfun.com/products/11021) ($30)
* A soldering iron & some solder

##Setting up the Arduino

Make sure you have the Arduino Software installed: http://arduino.cc/en/main/software

Open up the Arduino IDE. Make sure your Arduino works by going to File -> Examples -> Basic -> Blink. Upload the code to your Arduino by selecting the correct usb port on Tools->Serial Port and select the correct arduino board from Tools->board. Upload your the blink code by clicking on the upload button. 

This will make a light on your Arduino blink and is a super basic test of whether everything is working. 

##Setting up the WiFly

We're using a WiFly module for internet connectivity. If you buy the one from sparkfun you'll notice that it isn't an Arduino shield, so you'll have to solder some wires to right pins in order to connect it to an Arduino.

###Soldering the WiFly

There are 4 pins that you need to connect from the WiFly module to the Arduino: Vcc, GND, TX, and RX.

These 4 pins correspond to the following on the WiFly module

![WiFly](https://raw.github.com/lifegraph/hw-tutorial/master/imgs/wifly.png)

* Pin 1 &mdash; Vcc. Connect this to the **3.3v pin** on the Arduino.
* Pin 2 &mdash; TX. Digital pin 9 on the Arduino.
* Pin 3 &mdash; RX. Digital pin 10 on the Arduino.
* Pin 10 &mdash; Connect this to GND.

![WiFly all wired up](http://i.imgur.com/EDxmchO.png)

## Connecting to the internet with WiFlyHQ

We'll be using [WiFlyHQ](https://github.com/harlequin-tech/WiFlyHQ) as our library for interfacing with the WiFly module. This allows us to talk to the WiFly over serial.

In order to setup WiFlyHQ, you'll need to download it to your Arduino libaries. On OSX this is typically in `~/Documents/Arduino/libaries/`. If you don't have a library folder, you'll need to make one. 

If you use git you can download the library with the following

```
cd ~/Documents/Arduino/libraries;
git clone https://github.com/harlequin-tech/WiFlyHQ;
```

If not, you can [download the WiFlyHQ as a zip file](https://github.com/harlequin-tech/WiFlyHQ/archive/master.zip). You'll need to rename this folder "WiFlyHQ" and place it in the Arduino /libraries folder or else the Arduino IDE can't find it. 

After you add the library, you'll need to restart the Arduino IDE for it to pick up the library. If you've added it in the right place, you should be able to see the WiFlyHQ library if you go to Sketch -> Import Library.

After you have the library working, you'll need to open up the [helloworld example in this repo](https://raw.github.com/lifegraph/hw-tutorial/master/helloworld/helloworld.ino) and open it up with the Arduino IDE. 

In `helloworld.ino`, you'll need to change the SSID (name of your network) and the password to work with your own WiFi network:

```ino
const char mySSID[] = "your_ssid";
const char myPassword[] = "your_password";
```

## Making HTTP Requests

After you've modified `helloworld.ino` and saved it, you'll need to load the code to the Arduino through the Arduino IDE. Once the code is loaded on to the Arduino, you can go to Tools->Serial Monitor to bring up the serial output of the Arduino. You should see it connect to your wifi network.

It should try to grab the www.lifegraphlabs.com/hello_world site and print out the message "hello world"

##Further examples

* [GraphButton](https://github.com/lifegraph/graphbutton-wifly) - press the button and have it post a message to your Facebook
* [Notification light](https://github.com/lifegraph/notificationlight) - a light that lights up when you have a new facebook notification
