# Using 8*32 LED Dot-Matrix Display with Arduino

![LED DOT MATRIX](https://ardugeek-electronics-bucket.s3.amazonaws.com/media/products/MAX7219%2032x8%20Dot%20Matrix%204-in-1%20LED%20Display/screen_shot_2019-07-20_at_5.58.10_pm.jpg)

To control the MAX7219 display we will be using two awesome Arduino libraries.
MD_MAX72XX  MD_Parola
<p>The MD_Parola library can be used to create many different text animations like scrolling and sprite text effects. This library depends on the MD_MAX72XX library which implements the hardware functions of the LED matrix.

# LED DOT Matrix Connections :
  
  
| LED Dot Matrix        | Arduino           | 
| -------------         |:-------------:    | 
| VCC                   | 5V                | 
| GND                   | GND               |  
| DIN                   | 11                | 
| CS                    | 3                 |  
| CLK                   | 13                | 
  
```C++ 
  
// Include the required Arduino libraries:
#include <MD_Parola.h>
#include <MD_MAX72xx.h>
#include <SPI.h>

// Define hardware type, size, and output pins:
#define HARDWARE_TYPE MD_MAX72XX::FC16_HW
#define MAX_DEVICES 4
#define CS_PIN 3

// Create a new instance of the MD_Parola class with hardware SPI connection:
MD_Parola myDisplay = MD_Parola(HARDWARE_TYPE, CS_PIN, MAX_DEVICES);


void setup() {
  // Intialize the object:
  myDisplay.begin();
  // Set the intensity (brightness) of the display (0-16):
  myDisplay.setIntensity(0);
  // Clear the display:
  myDisplay.displayClear();
}

void loop() {
  myDisplay.setTextAlignment(PA_CENTER);
  myDisplay.print("Center");
  delay(2000);
  myDisplay.setTextAlignment(PA_LEFT);
  myDisplay.print("Left");
  delay(2000);
  myDisplay.setTextAlignment(PA_RIGHT);
  myDisplay.print("Right");
  delay(2000);
  myDisplay.setTextAlignment(PA_CENTER);
  myDisplay.setInvert(true);
  myDisplay.print("Invert");
  delay(2000);
}
```
  
```C++ 
// Include the required Arduino libraries:
#include <MD_Parola.h>
#include <MD_MAX72xx.h>
#include <SPI.h>

// Define hardware type, size, and output pins:
#define HARDWARE_TYPE MD_MAX72XX::FC16_HW
#define MAX_DEVICES 4
#define CS_PIN 3

// Create a new instance of the MD_Parola class with hardware SPI connection:
MD_Parola myDisplay = MD_Parola(HARDWARE_TYPE, CS_PIN, MAX_DEVICES);

void setup() {
  // Intialize the object:
  myDisplay.begin();
  // Set the intensity (brightness) of the display (0-16):
  myDisplay.setIntensity(0);
  // Clear the display:
  myDisplay.displayClear();
  myDisplay.displayText("YOLABS", PA_CENTER, 100, 0, PA_SCROLL_LEFT, PA_SCROLL_LEFT);
}

void loop() {
  if (myDisplay.displayAnimate()) {
    myDisplay.displayReset();
  }
}
  
  ```
