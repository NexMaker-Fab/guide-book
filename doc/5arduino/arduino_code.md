## 1. [Official tutorial](https://www.arduino.cc/en/Tutorial/BuiltInExamples)


## 2.OUTPUT:LED
[Thinkercad](https://www.tinkercad.com/)(we can use autodesk account to signin)
We can use Thinkercad to drawing the circuit,coding,even simulation.
![](https://gitlab.com/picbed/bed/uploads/7d11837cdd18f5823c819aed39d3f9f5/1586871622107.jpg)
![](https://gitlab.com/picbed/bed/uploads/e864b069379a90bf83f9521268adfd73/Screen_Shot_2020-04-14_at_21.38.14.png)

```
int LED1=12;
int LED2=13;
void setup()
{ 
  pinMode(LED1, OUTPUT); 
  pinMode(LED2, OUTPUT);   
}
void loop()
{
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,LOW);
    delay(1000);
    digitalWrite(LED2,HIGH);
    digitalWrite(LED1,LOW);
    delay(1000);
}
```



## 2. OUTPUT LCD displays

![](https://gitlab.com/picbed/bed/uploads/f0a8abdb86a3dcc3fee68b1f7dc3af5b/lcd_photo.png)
![](https://gitlab.com/picbed/bed/uploads/b3403ee8256dd4ce28c61e31719b3377/LCD_Base_bb_Fritz.png)
![](https://gitlab.com/picbed/bed/uploads/1330716fffb7ce1d6e07ac6446c25863/LCD_Base_bb_Schem__1_.png)


```
/*
  LiquidCrystal Library - Hello World

 Demonstrates the use a 16x2 LCD display.  The LiquidCrystal
 library works with all LCD displays that are compatible with the
 Hitachi HD44780 driver. There are many of them out there, and you
 can usually tell them by the 16-pin interface.

 This sketch prints "Hello World!" to the LCD
 and shows the time.

  The circuit:
 * LCD RS pin to digital pin 12
 * LCD Enable pin to digital pin 11
 * LCD D4 pin to digital pin 5
 * LCD D5 pin to digital pin 4
 * LCD D6 pin to digital pin 3
 * LCD D7 pin to digital pin 2
 * LCD R/W pin to ground
 * LCD VSS pin to ground
 * LCD VCC pin to 5V
 * 10K resistor:
 * ends to +5V and ground
 * wiper to LCD VO pin (pin 3)

 Library originally added 18 Apr 2008
 by David A. Mellis
 library modified 5 Jul 2009
 by Limor Fried (http://www.ladyada.net)
 example added 9 Jul 2009
 by Tom Igoe
 modified 22 Nov 2010
 by Tom Igoe

 This example code is in the public domain.

 http://www.arduino.cc/en/Tutorial/LiquidCrystal
 */

// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("hello, world!");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  // print the number of seconds since reset:
  lcd.print(millis() / 1000);
}

```


Reference from [arduino cc](https://www.arduino.cc/en/Tutorial/HelloWorld)


## Input:switch
We can use swith to control the circuit, in this case we use pin 7 as input port
![](https://gitlab.com/picbed/bed/uploads/e8692696c7583ae1fcd16918f94087d8/WX20200414-220404_2x.png)

```
const int LED1=12;
const int LED2=13;
int val=0; 
void setup()
{ 
  pinMode(LED1, OUTPUT); 
  pinMode(LED2, OUTPUT); 
  pinMode(7, INPUT);     
}
void loop(){
val=digitalRead(7);
  if(val==HIGH)
{
    digitalWrite(LED1,HIGH);
    digitalWrite(LED2,LOW);
}
else
{ 
    digitalWrite(LED2,HIGH);
    digitalWrite(LED1,LOW);  
}
delay(1000);
}
```


## Input:Sensor (Sharp GP2Y10 )



![](https://gitlab.com/picbed/bed/uploads/6f700260306bc7f920364993e5e7cd44/9770feae06.png
)

```
/*
Standalone Sketch to use with a Arduino UNO and a
Sharp Optical Dust Sensor GP2Y1010AU0F
/**user define**/ int voutPin = A0; 
//Connect Vo of dust sensor Vo to Arduino A0 pin int ledPin = 2; 
//Connect LED(3pin) of dust sensor to Arduino D2 pin
*/
/**system define**/ 

int samplingTime = 280; 
int deltaTime = 40; 
int sleepTime = 9680; 
int voMeasured = 0; 
float calcVoltage = 0; 
float dustDensity = 0;


void setup(){

 Serial.begin(9600);
 pinMode(ledPin,OUTPUT);

}


void loop(){

 digitalWrite(ledPin,LOW); // power on the LED
 delayMicroseconds(samplingTime);

 voMeasured = analogRead(voutPin); // read the dust value

 delayMicroseconds(deltaTime);
 digitalWrite(ledPin,HIGH); // turn the LED off
 delayMicroseconds(sleepTime);

 // 0 - 5V mapped to 0 - 1023 integer values
 // recover voltage
 calcVoltage = (float)voMeasured * (5.0 / 1024.0);

 // linear eqaution taken from http://www.howmuchsnow.com/arduino/airquality/
 // Chris Nafis (c) 2012
 if ( calcVoltage >= 0.6 )
 {
     dustDensity = 0.17 * calcVoltage - 0.1;
 }
 else
 {
     dustDensity = 0;
 }

 Serial.print("Raw Signal Value (0-1023): ");
 Serial.print(voMeasured);

 Serial.print(" - Voltage: ");
 Serial.print(calcVoltage);
 Serial.print("V");

 Serial.print(" - Dust Density: ");

 if( calcVoltage > 3.5 )
 {
    Serial.print(">");  // unit: mg/m3
 }
 
 Serial.print(dustDensity);
 Serial.println(" mg/m3");

 delay(1000);
} 
```