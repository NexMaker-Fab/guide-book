
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


### 3. 8x8 LED Matrix

Connect this 8*8 LED matrix with Arduino UNO
![](https://gitlab.com/picbed/bed/uploads/b728ea9bbdebc1ffbbbbac4ec3c0496d/88matrixled2.png)

[We use 18pin 8*8 LED Matrix in office example](https://www.arduino.cc/en/Tutorial/BuiltInExamples/RowColumnScanning),all of the LED would light.

The following show another method

```
int C[] = {2,7,A5,5,13,A4,12,A2};   

int R[] = {6,11,10,3,9,8,4,A3};     
  
unsigned char biglove[8][8] =       // image1 
{  
  0,0,0,0,0,0,0,0,  
  0,1,1,0,0,1,1,0,  
  1,1,1,1,1,1,1,1,  
  1,1,1,1,1,1,1,1,  
  1,1,1,1,1,1,1,1,  
  0,1,1,1,1,1,1,0,  
  0,0,1,1,1,1,0,0,  
  0,0,0,1,1,0,0,0,  
};  
  
unsigned char smalllove[8][8] =      //image2 
{  
  0,0,0,0,0,0,0,0,  
  0,0,0,0,0,0,0,0,  
  0,0,1,0,0,1,0,0,  
  0,1,1,1,1,1,1,0,  
  0,1,1,1,1,1,1,0,  
  0,0,1,1,1,1,0,0,  
  0,0,0,1,1,0,0,0,  
  0,0,0,0,0,0,0,0,  
};  
  
void setup()  
{  
   //define pinmode 
  for(int i = 0;i<8;i++)  
  {  
    pinMode(R[i],OUTPUT);  
    pinMode(C[i],OUTPUT);  
  }  
}  
  
void loop()  
{  
  for(int i = 0 ; i < 100 ; i++)        //loop 100 times  
  {  
    Display(biglove);                   //display image1  
  }  
  for(int i = 0 ; i < 50 ; i++)         //loop50 times  
  {     
    Display(smalllove);                 //display image2
  }  
}  
  
void Display(unsigned char dat[8][8])   //show function  
{  
  for(int c = 0; c<8;c++)  
  {  
    digitalWrite(C[c],LOW);
    for(int r = 0;r<8;r++)  
    {  
      digitalWrite(R[r],dat[r][c]);  
    }  
    delay(1);  
    Clear();  //clear 
  }  
}  
  
void Clear()                          //clear  
{  
  for(int i = 0;i<8;i++)  
  {  
    digitalWrite(R[i],LOW);  
    digitalWrite(C[i],HIGH);  
  }  
}

```

![](https://gitlab.com/picbed/bed/uploads/6b0188f98ecd1df6efa7f5716f97453a/1602658391370105.gif)

### 4. Segment display

![](https://gitlab.com/picbed/bed/uploads/f0e0576d4c2b0165315b4d0a6c81d234/5-1557192084.jpg)
*Remind:Example1 and example2 use same connection*
**Example1:4numbers**
```

int ledCount=8;

int segCount=4;

long previousMillis = 0;
const unsigned char dofly_DuanMa[10] = {0x3f,0x06,0x5b,0x4f,0x66,0x6d,0x7d,0x07,0x7f,0x6f};


int ledPins[] = {

12,8,5, 3, 2, 11, 6, 4, };

int segPins[]={13,10,9,7};

unsigned char displayTemp[4];

void setup() {



for (int thisLed = 0; thisLed < ledCount; thisLed++) {

pinMode(ledPins[thisLed], OUTPUT); }

for (int thisSeg = 0; thisSeg < segCount; thisSeg++) {

pinMode(segPins[thisSeg], OUTPUT);

}

}

void deal(unsigned char value){

for(int i=0;i<8;i++)

digitalWrite(ledPins[i],bitRead(value,i));

// !bitRead(value,i)

}

void loop() {

static unsigned int num;

static unsigned long lastTime=0;

if (millis() - lastTime >= 1000){

lastTime = millis();

//serialOutput();

num++;

}

displayTemp[0]=dofly_DuanMa[1]; 

displayTemp[1]=dofly_DuanMa[2];

displayTemp[2]=dofly_DuanMa[6];

displayTemp[3]=dofly_DuanMa[4];

static int i;

unsigned long currentMillis = millis();

if(currentMillis - previousMillis > 0) {

previousMillis = currentMillis;

deal(0);

for(int a=0;a<4;a++)

digitalWrite(segPins[a],1);

digitalWrite(segPins[i],0);

deal(displayTemp[i]);

i++;

if(i==4) 

i=0;

}

}


```

**Example2:timer**
```
int ledCount=8;

int segCount=4;

long previousMillis = 0;



const unsigned char dofly_DuanMa[10] = {0x3f,0x06,0x5b,0x4f,0x66,0x6d,0x7d,0x07,0x7f,0x6f};


int ledPins[] = {12,8,5, 3, 2, 11, 6, 4, };

int segPins[] = {13,10,9,7};

unsigned char displayTemp[4];

void setup() {


for (int thisLed = 0; thisLed < ledCount; thisLed++) {

pinMode(ledPins[thisLed], OUTPUT); }

for (int thisSeg = 0; thisSeg < segCount; thisSeg++) {

pinMode(segPins[thisSeg], OUTPUT);

}

}

void deal(unsigned char value){

for(int i=0;i<8;i++)

digitalWrite(ledPins[i],bitRead(value,i));

}

void loop() {

static unsigned int num;

static unsigned long lastTime=0;

if (millis() - lastTime >= 1000){

lastTime = millis();

//serialOutput();

num++;

}

displayTemp[0]=dofly_DuanMa[num/1000]; 

displayTemp[1]=dofly_DuanMa[(num%1000)/100];

displayTemp[2]=dofly_DuanMa[((num%1000)%100)/10];

displayTemp[3]=dofly_DuanMa[((num%1000)%100)%10];

static int i;

unsigned long currentMillis = millis();

if(currentMillis - previousMillis > 0) {

previousMillis = currentMillis;

deal(0);

for(int a=0;a<4;a++)

digitalWrite(segPins[a],1);

digitalWrite(segPins[i],0);//

deal(displayTemp[i]);

i++;

if(i==4) 

i=0;

}

    }

```



**Example3:Nixie tube**

![](https://gitlab.com/picbed/bed/uploads/bba1be4ffacfce45a9ebb29814e438af/20190716212343308.jpg)
```

int pin_a = 7;
int pin_b = 6;
int pin_c = 5;
int pin_d = 10;
int pin_e = 11;
int pin_f = 8;
int pin_g = 9;
int pin_p = 4;
		

int numTable[10][8] = {

//a  b  c  d  e  f  g  dp
{1, 1, 1, 1, 1, 1, 0, 0},     //0
{0, 1, 1, 0, 0, 0, 0, 0},     //1
{1, 1, 0, 1, 1, 0, 1, 0},     //2
{1, 1, 1, 1, 0, 0, 1, 0},     //3
{0, 1, 1, 0, 0, 1, 1, 0},     //4
{1, 0, 1, 1, 0, 1, 1, 0},     //5
{1, 0, 1, 1, 1, 1, 1, 0},     //6
{1, 1, 1, 0, 0, 0, 0, 0},     //7
{1, 1, 1, 1, 1, 1, 1, 0},     //8
{1, 1, 1, 1, 0, 1, 1, 0},     //9
};


void setup()
{
for (int i = 4; i <= 11; i++)
{
pinMode(i, OUTPUT); 
}
}

void loop()
{
for (int i = 0; i < 10; i++)
{
digitalWrite(pin_a, numTable[i][0]); 
digitalWrite(pin_b, numTable[i][1]); 
digitalWrite(pin_c, numTable[i][2]); 
digitalWrite(pin_d, numTable[i][3]); 
digitalWrite(pin_e, numTable[i][4]); 
digitalWrite(pin_f, numTable[i][5]); 
digitalWrite(pin_g, numTable[i][6]); 
digitalWrite(pin_p, numTable[i][7]); 
delay(200);
}

}

```
[Example3 reference from csdn](https://blog.csdn.net/TonyIOT/article/details/82347156)
### 5. Serve motor

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

### Stepper motor

More stepper motor information reference [Arduino.cc](https://www.arduino.cc/en/Reference/Stepper)
We can learn ULN 2003AN information in the following web:[Ti](https://www.ti.com/lit/ds/symlink/uln2003a.pdf?HQS=TI-null-null-digikeymode-df-pf-null-wwe&ts=1602728406149),[OCTOPART](https://datasheet.octopart.com/ULN2003AN-Texas-Instruments-datasheet-32624.pdf),
![](https://gitlab.com/picbed/bed/uploads/322791c3a9331fe315d359a2c974efbf/WX20201015-102518.png)
### Speaker
![](https://gitlab.com/picbed/bed/uploads/023f80978f9310c798cb7ab8d22246a6/Tone_Fritzing.png)

![](https://gitlab.com/picbed/bed/uploads/3668ee44de6e52ea85624dd9f43e42d4/Tone_Schematic.png)
```
void setup() {

}

void loop() {
  // turn off tone function for pin 8:
  noTone(8);
  // play a note on pin 6 for 200 ms:
  tone(6, 440, 200);
  delay(200);

  // turn off tone function for pin 6:
  noTone(6);
  // play a note on pin 7 for 500 ms:
  tone(7, 494, 500);
  delay(500);

  // turn off tone function for pin 7:
  noTone(7);
  // play a note on pin 8 for 300 ms:
  tone(8, 523, 300);
  delay(300);
}
```
Reference from [Arduino.cc](https://www.arduino.cc/en/Tutorial/BuiltInExamples/toneMelody)

### Relay

Soon



## Reference

* [Arduino.cc](https://www.arduino.cc/en/Reference/Stepper)
* [Tinkercad](https://www.tinkercad.com/)