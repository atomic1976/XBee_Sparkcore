Using Spark Core and XBee for RF Communication, Part #1
----------------------------------------------

Here is one of the project I worked these days, this is a part one that uses Spark Core and XBee for RF Communication. My intention is to use XBee(s) and Spark Core to create very simple Home Automation project. In this part, I just turn on/off a remote LED which can be controlled using a Web Application. 

The project is to control a remote light, i.e. turn on/off the light. In this part I am using Spark Core and two XBee's (either Series 1 or Series 2). If you are using Series 1, then one should be configured to accept API Command, other can be wither API or AT mode. If you are using Series 2, then one should be configured as coordinator API and other can either be a Router AT/API or an End Device. 

**Introduction**

Here in this project the Coordinator API XBee is connected to Spark Core and communicate using Serial. Spark Core is used as Internet Gateway to control XBee. The Core application uses XBee Library ported by @pkourany.  For this project I am using XBee Remote AT command to control remote XBee(s). For more about API Mode and Remote AT Commands please refer to [this link](http://www.digi.com/support/kbase/kbaseresultdetl?id=2184).

The Router XBee's D0, D1, D2 and D3 pin are connected to four LEDs which can be remotely turn on/off. Any device can be connected to any pins and send the Remote AT commands to the remote XBee. It can a Rely connected to Electrical Light, or anything else.

To send Remote AT Command, you can either use a Broadcast address or a destination 64-bit (MAC/EUI64) address of the XBee module. Using the 64-bit destination address allows us to send commands to a particular XBee. There is also a 16-bit configurable address which can be used to group multiple XBees and send commands to that group. Since this is a different topic and is not in our scope, for more information refer to the [Digi documentation](http://www.digi.com/support/kbase/kbaseresultdetl?id=2187).

The sample JavaScript Web application is used to control the remote light. To use this application you should replace the *deviceid* and *accesstoken* with actual values. When the application is opened you will be asked to enter the Name (any name, just for display purpose) and the 64-bit remote address of the XBee that is connected to the Relay Module. Once it is entered you can turn on/off the D0, D1, D2 and D3 pins.

[Here](http://ftp1.digi.com/support/utilities/digi_apiframes2.htm) you can find a very useful API Frame Generator from Digi International. This is extremely useful for the development and debugging, I used it a lot for this project.

**Wiring**

*Coordinator XBee and Spark Core*

 - XBee Vcc to Spark Core 3V3 
 - XBee GND to Spark Core GND 
 - XBee DOUT to Spark Core Rx 
 - XBee DIN to Spark Core Tx

*Router XBee and Relay Module*

 - XBee Vcc to 3v3
 - XBee GND to GND
 - XBee DIO0 to LED1
 - XBee DIO1 to LED2
 - XBee DIO2 to LED3
 - XBee DIO3 to LED3

**Screenshots**
![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/1.JPG)

![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/2.JPG)

![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/3.JPG)

![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/4.JPG)

![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/webapp-1.png)

![enter image description here](https://raw.githubusercontent.com/krvarma/XBee_SparkCore/master/Screenshots/webapp-2.png)

**Demo Video**	

https://www.youtube.com/watch?v=n_4AgTekWqs