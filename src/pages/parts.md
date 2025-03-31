---
layout: ../layouts/BaseLayout.astro
title: 'Learn about Parts'
show: True
order: 2
---

Note: In this tutorial we talk about the movement of electrons to simplify the conecept, but in real life they actually move in the opposite direction than what we say here.

In electronics, we deal with two main units: voltage (V), which is the difference of potential between two points (think of the force pushing electrons to go from one point to another), while current (I) is the amount of electrons passing through a given point.

In the beginner world, there is always a common ground, called VSS, GND or 0V. It's a point where there is no potential, so all the electrons want to go there. Thus if you connect a point that has 5V to GND, electrons will naturally flow from 5V to GND.

Now onto the components! All these come in the kit.

### Resistors
One of the fundamental parts of electrical design is resistors, which are used to limit the current flow. They are characterized by it's resistance, given by the formula R = V / I, which is also known as Ohm’s law.

If you put two resistors series, their resistance combine: It is equivalent to one resistor that has the resistance of the sum of the two original resistors. When two or more resistors are parallel, their total resistance is given by the formula 1/Rtotal = 1/R1 + 1/R2 + 1/R3 + ...

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