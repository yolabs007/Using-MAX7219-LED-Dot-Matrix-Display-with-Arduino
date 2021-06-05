# Using 8*32 LED Dot-Matrix Display with Arduino


#### `Testing of Arduino`

* Test the Arduino Board by using blinking an In-Built LED (Below code) 

```C++
/*
  This Code is written by Rahul Sharma for Yolabs. 
This is the  simplest code possible to blink in build LED  
Turns inbuild LED on and off at diff frequency to chk your arduino IDE, Arduino and cable is working
Note: please check the port in case you have error while uploadig 
 www.yolabs.in - 2020
  
*/

// the setup function runs once when you press reset or power the board

void setup()
{
  pinMode(13,OUTPUT);
  Serial.begin(9600);
}

void loop()
{
    digitalWrite(13, HIGH);
    
    Serial.println("I am High");
    delay(3000); // Wait for 1000 millisecond(s)
    digitalWrite(13, LOW);
    Serial.println("I am Low");
    delay(3000);
 
}


```


![LED DOT MATRIX](https://ardugeek-electronics-bucket.s3.amazonaws.com/media/products/MAX7219%2032x8%20Dot%20Matrix%204-in-1%20LED%20Display/screen_shot_2019-07-20_at_5.58.10_pm.jpg)

To control the MAX7219 display we will be using two awesome Arduino libraries.
1. **MD_MAX72XX**  
2. **MD_Parola**

<p>The MD_Parola library can be used to create many different text animations like scrolling and sprite text effects. This library depends on the MD_MAX72XX library which implements the hardware functions of the LED matrix.

# LED DOT Matrix Connections :
  
  
| LED Dot Matrix        | Arduino           | 
| -------------         |:-------------:    | 
| VCC                   | 5V                | 
| GND                   | GND               |  
| DIN                   | 11                | 
| CS                    | 3                 |  
| CLK                   | 13                | 
  
  # Display Text - code :
  
  * In Below code, change the code where `myDisplay.print("Center")` to display whaterever text want shown on LED Matrix.
  * Change the Intensity Values ( 0 ~ 16 ) in below code to Brighten the Matrix Display.
  
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
  myDisplay.print("Center");         // Change  `Center` to display diferent text.
  delay(2000);
  myDisplay.setTextAlignment(PA_LEFT);
  myDisplay.print("Left");           // Change  `Left` to display diferent text.
  delay(2000);
  myDisplay.setTextAlignment(PA_RIGHT);
  myDisplay.print("Right");          // Change  `Right` to display diferent text.
  delay(2000);
  myDisplay.setTextAlignment(PA_CENTER);
  myDisplay.setInvert(true);
  myDisplay.print("Invert");          // Change  `Invert` to display diferent text.
  delay(2000);
}
  
  
```
 
  # Scroll Text - code : 
  
   * In Below code, change the code where `myDisplay.displayText( "YOLABS" )` to display whaterever text want shown on LED Matrix.
   * Change the Intensity Values ( 0 ~ 16 ) in below code to Brighten the Matrix Display.
  
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
  myDisplay.displayText("YOLABS", PA_CENTER, 100, 0, PA_SCROLL_LEFT, PA_SCROLL_LEFT);    // Change  `YOLABS` to display diferent text.
}

void loop() {
  if (myDisplay.displayAnimate()) {
    myDisplay.displayReset();
  }
}
  
```
