# rssi-nav
Robust Localization and Navigation Algorithm Based on the RSSI
###### Study and realization of a robot follower/human assistant

### Signings

We dedicate this work to our beloved parents who have supported us at every stage of our
lives and this project in particular.

We also dedicate this work to all soldiers who died on the battlefield and to those who died in
natural disasters.

We just wanted them to be proud of us and to feel more confident in our skill set required
after graduation to acquire a job.





# Chapter 1: Needs Analysis


## Chapter 1: Needs Analysis

#### Introduction:

In this chapter, we will analyze the needs of this project and its design. We will discuss all the
services provided by this robot.

We will provide all the technical aspects that we have followed and carried out to carry out
this work.

#### 1. Functional needs

##### 1.1. An autonomous robot

We want the robot to be autonomous and follow a given signal. This signal will be Wifi 2.4 GHz.

##### 1.2. Detecting obstacles

A set of infrared sensors is attached to the robot to help it move without collision.

These sensors detect obstacles to the right, left and in front to help the system make the right
decision and detect exactly where the obstacle is.

#### 2. Non-functional needs

##### 2.1. Constraint of use

The user interface must be simple and easy to understand so that the user can benefit from the
system's functionality.

##### 2.2. Performance constraint

We use raspberry pi as the main processing unit to make decisions and process data. We
chose not to use a standard operating system but a custom one (DietPi) to gain performance
and reduce power consumption. We also selected the 512 MB RAM model.

#### 3. Use case diagrams

A use case is a specific way to use a system.


##### 3.1. Global Use Case Diagram

To have a global view of our system, the figure below presents an overview of the different
functionalities expected by this project. The robot moves without any human control and
avoids obstacles if they exist and reaches its destination at the end.

```
Figure 1- Global use case diagram
```
##### 3.2. Use case diagram location of the object tracked by signal

##### detection

We have two parts to this project:

- The part that emits a signal
- The part that detects the signal and tracks it

We will use the signal strength or decibel per meter (Dbm) to locate the target. When the Dbm
is stronger, the robot continues its route; if the Dbm weakens, the robot changes direction.


```
Figure 2- The object tracked by signal
detection
```
## Conclusion

In this chapter, we have tried t o explain the need for this project, as well as our general approach
on how we will design this robot and how it will work.


# Chapter 2: Studies and

# Implementation


## Chapter 2: Design and Implementation

#### Introduction:

In this chapter we will try to detail all the components, circuits and techniques used to carry
out this work.

We will also mention the main steps we followed in the realization.

#### 1. Tools and software :

##### 1.1. SolidWorks

SolidWorks is a computer-aided design (CAD) and computer-aided engineering (CAE) solid
modeling computer program [7].

We used SolidWorks to design all the mechanical parts for our project.

```
Figure 3- SolidWorks design
```

##### 1.2. EASYEDA

```
EasyEDA allows the creation and editing of electronic schematics, SPICE simulation of
mixed analog and digital circuits, the creation and editing of printed circuit boards and,
optionally, the manufacturing of printed circuit boards [4].
We used EasyEDA to design all the electronic circuits.
```
##### 1.3.^ DietPi OS^

```
Why DIETPI®?
```
```
We chose this system because we wanted to achieve ultimate performance, speed and stability
while consuming less power.
Moreover, we had experience with Linux systems and DIETPI is light for the raspberry pi
board. And since we use our robot for sensitive business, we needed maximum security to
avoid any intrusion [5].
```

##### 1.4. Python

```
The python language is one of the most accessible programming languages, as it has a
simplified and uncomplicated syntax, which places more emphasis on natural language.
Because of its ease of learning and use, python codes can be easily written and executed much
faster than other programming languages [3].
```
```
Python has a timing library that helps us to put time between instructions and a GPIO library that
helps us to interact with the raspberry pins.
```
_Figure 4-time library and GPIO_^

```
Figure 5 - Motor control function
To control the motors we use ('HIGH', 'LOW') or (1,0)
```

```
Figure 6- Program to detect the wifi signal
```
We use 'iwlist' to scan the available wifi networks and get all the necessary information.

We will explain iwlist in the bash section since it is related to bash. The

code is so simple actually. There are four functions:

forward to go forward

back to go backward

left and right to move left and right

So we have three variables F, L and R, the raspberry pi stores different values in these
variables every 10 seconds and there is a comparison that is done in the code by comparing
the three variables and the highest variable is the one where the robot has chosen a direction.

##### 1.5. Bash

Bash allows us to use Linux executables and tools. So in our mission we need a package
called iwlist [2].


```
Figure 7- IWLIST
iwlist is used to display some additional information of a wireless network interface.
We only need the dBm section so we used python to filter the output
```
##### 1.6.^ Lighttpd^

```
Lighttpd is an open source web server optimized for speed-critical environments, while remaining
standards-compliant, secure and flexible.
In order to diagnose, manually control and test the robot, we added a web server and a simple web
page to control the robot.
```
##### 1.7. HTML & CSS & JS

```
We used html CSS to design the web page that allows the user to manually control the robot if
needed and JavaScript to send commands to the robot via the web server.
```
```
Figure 8- Web page
```

^
_Figure 9- html CSS JavaScript code_

#### 2. Mechanical studies and realization :

```
The mechanical aspect is so important, so we tried to make our robot as hard as possible.
As design software, we used Solid Works.
```
```
Figure 10 SOLIDWORKS logo
```

##### 2.1. Required components

```
Figure 11 - Metal plate [8]
```
```
Figure 12 - Steel stove bolt[9]
```
```
Figure 13-Motor [10]
```
(^)
_Figure 14-Wheel [11]_


As we cannot fix the wheel to the motor, we have modified the diameter of the motor head
with the help of a turner.

And we've boosted the torque for more power on rough terrain.

#### 3. Electronic studies and realization :

We wanted this robot to be highly customizable. So we designed all the circuitry we need to
better understand all the parts we use and to make the robot work better.

In the same context, we design circuits from the robot charger to the motor driver and more.

In this chapter, we will discuss all the parts and steps of the circuit.

##### 3.1. 12V battery

The battery is composed of lithium cells, each has 3.7V. So we built a block containing three

cells in series and we connected three of these blocks in parallel.

```
Figure 19- Simplified battery design
```
```
Figure 20 - Cell type
```

^
_Figure 27- Diodes_

```
Figure 28-2 Resistors: 1kOhm and 3kOhm
```
##### 3.3.2. Circuit^

```
Figure 29-Voltage regulator circuit from 12V to 5V
```
(^)
_Figure 30- Regulator circuit test of 5V voltage and maximum amperage 3A_


#### 4. Studies and realization of the Wi-Fi infrastructure :

```
➢ Why didn't we use GPS for navigation?
```
When we start talking about robots and the need for sensors, the question many people ask is,
"Why don't we just use GPS? GPS is everywhere - it's in our phones, it's in our cars... it tells
us where we are.

A robot is on the ground and has a GPS receiver. In the sky there are several satellites in low
orbit, all of which send radio waves that the robot's GPS receiver can pick up.

Using the time it takes the radio wave to travel from each satellite to the robot, we can
calculate the distance between each satellite and the robot.

If we know these distances well enough - we know where the satellites are in space - then we
can determine where the robot is. This is the fundamental principle of GPS.

A robot is in an urban environment so part of the sky is obscured. We can't see all the
satellites. Now we can only see two satellites and that is not enough to get a position.

Now, if a robot is in a large industrial complex. There are big walls, chimneys and metal
structures. The satellite signals may not travel in a direct line to the robot. They may bounce
off some of these metal structures before reaching the robot. The problem is that the signals
have traveled a longer distance than the actual distance between the robot and the satellite.
The path length has been increased by what is called "multi-leg reflection". The robot's GPS
receiver does not know this and provides an incorrect estimate of the robot's position.

Another problem with GPS is that not all countries have the same technology.

GPS, or Global Positioning System, is one of four global satellite navigation systems The four
global GNSS systems are: GPS (United States), GLONASS (Russia), Galileo (EU), BeiDou
(China). There are also two regional systems: QZSS (Japan) and IRNSS or NavIC (India).


##### 4.1. Required components

```
Figure 54-Wifi USB [13]
```
(^)
_Figure 55-USB extension cable [14]._
(^)
_Figure 56-Servo motor [15]_

##### 4.2. Operating principle

```
Figure 57 - Operating principle
```

```
The diagram above shows the relationship between distance and dBm Wifi.
```
𝑥 = 10 log (^10 1) 𝑚𝑊𝑃^ [a]
x : power dBm^
𝑃
1 𝑚𝑊
: power in milliwatts
The USB wifi is attached to the servo motor and the servo motor rotates left, right and front
recording each time the dBm value in different variables called L, R, F.
In the next part, we will see how the robot can decide where to move using this method.
_Figure 58- Servo movement relationship and programming variables_


##### 4.3. Wifi range

As we all know, Wifi has a short range, but what most people don't know is that all devices
only display Wifi signals when they are able to connect to them. In our application, we don't
need connectivity but only to detect the signal strength.

Another concept to add to the equation is the channel in Wifi, it is true that Wifi is
2.4Ghz but is it exactly 2.4Ghz? [d]

No, Wifi has channels that differ slightly in frequency that can help extend the detection
distance.

```
Figure 59- Wifi channels
```
Since frequency and distance are inversely proportional, we choose channel number 1 because
it has the lowest frequency.

Higher frequencies become more attenuated as they move away. There are two effects that are
responsible for this.

First, high frequency radio waves tend to be absorbed more easily by objects.


```
The second effect is less intuitive and is derived from the Friis equation f o r free-space path
loss.
```
```
𝐹𝑆𝑃𝐿 = 10log 10 𝑑 + 20log 10
```
(^) 4Π
𝑓 + 20 log (^10) 𝑐 [b]^
(^)
Where FSPL is the free space path loss in dB, d is the distance in meters, and f is the
frequency in hertz, and c is the speed of light. Note that as f increases, the attenuation
increases [5].
The last concept we used to extend the range of our Wifi range is the point-to-point link[c].
Point to point links vary in range, we can get links from 20-30 meters to about 12km in good
conditions.

#### Work done:

```
Figure 60- Point to point links [c]
```
```
After completing all the design steps, we printed the circuit and here is the result.
```

_Figure 61-_^ _Map after printing_^

```
Figure 62- Map after printing
```
```
The robot: Here we present a set of photos of the robot from the first phases to the final phase.
```

_Figure 63-_^ _Real photo of Robot_^1

_Figure 64-Real picture of Robot_^2

_Figure 65-Real picture of Robot_^3

_Figure 66-Real picture of Robot_^4

```
Figure 67-Real picture of Robot 5
```

_Figure 68-Real picture of Robot_^6

_Figure 69-Real picture of Robot_^7

_Figure 70-Real_^ _picture of Robot_^8

```
Figure 71-Real picture of Robot 9
```

_Figure 72-Real picture of Robot_^10

_Figure 73-Real picture of Robot_^11

```
Figure 74-Real photo of Robot 12
```

#### General conclusion

This project was the best opportunity to exploit the techniques and theoretical knowledge
acquired during our academic training at the Higher Institute of Computer Science and
Mathematics of Monastir. After finishing the project, we felt so proud of the knowledge we
had and the knowledge we acquired while doing this work.

Indeed, the study and the realization of our project, allowed us to value our capacities in
programming, electronics, radio frequency and telecommunication. We will be able to
improve the application to make the interactivity more flexible and complete with the user,
also we can evolve even the robot by integrating multiple new sensors and detectors, and
various circuits to make it even more complete and automated.

The main objective was to dive into the world of robotics because it is a trend that has helped
many countries to evolve.

#### Perceptive

This robot is needed in many areas. Thus, in future implementations, we can add a robust
hand to hold different objects.

```
Figure 75- Robotic hand [16]
```
We can also change the motor controller with MOSFET controllers to improve response time
and power consumption.


```
Figure 76 - MOSFET controllers
```
We can add an electromagnetic holder so that the robot can be charged without the need to be
connected to a wall socket.

```
Figure 77- Electromagnetic support [17]
```
We can also further investigate our choice of parts to see if we had the best options like obstacle
avoidance sensors and USB wifi.

As a programming language we should continue to use bash but we can start using Rust
because this language is faster than C, C++ and python.

```
Figure 78 - Rust language[18]
```

#### Abbreviations

GPIO: General Purpose Input Output

WIFI: Wireless Fidelity

GPS: Global Positioning System

HTML: Hypertext Markup Language

CSS: Cascading Style Sheets

MOSFET: Metal-Oxide-Semiconductor Field-Effect Transistor

#### Bibliography

[a]: A Note on a Simple Transmission Formula Friis, H.T. (May 1946).

[b]: Antenna Theory and Design Stutzman, Warren; Thiele, Gary (1981).

[c]: TR- 1 4 | Structural Standards for Communication and Small Wind Turbine Support
Structures.

[d]: Wireless Communications Systems Design Book by Haesik Kim

#### Website used:

[1] : https://www.ti.com/

[2] : https://www.gnu.org/software/bash/

[3] : https://www.python.org/

[4] : https://easyeda.com/

[5] : https://dietpi.com/

[6] : [http://www.datasheetcatalog.com/](http://www.datasheetcatalog.com/)

[7] : https://www.solidworks.com/

[8] : https://fr.aliexpress.com/item/1950797362.html

[9] : https://www.amazon.fr/Boulon-po%C3%AAlier-acier-zingu%C3%A9-
FixPro/dp/B00QKQABCK

[10] :https://air.imag.fr/index.php/Hack_de_Moteur_perceuse/viseuse_sans_fil_12V_(bon_m
arch%C3%A9)

[11] : https://www.rootshop.com/be/fr/paire-roues-caoutchouc-bleu.html

[12] : https://tuni-smart-
innovation.com/index.php?id_product=144&id_product_attribute=0&rewrite=module-relay-
4 - channel&controller=product
[13] : https://www.cdiscount.com/informatique/r-cle+usb+wifi+150+mbps.html

[14] : https://www.ldlc.com/fr-lu/fiche/PB00147384.html


[15] : https://www.aranacorp.com/fr/pilotez-un-servo-avec-arduino/

[16] : https://i.pinimg.com/originals/8d/49/15/8d49154519d6f0a0890167813656adf1.jpg

[17] : https://support.bissell.com/app/answers/detail/a_id/3770/~/my-spinwave-robot-first-
use%2C-charging%2C-%26-cleaning-%7C-support

[18] : https://www.rust-lang.org/


