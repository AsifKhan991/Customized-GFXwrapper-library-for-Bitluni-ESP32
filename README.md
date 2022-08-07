# Customized-GFXwrapper-library-for-Bitluni-ESP32
First of all a HUGE thanks to [bitluni](https://github.com/bitluni) for creating such an [amazing library](https://github.com/bitluni/ESP32Lib) it saved me big time while doing a project.<br>
However, as of current version (0.3.4) the vga library doesn't have any method for rotating the display. This repository contains the edited GFxwrapper library and example where rotation and flipping of display is enabled.<br>
# Usage
Initiate a Gfxwrapper class  <br>
```C++
VGA3BitI vga;
GfxWrapper<VGA3BitI gfx(vga, 640, 480);
```
Then set the orientation of teh class wherever necessary:<br>
```C++
gfx.orientation = 90;
```
There are 6 types of roeintation that is supported:<br>
* object.orientation = 0    -> (default)actual orientation 
* object.orientation = 90   -> 90 degree clockwise rotation relative to actual
* object.orientation = 180  -> 180 degree clockwise rotation relative to actual
* object.orientation = 270  -> 270 degree clockwise rotation relative to actual
* object.orientation = -1   -> flip horizontally
* object.orientation = -2   -> flip vertically
# Notes
* Rotating the display causes your horizontal and vertic resolution to change. For example: if you have default resolution of 640 by 480 then rotating 90 degree clockwise will change your resolution to 480 by 640. So you have keep it in mind while displaying rotated graphics. please refer to the example sketch to understand how it works. 
* It is possible to set individual rotation for individual graphics objects in the display. For this just simply set the desired orientation before displaying the graphics and then just set the previous orientation.For exaample:
```C++
gfx.orientation = 270; //setting desired orientation before displaying
gfx.setCursor(320 , 240);
gfx.print("individual rotation"); //displaying sometihng (can be text or graphics)
gfx.orientation = 0; // revert baack to original orientation
```
* Although it is not implemented, tweaking a bit in the library it will also be possible to rotate to any arbitrary angles (i.e: 15, 129, 287 etc). The functionality lies in the drawPixel() function of the Gfxwrapper class.
# How the example sketch looks in display
![alt text](https://github.com/AsifKhan991/Customized-GFXwrapper-library-for-Bitluni-ESP32/blob/main/IMG_20220807_180029.jpg)
