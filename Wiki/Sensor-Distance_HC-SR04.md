##   Introduction

This HC-SR04 Ultrasonic Ranging Sensor is a non-contact distance measurement module with stable performance and high ranging accuracy, besides, the measure angle is 45°, For the advantage compared to the ultraviolent ranging sensor, the price of this module is surely to be expensive, in order to make the great use of the resource, we suggest you to use this sensor when the measurement range is up to 5 meter.

Look at the picture, there are two sensors, one is emit the ultrasonic and the other receive it when the ultrasonic is reflect by the obstacle, there are also two pins for emission and receiving the data from controller.

##   Features

Power supply: 5V DC

Effectual angle: <15°

Ranging distance: 2cm to 500 cm

Resolution: 1 cm

Ultrasonic Frequency: 40k Hz

Note: the size of the object is better to be more than 0.5 m2, the surface is as possible as smooth, or it will influence the accuracy of measure data.


##   usage

The principle of the HC-SR04: it transmits a short ultrasonic pulse, receive the signal which reflected by the object, and converts it into a electric signal.

Here’s the sequence chart:

 First, we transmit a trig signal which is high lever signal at least 10 μs to the HC-SR04, then it transmits 8 square waves at the frequency of 40 kHz in cycle, it will detect if there’s the return signal by itself, when the square waves reflected by the object, HC-SR04 transmit a high lever signal, the time of the high lever is proportional to the distance, therefore, it’s easy to get the distance by account the high lever’s time and then divide it by 58. 
 
How do I get this?

Here’s the program of how to measure the distance by use of HC-SR04 equation? First of all, the speed of the voice is normally 340 m/s, the unit of time we get is μs, and the unit of distance is cm, the time of high lever is cost from the square wave was transmit then reflected by the object to the wave has been received by the HC-SR04, so the distance is equal to time*340*100/1000000/2 as well as time/58, the unit of distance is cm. 

## code

[code]
#define ECHO 2

#define TRIG 3

void setup() {

  // put your setup code here, to run once:

pinMode(ECHO, INPUT);

pinMode(TRIG, OUTPUT);  

Serial.begin(9600);
}

void loop() {

/*
   * Here's the pulseIn function: Reads a pulse (either HIGH or LOW) on a pin. 
    For example, if value is HIGH, pulseIn() waits for the pin to go HIGH, 
    starts timing, then waits for the pin to go LOW and stops timing. Returns 
    the length of the pulse in microseconds. Gives up and returns 0 if no pulse 
    starts within a specified time out.
 
 */

// put your main code here, to run repeatedly:

digitalWrite(TRIG, LOW);   //give a low lever signal to the trig pin of HC-SR04

delayMicroseconds(2);      //delay 2μs

digitalWrite(TRIG, HIGH);  //write a high lever signal to the trig pin of HC-SR04

delayMicroseconds(10);     //delay 10μs

digitalWrite(TRIG, LOW);   //write a low lever signal to the trig pin of HC-SR04 

float Time=pulseIn(ECHO, HIGH);   //time the high lever signal's time, also means 

//  the time cost by double distance

float distance;            

distance= Time/58;         //calculate the distance

Serial.println(distance); //display the distance
}

[/code]

<font color="#5e6d03">#define</font> <font color="#000000">ECHO</font> <font color="#000000">2</font>
<font color="#5e6d03">#define</font> <font color="#000000">TRIG</font> <font color="#000000">3</font>
<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#434f54">&#47;&#47; put your setup code here, to run once:</font>
<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">ECHO</font><font color="#434f54">,</font> <font color="#00979c">INPUT</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">TRIG</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#95a5a6">&#47;*</font>
<font color="#95a5a6"> &nbsp;&nbsp;* Here&#39;s the pulseIn function: Reads a pulse (either HIGH or LOW) on a pin. </font>
<font color="#95a5a6"> &nbsp;&nbsp;&nbsp;For example, if value is HIGH, pulseIn() waits for the pin to go HIGH, </font>
<font color="#95a5a6"> &nbsp;&nbsp;&nbsp;starts timing, then waits for the pin to go LOW and stops timing. Returns </font>
<font color="#95a5a6"> &nbsp;&nbsp;&nbsp;the length of the pulse in microseconds. Gives up and returns 0 if no pulse </font>
<font color="#95a5a6"> &nbsp;&nbsp;&nbsp;starts within a specified time out.</font>
<font color="#95a5a6"> &nbsp;*&#47;</font>
 &nbsp;&nbsp;<font color="#434f54">&#47;&#47; put your main code here, to run repeatedly:</font>
<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">TRIG</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;give a low lever signal to the trig pin of HC-SR04</font>
<font color="#d35400">delayMicroseconds</font><font color="#000000">(</font><font color="#000000">2</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;delay 2μs</font>
<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">TRIG</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;<font color="#434f54">&#47;&#47;write a high lever signal to the trig pin of HC-SR04</font>
<font color="#d35400">delayMicroseconds</font><font color="#000000">(</font><font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;delay 10μs</font>
<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">TRIG</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;write a low lever signal to the trig pin of HC-SR04 </font>
<font color="#00979c">float</font> <font color="#000000">Time</font><font color="#434f54">=</font><font color="#d35400">pulseIn</font><font color="#000000">(</font><font color="#000000">ECHO</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font> &nbsp;&nbsp;<font color="#434f54">&#47;&#47;time the high lever signal&#39;s time, also means </font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47; &nbsp;the time cost by double distance</font>
<font color="#00979c">float</font> <font color="#000000">distance</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
<font color="#000000">distance</font><font color="#434f54">=</font> <font color="#000000">Time</font><font color="#434f54">&#47;</font><font color="#000000">58</font><font color="#000000">;</font> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;calculate the distance</font>
<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">distance</font><font color="#000000">)</font><font color="#000000">;</font> <font color="#434f54">&#47;&#47;display the distance</font>
<font color="#000000">}</font>
