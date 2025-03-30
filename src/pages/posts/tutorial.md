---
layout: ../../layouts/BaseLayout.astro
title: "Tutorial"
show: True
order: 1
---

Note: In this tutorial we talk about the movement of electrons to simplify the conecept, but in real life they actually move in the opposite direction than what we say here.

<h2 id="getting-started">Getting Started</h2>
In electronics, we deal with two main units: voltage (V), which is the difference of potential between two points (think of the force pushing electrons to go from one point to another), while current (I) is the amount of electrons passing through a given point.

In the beginner world, there is always a common ground, called VSS, GND or 0V. It's a point where there is no potential, so all the electrons want to go there. Thus if you connect a point that has 5V to GND, electrons will naturally flow from 5V to GND.

## Basic Components

### Resistors
One of the fundamental parts of electrical design is resistors, which are used to limit the current flow. They are characterized by it's resistance, given by the formula R = V / I, which is also known as Ohm’s law.

If you put two resistors series, their resistance combine: It is equivalent to one resistor that has the resistance of the sum of the two original resistors. When two or more resistors are parallel, their total resistance is given by the formula Rtotal = 1/R1 + 1/R2 + 1/R3 + ...

They are used in places where we want to stop components from using up too much electricity, and getting hot then burning itself

### Capacitors</h4>
Capacitors are like tiny batteries, they charge up when you apply a voltage across them, and their internal voltage increase. And discharge when the outside voltage is lower then their internal voltage.

### Diodes</h4>
Diodes are simple electrical components that only allows electricity to flow in one direction. When you see a diode on the schematic, it is often represented with a small triangle with a bar, which represents that electricity can only flow in the direction the triangle is pointing to.

### Buttons</h4>
Buttons do what they do! Press em and they will conduct a current. They have 4 pins, but each pair is actually connected together so it's actually 2 pins.

### Vibration motors</h4>
Vibrates when current is passed through! Use potentiometers or resistors to limit their speed.

### Potentiometer</h4>
Potentiometers have 3 terminals, and act as a variable resistor. By connecting the two ends, they act as a constant resistor, but the pin in the middle is special, it has variable resistance from one end of the potentiometers to the middle pin. If you want adjustable resistance, just wire up one end of the potentiometers, and use the middle pin as output.

### Transistors</h4>
Transistors are more complex, they are divided into NPN and PNP types, and they have three pins, called emmiter, collector and gate.

![](https://hc-cdn.hel1.your-objectstorage.com/s/v3/a381d42773bcd403a74388d6688b6665c933234b_image.png)

In the case of a NPN transistor, the emmiter is where the electrons exits, the collector where the electrons enters. The gate is basically a control circuit. If it’s voltage is the voltage on the emitter, the transister won’t allow electrons to pass. Inversly, if it’s the voltage on the collector, the transistor will allow electrons to pass.

The PNP transistor is the inverse of a NPN transistor: The base needs to be at a lower voltage than the emitter for electricity to flow. When the base is at the same voltage as the emitter, it doesn't allow any electricity to pass through

## KiCAD quick start!</h2>
To design a PCB, we will use KiCAD! A free and open source CAD software. Download it <a href="https://www.kicad.org/" target="_blank">here</a>

Open up the app, and you will be presented with a small popup, click apply. And now you are presented with the main menu.

You first need to create a new project: Go to File &gt; New Project and create it. After that, click on this button to open then schematic editor:

![](/tutorial/schematic.png)
A schematic is basically a diagram of the electrical circuit that expresses what parts you use and how they are connected. Note that they don't convey irl positioning - draw your part anywhere you want!

For this tutorial we are just going to make three button controlled LEDs. Firstly, we need a battery to power the device, so press A and search "Battery_cell", click OK and click anywhere on the schematic to place the component. When you are placing the component, you and also press R to rotate it! We are using CR2032s as batteries, so on the + side of the terminal, there will be 3V and on the opposite side, it will be ground.

Add a few more components in the same way: Two LEDs named "LED" and two resistors named "R". Your schematic should look like this:
![](/tutorial/schematic-nc.png)

The presence of LEDs are obvious, since we need them to be able to emit light. As the name of the name "Light Emitting Diodes" implies, their behaviour is the same as normal diodes, they just emit light at the same time.

The use of resistors is essential - they prevent too much electricity from passing through the LEDs. Without a resistor, the hungry LEDs would gobble up as much electricity as possible, and end up too hot and burn itself. (No, there won't be any fires, they just make a small pop and turn black)

For the values of the resistors, it is 220ohms!

Time to add wires! Wires are basically paths that electricity will flow through. We would like to wire the positive end of our battery (the end where there is a +: Where electricity departs) up to the back of the LEDs. Then at the we wire the output of our LEDs up to the resistors. (You can change the order of the LED and resistor!) After that we will want to wire the other end of the reistor to the ground of the battery.

To do this, hover your mouse over one end of a symbol, and press W to start wirering. Drag the wire around, if you want to make a turn, press W again to anchor your wire onto the current spot, and continue dragging. When you are at your desired destination symbol's end, press W to place. You should have something like this:

![](/tutorial/schematic-wc.png)

Great job! Now it's the time to associate footprints to the symbols. Press the following button on the top of KiCAD:

![](/tutorial/link.png)

You should be presented with a table of all the components you have placed. Press a symbol's row, find the corresponding footprint using the following table, search it up in the top bar and double click the right entry on the right hand side. Repeat this for each component.

| Symbol | Footprint |
| ------ | --------- |
| R | R_Axial_DIN0207_L6.3mm_D2.5mm_P7.62mm_Horizontal |
| LED | LED_D5.0mm |
| Button | SW_PUSH_6mm |
| Battery | BatteryHolder_Keystone_3034_1x20mm |
| NPN | TO-92L_HandSolder |
| PNP | TO-92L_HandSolder |
| C | CP_Radial_D8.0mm_P5.00mm |
| R_Potentiometer | Potentiometer_Bourns_3386F_Vertical |
| Conn_01xN_Pin | PinHeader_1xN_P2.54mm_Vertical (Replace N!) |

At the end, you should have something like this:
![](/tutorial/linked.png)

Now go back to the starting KiCAD window, and press this button to open the PCB editor:
![](/tutorial/pcb.png)

After that, click Update PCB from schematic at the top of the screen:
![](/tutorial/update-from-schematic.png)

You should now have parts under your mouse, click anywhere to place them.
![](/tutorial/parts-unplaced.png)

This PCB is a design of your IRL circuit board, so this time the placement of components will matter - Where you place them is where they turn out on the final product, so think carefully where they should go!

Click on a component and press M to drag them around, and press R to rotate. If you want to place a component on the back side, press F to flip. Here is the placement I'm going with:
![](/tutorial/parts-placed.png)

Now, go on the right menu bar, and select "Edge.Cuts". After that select the draw rectangle tool

![](/tutorial/draw-rectangle.png)

Use this tool to draw a rectangle around your components - That will be the outline of your circuit board and mark the size of the physical product.

![](/tutorial/board-outline.png)

Great job! The only thing left is wirering the board. Hit X on your keyboard and while hovering over any golden pad with a thin blue line poking out of it. It should dim the entire screen, and show you which direction you need to go with a thin blue line and highlight the destination:

![](/tutorial/routing.png" className="max-w-96)

**Attention**! Wires and pads of different colors (except golden) can't be connected together directly! You must via to the other side.

If you want to start routing from the back side, select "B.Cu" on the right menu bar.

Continue until there are no thin blue lines on the screen! The final product should look something like this:
![](/tutorial/routed.png)

Good work! You're almost done with the PCB. Let's run the DRC to make sure the PCB works. The silkscreen warnings you see are okay, make sure there are no more errors!

![](/tutorial/drcbutton.png)

If there are, please resolve them! Otherwise we only need to generate the final fabrication file! Go back to the main KiCAD window, and click "Plugin and Content Manager"

![](/tutorial/plugins.png)

Search up "Fabrication Toolkit" and install it. Now go back to the PCB editor, you should see a new button appear, click it and click generate

![](/tutorial/fabrication-toolkit.png)

Contgrats on making a PCB! You should find a .zip of your project in the "production" subfolder of your project's directory - thats the file that you need to send to the manufaturers! All that's left is to open a pr and submit your project :D

One last step before submission - please take a screenshot of your schematic and PCB, then put it inside your README.md of your project! (Create a README if you don't have one)

After that, you only need to wait for your submission to get approved :D
