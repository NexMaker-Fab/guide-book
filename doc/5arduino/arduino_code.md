## 1.Basic Language Reference
### 1.1 Digital I/O

```
int ledPin = 13;  // LED connected to digital pin 13
int inPin = 7;    // pushbutton connected to digital pin 7
int val = 0;      // variable to store the read value

void setup() {
  pinMode(ledPin, OUTPUT);  // sets the digital pin 13 as output
  pinMode(inPin, INPUT);    // sets the digital pin 7 as input
}

void loop() {
  val = digitalRead(inPin);   // read the input pin
  digitalWrite(ledPin, val);  // sets the LED to the button's value
```

* 1.1.1digitalRead()
  * Description: Reads the value from a specified digital pin, either HIGH or LOW.
  * Syntax:digitalRead(pin)
  * Parameters(pin): the Arduino pin number you want to read
  * Returns:HIGH or LOW
  * Example Code(Sets pin 13 to the same value as pin 7, declared as an input.)



* 1.1.2digitalWrite()
  * Description:Write a HIGH or a LOW value to a digital pin.If the pin has been configured as an OUTPUT with pinMode(), its voltage will be set to the corresponding value: 5V (or 3.3V on 3.3V boards) for HIGH, 0V (ground) for LOW.If the pin is configured as an INPUT, digitalWrite() will enable (HIGH) or disable (LOW) the internal pullup on the input pin. It is recommended to set the pinMode() to INPUT_PULLUP to enable the internal pull-up resistor. See the Digital Pins tutorial for more information.If you do not set the pinMode() to OUTPUT, and connect an LED to a pin, when calling digitalWrite(HIGH), the LED may appear dim. Without explicitly setting pinMode(), digitalWrite() will have enabled the internal pull-up resistor, which acts like a large current-limiting resistor.
  * Syntax: digitalWrite(pin, value)
  * Parameters:
    * pin: the Arduino pin number.
    * value: HIGH or LOW.
  * Returns:Nothing
  * Example Code:The code makes the digital pin 13 an OUTPUT and toggles it by alternating between HIGH and LOW at one second pace.


* 1.1.3 pinMode()
  * Description:Configures the specified pin to behave either as an input or an output. See the Digital Pins page for details on the functionality of the pins.
  * Syntax:pinMode(pin, mode)
  * Parameters
    * pin: the Arduino pin number to set the mode of.
    * mode: INPUT, OUTPUT, or INPUT_PULLUP. See the Digital Pins page for a more complete description of the functionality.
  * Returns:Nothing


### 1.2 Analog I/O
* 1.2.1analogRead(pin)
    * Example Code:The code reads the voltage on analogPin and displays it.

  ```
  int analogPin = A3; // potentiometer wiper (middle terminal) connected to analog pin 3
                    // outside leads to ground and +5V
  int val = 0;  // variable to store the value read

  void setup() {
  Serial.begin(9600);           //  setup serial
  }

  void loop() {
  val = analogRead(analogPin);  // read the input pin
  Serial.println(val);          // debug value
  }
  ```

  * Description: Reads the value from the specified analog pin. Arduino boards contain a multichannel, 10-bit analog to digital converter. This means that it will map input voltages between 0 and the operating voltage(5V or 3.3V) into integer values between 0 and 1023. On an Arduino UNO, for example, this yields a resolution between readings of: 5 volts / 1024 units or, 0.0049 volts (4.9 mV) per unit. See the table below for the usable pins, operating voltage and maximum resolution for some Arduino boards.The input range can be changed using analogReference(), while the resolution can be changed (only for Zero, Due and MKR boards) using analogReadResolution().On ATmega based boards (UNO, Nano, Mini, Mega), it takes about 100 microseconds (0.0001 s) to read an analog input, so the maximum reading rate is about 10,000 times a second.

    ![](https://gitlab.com/picbed/bed/uploads/83bba1c5ee8f789279e32afc988395d9/WX20200415-094053_2x.png)

  * Syntax:analogRead(pin)
  * Parameters:pin: the name of the analog input pin to read from (A0 to A5 on most boards, A0 to A6 on MKR boards, A0 to A7 on the Mini and Nano, A0 to A15 on the Mega).
  * Returns:The analog reading on the pin. Although it is limited to the resolution of the analog to digital converter (0-1023 for 10 bits or 0-4095 for 12 bits). Data type: int.

* 1.2.2analogWrite(pin)
  * Description:Writes an analog value (PWM wave) to a pin. Can be used to light a LED at varying brightnesses or drive a motor at various speeds. After a call to analogWrite(), the pin will generate a steady rectangular wave of the specified duty cycle until the next call to analogWrite() (or a call to digitalRead() or digitalWrite()) on the same pin. 
![](https://gitlab.com/picbed/bed/uploads/06df60ca8eea67ff7eb5d52f8002a5ad/WX20200415-094509_2x.png)

  * Syntax:analogWrite(pin, value)
  * Parameters:pin: the Arduino pin to write to. Allowed data types: int.
  * value: the duty cycle: between 0 (always off) and 255 (always on). Allowed data types: int.
  * Returns:Nothing
  * Example Code:Sets the output to the LED proportional to the value read from the potentiometer.
 
  ```
  int ledPin = 9;      // LED connected to digital pin 9
  int analogPin = 3;   // potentiometer connected to analog pin 3
  int val = 0;         // variable to store the read value

  void setup() {
  pinMode(ledPin, OUTPUT);  // sets the pin as output
  }

  void loop() {
  val = analogRead(analogPin);  // read the input pin
  analogWrite(ledPin, val / 4); // analogRead values go from 0 to 1023, analogWrite values from 0 to 255
  }
  ```

 ### 1.3 Math
* 1.3.1 abs() 
  * Description:Calculates the absolute value of a number.
  * Syntax:abs(x)
  * Parameters  x: the number
  * Returns:  
    * x: if x is greater than or equal to 0.
    * -x: if x is less than 0.
* 1.3.2 constrain() 
  * Description:Constrains a number to be within a range.
  * Syntax:constrain(x, a, b)
  * Parameters
    * x: the number to constrain Allowed data types: all data types.
    * a: the lower end of the range. Allowed data types: all data types.
    * b: the upper end of the range. Allowed data types: all data types.
  * Returns
    * x: if x is between a and b.
    * a: if x is less than a.
    * b: if x is greater than b.
  * Example Code:The code limits the sensor values to between 10 to 150.
    
    ```
    sensVal = constrain(sensVal, 10, 150); 
    // limits range of sensor values to between 10 and 150

    ```

* 1.3.3max()/min() 
  * Description:Calculates the maximum( minimum) of two numbers.
  * Syntax:max(x, y)  /min(x,y)
  * Parameters
    * x: the first number. Allowed data types: any data type.
    * y: the second number. Allowed data types: any data type.
  * Returns
    * max:The larger of the two parameter values.
    * min:The larger of the two parameter values.
  * Example Code:The code ensures that sensVal is at least 20.
  
  ```
  sensVal = max(sensVal, 20);
  // assigns sensVal to the larger of sensVal or 20
  ```

* 1.3.4 pow()   
  * Description:Calculates the value of a number raised to a power. pow() can be used to raise a number to a fractional power. This is useful for generating exponential mapping of values or curves.
  * Syntax:pow(base, exponent)
  * Parameters
    * base: the number. Allowed data types: float.
    * exponent: the power to which the base is raised. Allowed data types: float.
  * Returns:The result of the exponentiation. Data type: double.
  * Example Code:Calculate the value of x raised to 
  
  `z = pow(x, y);`



* 1.3.5 sq() 
  * Description:Calculates the square of a number: the number multiplied by itself.
  * Syntax:sq(x)
  * Parameters x: the number. Allowed data types: any data type.
  * Returns:The square of the number. Data type: double.

* 1.3.6 sqrt() 
  * Description:Calculates the square root of a number.
  * Syntax:sqrt(x)
  * Parameters x: the number. Allowed data types: any data type.
  * Returns:The number’s square root. Data type: double.

### 1.4 Random Numbers
* Description:The random function generates pseudo-random numbers.
* Syntax
  * random(max)
  * random(min, max)
* Parameters
  * min: lower bound of the random value, inclusive (optional).
  * max: upper bound of the random value, exclusive.
* Returns:A random number between min and max-1. Data type: long.

### 1.5 Communication
* 1.5.1 Serial.begin()

    ```
    void setup() {
      Serial.begin(9600); // opens serial port, sets data rate to 9600 bps
    }
    void loop() {}

    ```
    Description:Sets the data rate in bits per second (baud) for serial data transmission. For communicating with Serial Monitor, make sure to use one of the baud rates listed in the menu at the bottom right corner of its screen. You can, however, specify other rates - for example, to communicate over pins 0 and 1 with a component that requires a particular baud rate.

    An optional second argument configures the data, parity, and stop bits. The default is 8 data bits, no parity, one stop bit.

* 1.5.2 Serial.write()

    ```
    void setup() {
     Serial.begin(9600);
    }

    void loop() {
      Serial.write(45); // send a byte with the value 45

      int bytesSent = Serial.write("hello");  //send the string "hello" and return the length of the string.
    }
    ```

    Description: Writes binary data to the serial port. This data is sent as a byte or series of bytes; to send the characters representing the digits of a number use the print() function instead.


* 1.5.3 Serial.print()




 Description:Prints data to the serial port as human-readable ASCII text. This command can take many forms. Numbers are printed using an ASCII character for each digit. Floats are similarly printed as ASCII digits, defaulting to two decimal places. Bytes are sent as a single character. Characters and strings are sent as is. 

  ```
  Serial.print(78) 
  ```
  Result :gives "78"

### 1.6 Time
 * delay()
  * Description:Pauses the program for the amount of time (in milliseconds) specified as parameter. (There are 1000 milliseconds in a second.)
  * Syntax:delay(ms)
  * Parameters: ms: the number of milliseconds to pause. Allowed data types: unsigned long.
  * Returns:Nothing
  * Example Code:The code pauses the program for one second before toggling the output pin.

    ```
    int ledPin = 13;              // LED connected to digital pin 13

    void setup() {
      pinMode(ledPin, OUTPUT);    // sets the digital pin as output 
    }

    void loop() {
      digitalWrite(ledPin, HIGH); // sets the LED on
      delay(1000);                // waits for a second
      digitalWrite(ledPin, LOW);  // sets the LED off
      delay(1000);                // waits for a second
    }
    ```

  we can also use  the following 3 commands

  * delayMicroseconds() 
  * micros() 
  * millis() 


## 2 OUTPUT

### 2.1 OUTPUT:LED
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



### 2.2. OUTPUT LCD displays

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

### 2.3 serve motor

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

## 3. Input
### 3.1 Input:switch
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


### 3.2 Input: air sensor
 We use MQ-2 air sensor to do this test

 ![](https://gitlab.com/picbed/bed/uploads/015c4cc84f7fe84d194f026fff4d20f9/WX20200415-152026_2x.png)
```
 void setup()
{
    Serial.begin(9600);
}
void loop()
{
    int val;
    val=analogRead(0);
    Serial.println(val,DEC);
    delay(100);
}
```


### 3.3 temperature sensor
![](https://gitlab.com/picbed/bed/uploads/39121a601bd52777197a4c9b5de46621/temperature_tmp36pinout.gif)
![](https://gitlab.com/picbed/bed/uploads/831b78bcdd7c99281cbcc60f55bf0b5d/TMP36GZ.jpg)

```
const int temperaturePin = 0;

void setup()
{ 
  Serial.begin(9600);
}

void loop()
{

  float voltage, degreesC, degreesF;

  voltage = getVoltage(temperaturePin);
  degreesC = (voltage - 0.5) * 100.0;
  degreesF = degreesC * (9.0/5.0) + 32.0;

  Serial.print("voltage: ");
  Serial.print(voltage);
  Serial.print("  deg C: ");
  Serial.print(degreesC);
  Serial.print("  deg F: ");
  Serial.println(degreesF);
   
  delay(1000); // repeat once per second (change as you wish!)
}

float getVoltage(int pin)
{

  return (analogRead(pin) * 0.004882814);
 
}
```

### 3.4  Input:Sharp GP2Y10



![](https://gitlab.com/picbed/bed/uploads/6f700260306bc7f920364993e5e7cd44/9770feae06.png
)

```
#define        COV_RATIO                           0.17           // (ug/m3) / mv
#define        NO_DUST_VOLTAGE         600            // mv
#define        SYS_VOLTAGE                     5000          // ADC参考电压    

/*
I/O define
*/
const int iled = 3;                                           //drive the led of sensor
const int vout = 0;                                           //analog input

/*
variable
*/
float density, voltage;
int   adcvalue;

/*
private function
*/
int Filter(int m)
{
  static int flag_first = 0, _buff[10], sum;
  const int _buff_max = 10;
  int i;
  
  if(flag_first == 0)
  {
    flag_first = 1;

    for(i = 0, sum = 0; i < _buff_max; i++)
    {
      _buff[i] = m;
      sum += _buff[i];
    }
    return m;
  }
  else
  {
    sum -= _buff[0];
    for(i = 0; i < (_buff_max - 1); i++)
    {
      _buff[i] = _buff[i + 1];
    }
    _buff[9] = m;
    sum += _buff[9];
    
    i = sum / 10.0;
    return i;
  }
}

void setup(void)
{
  pinMode(iled, OUTPUT);
  digitalWrite(iled, LOW);                                     //iled default closed
  Serial.begin(9600);                                          //send and receive at 9600 baud
}

void loop(void)
{
  /*
  get adcvalue
  */
  digitalWrite(iled, HIGH);
  delayMicroseconds(280);
  adcvalue = analogRead(vout);
  delayMicroseconds(40);
  digitalWrite(iled, LOW);
  
  adcvalue = Filter(adcvalue);
  
  /*
  covert voltage (mv)
  */
  voltage = (SYS_VOLTAGE / 1024.0) * adcvalue * 11;
  
  /*
  voltage to density
  */
  if(voltage >= NO_DUST_VOLTAGE)
  {
    voltage -= NO_DUST_VOLTAGE;
    density = voltage * COV_RATIO;
  }
  else
    density = 0;
    
  
  Serial.print("The current dust concentration is: ");
  Serial.print(density);
  Serial.print(" ug/m3\n");  
  
  delay(1000);
}
```

## Reference
* [Official tutorial](https://www.arduino.cc/en/Tutorial/BuiltInExamples)
* [How to start](https://www.arduino.cc/en/Guide/HomePage)
* [Examples from Libraries](https://www.arduino.cc/en/Tutorial/LibraryExamples)
* [Language Reference](https://www.arduino.cc/reference/en/)
