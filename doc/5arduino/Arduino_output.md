
## OUTPUT

### 1. OUTPUT:LED
[Tinkercad](https://www.tinkercad.com/)(we can use autodesk account to signin)
We can use Tinkercad to draw the circuit,coding,even simulation.
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



### 2. OUTPUT LCD displays

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

### 3. Serve motor

![](https://gitlab.com/picbed/bed/uploads/bfe44b250cd86b93d92d6957812e12a2/sg0.png)
```
#include <Servo.h>
 
#define PIN_SERVO 10
Servo myservo;
 
void setup()
{
  myservo.attach(PIN_SERVO);
}
 
void loop()
{
  myservo.write(0);
  delay(1000);
  myservo.write(40);
  delay(1000);
  myservo.write(80);
  delay(1000);
  myservo.write(40);
  delay(1000);
  myservo.write(0);
  delay(1000);

}
```
