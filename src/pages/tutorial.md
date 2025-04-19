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

Great job! Now it's the time to associate footprints to the symbols. Footprints define the what the copper connections on the physical PCB look like. There are two big types of component footprints: THT and SMD.

![](/tutorial/tht-vs-smd.png)

THT components need a hole on the PCB to be mounted (Normally a yellow circle on kicad), they will also have iron legs sticking out of the component, they are easy to solder. SMD components doesn't need a hole on the PCB to be mounted, are typically smaller and super hard to solder. You generally don't want to solder these by hand.

We will be using the THT footprints. Press the following button on the top bar of KiCad:

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
| R_Potentiometer | Potentiometer_Vishay_T73YP_Vertical |
| Conn_01xN_Pin | PinHeader_1xN_P2.54mm_Vertical (Replace N!) |

![](/tutorial/sch6.png)

After that, click _Ok_! Your schematic should look the same, but now the footprints are connected.

Save the schematic - you're done with it! Now, onto the PCB!

### Making the PCB

Now go back to the starting KiCAD window, and press this button to open the PCB editor:

![](/tutorial/pcb1.png)

After that, click Update PCB from schematic at the top of the screen - this gets what you made in the schematic into the PCB:

![](/tutorial/pcb2.png)

You should now have parts under your mouse, click anywhere to place them.

![](/tutorial/pcb3.png)

This PCB is a design of your IRL circuit board, so this time the placement of components will matter - where you place them is where they turn out on the final product, so think carefully where they should go!

Click on a component and press M to drag them around, and press R to rotate. If you want to place a component on the back side, press F to flip. Here is the placement I'm going with:

![](/tutorial/pcb4.png)

Remember to not block where the battery slides in with parts!

Now, go on the right menu bar, and select "Edge.Cuts". This is the outline of your board! Using the polygon tool, you can draw an outline for your board. I'm going for a cat-like shape!

I highly recommend drawing a more detailed SVG (ie: Figma), then import it in by File > Import > Graphics. 

![](/tutorial/pcb5.png)

Great job! The only thing left is wiring the board. Click the wire symbol on the right sidebar, then click on any component pad. It should dim the entire screen, and show you which direction you need to go with a thin blue line and highlight the destination:

![](/tutorial/pcb6.png)

**Attention**! Wires and pads of different colors (except golden) can't be connected together directly! You must via to the other side.

If you want to start routing from the back side, select "B.Cu" on the right menu bar.

Continue until there are no thin blue lines (called ratlines) on the screen! Because my design is simple, I only need to wire on one side. The final product should look something like this:
![](/tutorial/pcb7.png)

Good work! You're almost done with the PCB. Let's run the DRC to make sure the PCB works. Go to Inspect > Design Rules Checker to open the pop-up, then run it. If you get any silkscreen errors, that's alright, but make sure there are no more errors!

![](/tutorial/pcb8.png)

If there are, please resolve them! Otherwise, it's time to pretty up the PCB! With the _Draw Text_ button on the right of the screen you can add some text to the PCB:

![](/tutorial/add-text.png)

Be sure to set the layer as "F.Silkscreen"! After that, it's time for some graphics. Grab a picture on google or draw one yourself, then open up Image Converter in KiCAD. Load a source image, and drag the black white threshold slider on the right to tweak the output.

![](/tutorial/art.png)

When your satisfied, check _Footprint_ as the output format, then click _Export to Clipboard_ and paste in the PCB window. If you see "G***" written on your drawing, just click on it and press delete. Now look at the beatiful drawing you have on your PCB!

![](/tutorial/silkscreen.png)

If it's too big or too little, press M and use the ruler tool to measure the desired size. Now go back to the converter window, then change the output size to the measured size and copy then paste again. Now we only need to generate the final fabrication file! Go back to the main KiCAD window, and click "Plugin and Content Manager".

![](/tutorial/pcb9.png)

Search up "Fabrication Toolkit" and install it. Now go back to the PCB editor, you should see a new button appear, click it and click generate

![](/tutorial/fabrication-toolkit.png)

Contgrats on making a PCB! You should find a .zip of your project in the "production" subfolder of your project's directory - thats the file that you need to send to the manufaturers! All that's left is to ship your project :D 

Make a Github repo, and add all your files in!

One last step before submission - please take a screenshot of your schematic, PCB, and 3D view (Press Control+3), then put it inside your README.md of your project! (Create a README if you don't have one.)

Now, head on to the How to Submit to go through the submission flow!
