# Soldering Instructions for *Beatmaker's Sketchbook DIY v1*

Welcome to the soldering instructions for the *Beatmaker's Sketchbook DIY v1* and thank you for purchasing a kit from sucofunk.

Soldering all the components to the PCB and bringing *Beatmaker's Sketchbook* to life will take about 3-6 hours, depending on your skills. <br>
Please read the complete instructions guide and follow the instructions step by step in the described order. <br>
Some tasks may seem tedious, but in the end it will be satisfying and worth the work. ;)

### Parts

If you bought a complete kit from sucofunk.com, you are fine to jump to the next section.
Here is a picture of all the parts you should have received:

![All components on a plate](images/components.png)

### Sourcing parts

If you are sourcing the parts by yourself, take a look at this BOM at Octopart: https://octopart.com/bom-tool/qJS5oQ3y

Pay attention that the microphone, display and slide switch could not be found on Octopart. Links to the right products are added to the description field. Pay attention to the desciption column, as there are some comments on similar parts and so on.

You need to solder the two PSRAM modules to the Teensy 4.1 by yourself. Check [this page](https://www.pjrc.com/store/psram.html) from PJRC for instructions. If you bought a kit, the modules are already soldered to the Teensy and tested.

## 1. Preparation

To get started with soldering, you will need some preparation. First, get all the tools you need, then clean the big PCB for soldering.

### Tools you need
* Soldering Iron
* Solder
* Wire cutter
* Cutter knife
* Small screwdriver (+)
* Basic Multimeter (only "Resistor measurement" -> Ohm and "Continuity check" -> beep needed)
* Tape
* Lighter
* Alcohol to clean the PCB (do not use the lighter with the above mentioned alcohol) ;)
* In case you mess something up, a *desoldering pump* might be helpful
* A "third hand" might be helpful at some points, but is not needed. Check out [Omnifixo](https://omnifixo.com/) - it's perfect!
* Micro USB Cable to connect the Teensy Microcontroller to your PC

### Bring your skills up to date, if needed

If you are a complete beginner in soldering, you should learn the basics. There are plenty of videos on Youtube. A good recommendation is [this video](https://www.youtube.com/watch?v=QKbJxytERvg) from Collin's Lab.

In case you mess something up, you should be familiar with desoldering, too. Another recommendation is [this video](https://www.youtube.com/watch?v=N_dvf45hN6Y) from Collin's Lab.

If you need information on how to use a multimeter, reading [this article](https://learn.sparkfun.com/tutorials/how-to-use-a-multimeter/all) is a good starting point.

### This is what the result will look like
<p style="color:red">
ToDo:
- zwei Bilder der Platine ohne Komponenten
- zwei Bilder komplett bestückt
</p>
### Remove Tabs from PCB

There are some tabs around the PCB which hold the Board in place while manufacturing. Most of the time, these tabs are not removed properly. You should remove them, otherwise the board might not fit 100% into the case and you might cut your fingers.
Depending on the size, use a wire cutter or a cutter knife to remove the tabs. Sanding paper might be helpful, if you are a perfectionist.

![Remove Tabs](images/tabs.png)

### Clean PCB

To prevent cold solder joints which might appear, if the solder pads are greasy, clean the whole board with alcohol. Isopropanol is a good choice. Some vodka might work, too. Just pay attention it is clear liquor without sugar ;)

Just use some fabric, drip some alcohol on it and wipe the board clean. Do not drown the PCB in alcohol. It will probably not harm, but we do not want it to get dizzy. ;)

If you feel the PCB gets greasy while working with it, repeat the step.

## 2. IC Sockets

Place the six IC sockets on the corresponding places on the top side and solder them from the bottom side. Don't worry, you cannot place them wrong, as long as you place them on the top side as shown in the pictures.<br> Yes, we are starting with a lot of soldering. ;)

![ICs](images/ICs.png)

**Pro Tip**: Place the ICs on the top side, cover the PCB and IC sockets with a sheet of paper, flip everything over and remove the sheet of paper. This way you do not have to hassle with the sockets ;)

**Why are we using IC sockets and do not solder the ICs directly to the PCB?**<br>
You can do it, if you want, but this way it is beginner friendly. You don't have to worry to kill the IC with too much heat or whatever could go wrong.

**What are the ICs for?** <br>
The five **big ICs** are Port expanders. They have 16 Input/Output pins and are used to identify button pushes (input) or light up our LEDs (output). In total these five ICs offer 80 input/output options. If we would connect all the buttons and LEDs to the teensy directly, there would not be enough pins. The Port expander ICs communicate via I2C Bus with the teensy. The I2C Bus only needs 2 PINs for communication and each IC has an interrupt connection to the teensy to send an interrupt signal, if an interrupt pin receives a signal (e.g. a button pressed or released). The teensy listens to the five interrupt (short: IRQ) pins and queries the corresponding IC via the I2C bus what happened.<br>
The **small IC** is an optical coupler and is used for incoming MIDI signals. With MIDI you are connecting another device to the Beatmaker's sketchbook and the optocoupler makes sure the external device is not interfering with our circuit. In a basic explanation it internally works with light. The incoming electrical power is triggering a light source and the optocoupler receives the light signals and transforms it into electrical signals for our circuit.

## 3. Note Keys

Mounting the "note keys" - the buttons which map the two octaves of the keyboard - is easy. This task is the one where you should work as neat as possible. Pay attention to place the buttons as straight as possible. If a button is not straight, you will always see it, when the key caps are mounted.

![Note Keys](images/noteKeys.png)

**A common source of defect** is bending down a button's connector pin. If it is not going through the PCB, you might not notice it when soldering the button from the backside and that button will not be connected and therefore not work.

## 4. Function Buttons & Program Button

These are the buttons to control Beatmaker's sketchbook: Function, Menu, Set, Switch, Play, Stop, Record, Input Selector, Left, Right, Up, Down.<br>
Just plug the 12 buttons on the top side into the PCB and solder them from the back side.

![Function Keys](images/fnKeys.png)

On the bottom side you need to plug the 13th button - the **Program button**. Do not forget to solder it on the top side of the PCB. <br>
In case the auto **upload** for the **firmware** does not work, you need to push this button to upgrade the firmware. <br>It can be used to perform a **hard reset** of the Teensy microcontroller, if you hold the button for more than 15 seconds.

## 5. Resistors, Capacitors & Diode

All the resistors, capacitors and the diode come in a small bag. Besides the bag you will find a sheet with designated areas where you should place the parts.

![Component Sheet](images/sheet.png)

Now start from top to bottom and place each part at the described position on the PCB.

All parts from the sheet should be mounted on the top side of the PCB. After soldering, cut the remaining parts of the legs with a wire cutter.

If a resistor lost its label, you should use a multimeter to measure its Ohm value. If you do not own a multimeter, another option might be checking the coloured rings against a resistor table. You can find one [here](https://www.digikey.com/en/resources/conversion-calculators/conversion-calculator-resistor-color-code).

It is always a good idea to double check the resistors value before soldering it to the PCB.

### Resistors
Bend the resistor wires right at the edge of the resistor. This way it will fit straight into the PCB. Resistors do not have a polarity. It does not matter which way you put them on the PCB. Just place it the way you like it most - they are coloured! ;)

![Resistor](images/resistor.png)

### Capacitors

The capacitors can be inserted directly into the PCB. You do not need to push them until the capacitor head reaches the PCB. If they touch the PCB - no problem. The capacitors in this kit do not have a polarity marker. Just place them as you like, but do not use/place/solder C3 - it's for experimental use only ;)

![Capacitor](images/capacitor.png)

### Diode

The diode needs to be placed in the right direction at position D33. The black marker should be on the same side as the white line printed on the PCB.

![Diode](images/diode.png)


## 6. Volume Potentiometer

To change the volume, a thumbwheel potentiometer needs to be mounted on the PCB.

Please note, that the volume potentiometer should be mounted from the bottom side, if you want to use the official enclosure.

![Thumbwheel Potentiometer](images/volume.png)

The potentiometer is connected to an analog input on the Teensy microcontroller. From time to time the controller reads the current resistance of the potentiometer - a potentiometer is a variable resistor - and adjusts the output volume.

## 7. Line Jacks

Now it's time to mount and solder the line jacks. It's straight forward.

![Line In and Out](images/line.png)

## Interlude - The PCB Holder

<p style="color:red"> ToDo: short description.. </p>


## 8. Connectors and Pins

### Female connectors

To connect the additional PCBs for audio input/output, power management, the brain a.k.a. Teensy 4.1 and the amplifier to drive the speakers, will be connected to the Beatmaker's sketchbook PCB via female connectors. The connectors need to be placed on the bottom side of the PCB and will be soldered on the top side.<br>
Take the two 50 connector strips and cut them into eight parts:

![Connectors](images/connectors.png)

11 single connectors will remain. We do not need them for this project. You can build something funny with it or save them for another project. You should never throw spare parts away. ;)

### Male connectors / Pins

Now we cut the counterparts, the male connectors or often called *Pins*. Same procedure as before.  

![Cut all pins](images/cutPins.png)

We will solder the pins in a further chapter - not now. So put them aside and continue with soldering the female connectors, first.

### Soldering

Now place the connectors and solder them as shown on the pictures. You should use the PCB holder to keep them in place. Pay attention that they are aligned in a 90° angle to the PCB. Otherwise you will get in trouble connecting the additional PCBs.

![Placing connectors](images/connectors2.png)

And a more detailed view. Do not forget the single connector "inside" the Teensy. It will connect the battery to power the brain. One of the most important connections. ;)

![Placing connectors](images/connectors3.png)

## 9. Microphone

Mounting the microphone is an easy task. Just place the microphone in the right position, as shown on the picture and solder.

![Microphone](images/mic.png)


## 10. Screen PINs

You reached one of the first hacks! Tear some cardboard from the display package off and place it on our workplace.<br>
Use the long pins (see picture) and put them from the top side through the holes for the display connector. Turn The PCB upside down, use the PCB holder and make sure the pins are touching the cardboard. Solder the pins on the bottom side of the PCB.

![PINs for display](images/screenPINs.png)

**Why?**
Because we do not want the pins to scratch the plexiglass cover when it is mounted. The cardboard is used as a little spacer.

## 11. LEDs

LEDs need to be placed in the right direction. The long leg is always connected to power (+) and the short leg needs to be connected to ground (-). Put the long leg through the round solder pad and the short leg through the squared solder pad as shown in the picture.

![LED polarity](images/LEDpolarity.png)

To position the LEDs right below the plexiglass cover for best visibility of the light, you should use the PCB holder. Solder one LED after the other. Start with one leg, then bend the LED in place and solder the second leg. Cut the remaining parts of the legs with a wire cutter after soldering.

![LED](images/LED.png)

Place the **red** LEDs on positions **D1-D8** and the **green** ones on **D9-D32**.

## 12. Front- & Power-switch PINs

Up to the next hack! Soldering the connector pins for the fader and the fader LED might be a bit fiddly.

Take the angled 5 PIN connector, put it through the holes of the PCB and bend it to the +-45° angled position shown in the picture. Then hold it somehow in place - tape might help - and solder it. The PINs should not be directed to point off the board as it would not fit in the case afterwards.

![Power PINs](images/frontPINs.png)

Repeat the task with the angled, 2 PIN connector at the power switch position as shown in the picture.

![Power PINs](images/powerPINs.png)

When done, shorten the two power button pins with a jumper. If you bought a complete kit, the jumper is already attached to the pins. The jumper will be our temporary power switch. Removing the jumper will switch the device on. Putting it back on will turn it off.

## 13. MIDI Sockets

Mounting the MIDI connectors might be a bit difficult as they tend not to stay in place if you flip the PCB for soldering. It might be helpful to use some tape to hold them in place for soldering.

![MIDI sockets](images/midi.png)

## 14. Headphone Jack

This step is straight forward. Plug the headphone jack in and just solder.

![Headphone jack](images/headphone.png)

## 15. Install Teensy

### Remove the SD card

If you bought a kit from sucofunk.com, the SD card is already plugged in to the Teensy. It is recommended to remove the card before soldering the PINs to prevent accidents with your soldering iron and the plastic housing of the card ;)

### Adding PSRAM

You can skip this step, if you bought a complete kit from sucofunk.com. If you sourced the parts by yourself, now would be a good time to attach the memory. If the pins are already mounted, it is going to be a bit more difficult.

### Solder Pins

Now fetch the pins back from where you stored them and take the two 24 pin strips, the 5 pin strip and the single pin and place them with the long side into the female connectors you soldered before.

![PINs for Teensy](images/teensyPins.png)

Now it is a good moment to take the alcohol and clean the solder pads of the Teensy microcontroller. We do not want loose connections to the Teensy, as they are very hard to locate, if something is not working.

Then take the teensy and place it on the short, pointing upright, side of the pins. All pins need to go straight through the Teensy PCB as shown in the picture.

![Mounted Teensy](images/teensyMounted.png)

It's time to link the brain to the system. Pick up your soldering iron again and solder all 54 pins to the Teensy microcontroller. This task is one of the most tedious ones in the whole project, as the solder pads are very small. By now you should be a soldering pro - take a deep breath and solder. ;)

**Pro Tip**: Start by soldering the four corner pins first. This way the Teensy is fixed correct and soldering the other pins is a bit more easy, as the plastic that is holding the pins might deform a bit.

## 16. Audio Board

Repeat the last step with the Sucofunkey Audio Board. Pay attention to place it the right way! On one side the pins are labeled on both PCBs. Pay attention the labels on the main PCB and the audio board match - as shown in the picture.

![Audio Board](images/audioBoard.png)


## 17. Encoders

Now it is time to mount the four rotary encoders. If the PCB does not have mounting holes for the encoders "mounting clamp-pins", just cut them off with a wire cutter as shown in the pictures.

![Encoder](images/encoderCut.png)

Then mount the encoders and solder them to the PCB. Repeat this step for all four encoders.

![Encoder](images/encoder.png)


## 18. Mount ICs

<p style="color:red"> Remember what they are used for? </p>


## 19. Amplifier & Speakers

During one of the the last steps we connected the audio board, which outputs the audio signals from the Teensy to the analog world. But hey, it is impossible to hear anything from that audio board without speakers. Ok, you already soldered the headphone- and line-out jacks some steps ago, but that is not enough.

So we need a small amplifier and two speakers to make *Beatmaker's sketchbook* rock.

First take the small bag with the "3.7W Class D Amp" and attach all the pins and clamps as shown in the picture. DO not forget to solder ;)

![Amplifier](images/amp.png)

Then plug the amp into the connectors you soldered before to the main PCB. They are labeled with "MAX98306". You cannot place it to a wrong place, as there is no other free 9 pin connector left on the board.

For a detailed solder guide and some further information to the amp, check out [this instruction](https://learn.adafruit.com/stereo-3-7w-class-d-audio-amplifier) from Adafruit.

Ok, amplification should not be a problem. You can set the gain with the small jumper, which is inside the bag. As there is a default gain setting, you can do this at a later stage, when you hear the output.

Now let's connect the speakers. There are two red and two black wires in the kit. Take them and solder them to the solder pads at the speakers. The polarity (+ and -) is written in the middle of the speakers. Solder the red wire to + and the black one to the - pad. Pay attention to direct the wired to the middle of the speaker as the wires will go through the middle of the 3D printed speaker shell.

Tin the ends of the wire by heating by heating it up with the soldering iron up and apply some solder. This keeps the inner wires straight

![Speaker](images/speaker.png)

If you soldered all four wires to the two speakers, connect the ends of the wires to the amplifier. You need a small screwdriver for this task. Connect the **black wire of the left speaker** to **LOUT-** and the red wire of the left speaker to the connection right beside the black wire. Repeat this step for the right speaker by connecting the **black wire of the right speaker** to **ROUT-** and as you already guessed, connect the red wire to the position right beside the black wire. ;)  

Well done! We are done with soldering for now and ready to power the system up and check if your Beatmaker's Sketchbook is working.


## 20. Test

Before the first test we need to prepare two more things.

### Plug the SD card back in
As you might remember, you removed the SD card from the Teensy before soldering the pins. Now it is time to put the card back in.

### Connect display
A Test without a display? Now way - you cannot see, if it is working ;)
So use the display adapter cable from the display box and connect the white connector on the backside of the screen with the white plug from the cable. Then plug the wires according to their position on the display PCB (VCC, GND, DIN, CLK..) into the display connector on the main PCB.

ToDo: Bild

### Powering the system for the first time

ToDo: USB connection

### Test if everything is working


## 21. Mount Display
- remove screws from display
- attach display spacer with screw
- place Display
- solder

## 22. Power Supply

To continue with this step, unplug the micro USB cable from Beatmaker's Sketchbook, first.

### Preparing the teensy for battery power
If you are not using the power management board and do not power your Beatmaker's sketchbook from a battery, you should skip this step.

Otherwise you need to separate the two pads on the bottom side of your Teensy 4.1. The standard configuration is to use the Teensy with USB power. We will power the teensy from a battery. To not mix the GND from the USB and the battery (which will definitely harm the Teensy!), we need to decouple them by cutting the small trace with a cutter knife.

![Cut pads](images/teensyPads.png)

To make sure the trace is cut, you can use your multimeter and check if there is a connection or not. You can do this by using the continuity check, which beeps on most multimeters, if there is a connection between the two probes. Place one probe on each pad. If it beeps, there is still a connection. If it does not beep, we are done with this step.

### Battery charger

To give power to *Beatmaker's sketchbook* from a battery, we need to connect the battery charger module. It is a Power Boost 500 module from Adafruit. You need to solder the last 8 pin strip to the module. Pay attention to solder it upside down or in this case downside up as shown in the picture. When you plug it into the main PCB, the labels have to match. Pay attention to do everything right and **do not connect the LiPo battery before soldering**.

![Power management](images/power.png)

There is a USB jack in the *Power Boost 500 bag*. We do not need that plug for *Beatmaker's sketchbook*. Do not solder it and keep it with the spare pins and connectors. ;)

Check, if the jumper is still connecting the power switch pins! If not, fix it, because in this case the connected pins are the same as a power switch. In our case connected means off and no connection (jumper removed) is on.

Now you can plug the battery in and if the blue LED is shining, there is some power in the battery and we are ready to go. Plug the Power Boost to the main PCB.

![Power management](images/powerMounted.png)


## 23. Connect Fader and Fader LED
### 1. Disassemble Display cable
### 2. Heat shrink tube
### 3. Connect Female 5 Port Dupont housing
### 4. Solder wires to fader
### 5. Mount LED
Do not mix GND and VCC,
Isolate connectors

## 24. Power Switch
