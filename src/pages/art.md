---
layout: ../layouts/BaseLayout.astro
title: "PCB Art"
show: True
order: 3.5
---

Here's how to add art and polish to your PCB!

## Rounding your edge corners

In your PCB editor, right click on your Edge.Cuts outline > Shape Modification > Fillet Lines! 

You can choose how much you want to round it after. Note that this will turn your polygon into a bunch of lines. PCBs are sharp, so you should definitely round your corners when possible.

![](https://cdn.hackclub.com/01a01fa9-2628-73aa-b0ed-6efa9563aa09/filletoutline2.png)

## Custom shape outlines

If your shape has mostly flat lines, I'd recommend using the polygon tool on the sidebar.

Otherwise, for more organic shapes, I use Figma to make a vector SVG of the outline, then import it into KiCad.

Go to File > Import > Graphics, and a pop up wil open. 

![](https://cdn.hackclub.com/01a01fc2-f55e-7f10-ba3e-2e9b1b855c06/importgraphics.png)

Make sure you're importing it onto the Edge.Cuts layer!

You will probably need to change the Import Scale for it to show up in the right size. I usually just spam import until I get the scale right :"D

![](https://cdn.hackclub.com/01a01fc3-04ea-79e3-af88-992f9e44f0c5/importgraphics2.png)

## Custom holes 

Separately from your outline, import an SVG into your Edge.Cuts layer!

You can also make a normal shaped hole by using the polygon tool on the Edge.Cuts layer. Make sure to close your outline!

For circular keychain holes / screw holes, you can get those by pressing A, then choosing a MountingHole footprint.

## Silkscreen art

I'd recommend drawing art on any raster art software - I use Procreate, but [Krita](https://krita.org/en/) and [Aseprite](https://github.com/aseprite/aseprite/blob/main/INSTALL.md) are both free and good! *(You will need to compile Aseprite yourself.)* Export what you've drawn as a PNG.

To get a PNG into silkscreen in KiCad, open the Image Converter!

![](https://cdn.hackclub.com/01a01fd4-bb57-79ff-8d6d-0234fdaf8f3f/kicadimage1.png)

Click on "Load Source Image" to get your image into the editor. Then, change the size, adjust the black/white threshold until the image shows up how you want it, and make sure it's set as a footprint on the F.Silkscreen layer!

After you're done, click on Export to Clipboard, and you can paste it straight into the PCB editor. Remember to delete the label :D

![](https://cdn.hackclub.com/01a01fe0-302e-7760-a699-c350aa8ac2dd/kicadimage2.png)

Silkscreen is the white stuff printed on PCBs! They're used by default for text, but you can also do a lot more things with it.

Everything white below is an example of art/text I drew in Procreate and then imported into KiCad on a PCB! 

![](https://cdn.hackclub.com/01a01fea-ac96-78c0-9019-af38009acf94/silkscreenexample.png)

## Copper art

Go back into the Image Converter. Instead of exporting as F.Silkscreen, export it twice - once as F.Cu, and once as F.Mask! 

![](https://cdn.hackclub.com/01a01ff9-fb83-7565-b5d2-61f7ac7fb92a/kicadcopper.png)

Put both into your PCB editor, overlapped. I've slightly stagnated it here so that you can see that the overlap is what exposes the copper layer.

If you click on the 3D viewer, it should show up as gold!

![](https://cdn.hackclub.com/01a02003-0e01-74a9-b497-243a47405594/kicadcopper2.png)

![](https://cdn.hackclub.com/01a02003-1ce8-78a9-b8a2-ea18a10f0a20/kicadcopper3.png)

When you order a PCB, you can choose this to be silver (HASL) or gold (ENIG). Since ENIG is ~20 USD more expensive, you are expected to order with silver, unless your PCB requires the better specs.

## FR4 art

FR4 is the semi-translucent fiberglass material that PCBs have on their inside! 

The yellow-ish eyes and ears below are the FR4 exposed. It lets backlit light shine through: 

![](https://cdn.hackclub.com/01a0200e-595b-7b9c-a445-921919c4b955/kicadfr4.png)

So you can make some pretty cool things by having LEDs on the PCB that shine through! Kai's [badge](https://github.com/KaiPereira/Alchemical-Cosmological-Badges) is a great example:

![](https://private-user-images.githubusercontent.com/88850028/631512363-6faa6783-c593-44d4-8d61-3aee0b9c9191.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3ODcyNDQ2MzEsIm5iZiI6MTc4NzI0NDMzMSwicGF0aCI6Ii84ODg1MDAyOC82MzE1MTIzNjMtNmZhYTY3ODMtYzU5My00NGQ0LThkNjEtM2FlZTBiOWM5MTkxLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjA4MjAlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYwODIwVDE2NDUzMVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTQ0NTBiN2JmNDRkMjBhMDE5NDM4Y2M1OTIxNWZhZDIyNWE4ZjZiYjczOTZjOGI0MmZhOWVjNjQ5YWJkODdkMDcmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.XriXMU7GB9ByN7sKx2OAi9sWKVyIMJK8q1ZZs0bzcpg)

In order to expose the FR4, export it as F.Mask.

![](https://cdn.hackclub.com/01a0201c-5d50-7ee1-b3cb-de98124074fa/kicadfr42.png)

Note that you need expose the FR4 on both sides in order to shine LEDs through! That means you need to paste in a second, flipped footprint of the mask, and then press F to flip it to B.Mask.

It should show up as a brown-ish color in the 3D viewer:

![](https://cdn.hackclub.com/01a0201e-52a6-78d2-95ea-e9d9fad8897d/kicadfr43.png)

Let @acon know if you have any questions of if there's anything you'd like to know!