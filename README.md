# Using 8*32 LED Dot-Matrix Display with Arduino

![LED DOT MATRIX](https://ardugeek-electronics-bucket.s3.amazonaws.com/media/products/MAX7219%2032x8%20Dot%20Matrix%204-in-1%20LED%20Display/screen_shot_2019-07-20_at_5.58.10_pm.jpg)

To control the MAX7219 display we will be using two awesome Arduino libraries.
MD_MAX72XX  MD_Parola
<p>The MD_Parola library can be used to create many different text animations like scrolling and sprite text effects. This library depends on the MD_MAX72XX library which implements the hardware functions of the LED matrix.

LED DOT Matrix Connections :

MAX7219 Display ----->	Arduino

<p>VCC      5V
<p>GND      GND
<p>DIN	    11 
<p>CS	      3 
<p>CLK	    13 
  
  
| LED Dot Matrix        | Arduino           | 
| ------------- |:-------------:| 
| col 3 is      | right-aligned | 
| col 2 is      | centered      |  
| zebra stripes | are neat      | 
