---
layout: ../layouts/BaseLayout.astro
title: "Ordering your PCB"
show: True
order: 4
---

Once your design is done, it's time to actually get it manufactured!

### Exporting your Gerber and Drill files

The first thing is to export your PCB files for production! You need gerber (.gbr) and drill (.drl) files of your PCB no matter where you order from.

To get those files, I like using KiCad's Fabrication Toolkit plugin! On the main screen, click on Plugin and Content Manager.

![](https://cdn.hackclub.com/01a02095-a450-7b32-b551-f649ad3ec224/kicadexport1.png)

Then, search "Fabrication Toolkit", click Install, and then click Apply Pending Changes in the bottom right.

![](https://cdn.hackclub.com/01a02095-b65e-76f5-891b-eb1fb38e75d8/kicadexport2.png)

(If you're using PCBWay, you can also install PCBWay's fabrication toolkit!)

Then, go to your PCB editor, and click on the Fabrication Toolkit symbol.

![](https://cdn.hackclub.com/01a020a1-07b8-7552-b82c-b7adb32f74b1/kicadexport3.png)

It should generate a .zip file of your gerber and drill files!

*Alternative method: in the PCB editor, click File > Fabrication Outputs > Gerbers (.gbr...) > Plot. Remember to also generate Drill files!*

### Where do you order from?

Here are a couple of places:
- [JLCPCB](https://jlcpcb.com/) - I personally order from here! It's very cheap.
- [Seeed Studio](https://www.seeedstudio.com/fusion_pcb.html) - shipping may be cheaper here, depending on your country.
- [PCBWay](https://www.pcbway.com/orderonline.aspx)

Please order from the cheapest place!

### [JLCPCB](https://cart.jlcpcb.com/quote?stencilLayer=2&stencilWidth=100&stencilLength=100&stencilCounts=5&plateType=1) ordering guide

Upload the .zip of your gerber and drill files where it says *Add gerber file*! 

There are only two options you need to choose: the color of your PCB, and the surface finish. The color doesn't matter, so choose what you aesthetically want! For the surface finish, please choose LeadFree Hasl. ENIG is significantly more expensive :"D

![](https://cdn.hackclub.com/01a02080-a129-787d-af62-d2c2f1fa7fdd/jlcordering1.png)

Save to cart when you're done!

For shipping, choose Global Standard Direct Line.

![](https://cdn.hackclub.com/01a0209a-c33b-797b-a3fc-ab20a5914ee3/jlcordering2.png)

JLCPCB has many coupons if it's your first time using it - I'd recommend adding one of those!