# node-neopixel-utils
A Node.js module that provides a set of NeoPixel (ws2812) utilities.

When we think of a NeoPixel, we see it as an LED with 24 bits of data that define
its color.  There are 8 bits for red, 8 bits for green and 8 bits for blue.  However,
we generally don't work with just one NeoPixel but instead work with a "strip" of them
where each NeoPixel is daisy-chained to the next one.  When we want to set the value of
one NeoPixel, we need to actually set the value of all of them as a single operation.
This means that we need to remember the "state" of all the pixels and that is where
this module comes into play.
 
The module exposes a function called "Strip" that, when called, returns a logical
representation of a strip of NeoPixels of a given length (count of pixels).  The
return is an object with methods upon it to get and set pixels that are then remembered
by the strip object.  When ready, we can then ask that object for a Buffer containing
the data for all the pixels.
 
The functions and properties exposed by the strip object are:

* `buffer` <Buffer> - A Buffer object representing the data of the pixels.
* `pixelCount` <Number> - The number of pixels in the strip.
* `setPixelColor(index, color)` - Set the pixel at the given index to the specified color.
* `getPixelColor(index)` - Return the color of the pixel at the given index.  The result
is an RGB array.
* `off()` - Set the colors of all pixels to off.
* `on(color)` - Set the color of all the pixels to the supplied color.
 
A color can be supplied in a few formats.  These include:
* `[R, G, B]` - A 3 number array where each number is between 0 and 255.
* `"#RRGGBB"` - A 6 character hex string
* `"blue"` - A CSS color name
* `"rgb(200, 200, 200)"` - A string representing and RGB color value
* `"hsl(360, 100%, 50%)"` - A string representing the HSL color value
