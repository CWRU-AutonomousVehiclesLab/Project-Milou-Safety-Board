# Project Milou Safety Board
This repo contains Project Milou's safety board design. The goal of this design is to have a standardized modular designed board that allow other competitor to improve their safety system.

## What is Project Milou?
Project Milou is Case Western Reserve University's second autonomous snowplow robot. The robot actively participate in the ION Autonomous Snowplow Challenge. Currently the latest revision of the robot is utilizing a Teensy 3.6, an ITX computer with a core i5 as its main control system.

## Logistics

Latest revision is done at Febuary, 2020.

The designer of this board can be traced back maybe 5 years, designed by folks working with Project Otto. This board re-layed out by Ziyi Huang as part of fullfilment for his senior project fall 2019. The board is modified by Frank (Chude Qian) to make it work on the robot. 

This project is maintained under CWRU Auontomous Vehicles Lab till 2021, and further maintained under CWRU Biologically Inspired Robotics (Biorobotics) Center. 

*Copyright belongs to CWRU Autonomous Vehicles lab, CWRU Biologically Inspired Robotics (Biorobotic) Center. Please use with acknowledgement.*

### Contact for questions
To contact, email [Frank](mailto:cxq41@case.edu), if currently it is after 2021, email [Ian](mailto:ija2@case.edu) and [Dr. Merat](mailto:flm@case.edu). 

## How to use this?
To use the safety board design, we recommend you to have some basic understanding of Egale the PCB software if you want to modify it. Currently, it should work and it should be fairly easy to use on a standardized ROS enabled robot.


### Pressumptions
The board assumes the following components: a 5V supply, a 12V supply, a standard RC Spread Specturum 2.4G remote reciever, a digital microcontroller that is capable of 5V or 3.3V digital input and output, a standard E-stop Button and a 12V relay.

### Materials
In order to use this PCB board, you will have to manufature it. We recommend [JLCPCB](https://jlcpcb.com/) which only cost about 10 USD for 5 boards. Unless you are mass manufacturing it, for sampling purposes, it should be good enough.

### Putting it together
In BOM folder, you will be able to find an excel sheet where it includes all of the materials you will need to put the board together. **NOTE: Do not use the value on the Eagle Schematics as they might by faulty. It is only used for manufacturing the PCB purpose.**

### 5V or 3.3V?
This board supports both 5V logic system and 3.3V logic. If you need to have the output of the board to a 5V system, you should not solder R19 and R17 (aka a voltage divider to step down the 5V logic).

If your input voltage is normally 5V, I would recommend you use the same Q4 and Q5, instead of listed.

### Wiring it up!
Once you have completed all the steps above, you should be able to wire it up. To do so, start from left to right. The left side are all of the inputs.

**Supply**: The top of the supply terminal is +5V logic voltage, it is also used to power your Remote Reciever. A Ground is then followed. A 12V rail for driving the relay, and another ground.

**RCV-CH3**: For this 4 pin terminal, the top pin is your actual signal, and the middle one is 5V, and the bottom one is GND. Note that the last pin is not used, and additoionally, the 5V pin can be disconnected if your RC reciever runs on a different voltage system. However, make sure that your GND is connected so that the system runs on the same logic signal.

**TEENSYIN** For this terminal, the top two are responsible for tracking the microcontroller output. This is used for allowing the microcontroller to throw an Estop exception allowing the robot to be safely disabled from software. If your design do not have this feature, simply follow the 5V logic guideline and apply 5V directly on to the terminal. The bottom two are responsible for the Red ESTOP button. Simply wire the button to those two leads.

**TEENSYOUT** This is the right single 4pin terminal. This is all the output terminals. The TOP 2 terminals are wired directly to a relay to further drive a contactor for the robot. These two will run on 12V so make sure not to get it onto your microcontroller. The bottom two are responsible for the microcontroller. The microcontroller should use these two to read the state of the ESTOP board. As always, top is signal, and bottom is GND. 

The board is designed to provide you ground wherever you might needed. For best practice you can also use twisted cable for delivering signal as ground pins are widely available. The

