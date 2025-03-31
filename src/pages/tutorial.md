---
layout: ../layouts/BaseLayout.astro
title: "Tutorial"
show: True
order: 2
---

For this tutorial we are just going to make two button controlled LEDs. There are two parts of making this: first the schematic, then the PCB!

### Keyboard shortcuts

KiCad has a lot of keyboard shortcuts that are useful to know! Here's a list:
- a: add a component
- p: place an item (electric and ground)
- r: rotate item
- m: pick up item and move it
- g: grab the item and move it, including attached wires
- w: begin drawing a wire connection
- delete: delete item

### Making the Schematic

A schematic is basically a diagram of the electrical circuit that expresses what parts you use and how they are connected via wires.

Note _where_ you place your parts in the schematic doesn't convey IRL positioning - place it where it's convenient! 

Click here to open the schematic editor:

![](/tutorial/sch1.png)

For making three button controlled LEDs, we need to add our parts in! In KiCad, press A to _add_ a part. A pop-up should appear; first, search for LED, then press _ok_ to add! Place it anywhere.

![](/tutorial/sch2.png)

Repeat this for adding a battery (Battery_cell) to power the device, and two resistors (R) for the LEDs. Press R to rotate items. It should look something like this when you're done!

![](/tutorial/sch3.png)

We're using CR2032s as batteries, which are 3V! So, on the + side of the terminal, it will be 3V, and on the opposite side, it will be ground. 

When connected to the battery, the LEDs (called Light Emitting Diodes) will emmit light! The use of resistors is essential - they prevent too much electricity from passing through the LEDs. Without a resistor, the hungry LEDs would gobble up as much electricity as possible, and end up too hot and burn itself. (No, there won't be any fires, they just make a small pop and turn black.) The resistors we're using are 220ohms! 

Time to add wires! Wires are basically paths that electricity will flow through. We would like to wire the positive end of our battery (the end where there is a +: Where electricity departs) up to the back of the LEDs. Then at the we wire the output of our LEDs up to the resistors. (You can change the order of the LED and resistor!) After that we will want to wire the other end of the reistor to the ground of the battery.

To do this, hover your mouse over one end of a symbol, and press W to start wiring. Drag the wire around and wire your parts together. You should have something like this:

![](/tutorial/sch4.png)

Great job! Now it's the time to associate footprints to the symbols. Footprints define the what the copper connections on the physical PCB look like. Press the following button on the top bar of KiCad:

![](/tutorial/sch5.png)

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

![](/tutorial/sch6.png)

After that, click ok! Your schematic should look the same, but now the footprints are connected.

Save the schematic - you're done with it! Now, onto the PCB!

### Making the PCB

______

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
