
## Arduino Input
### 1. Switch
We can use swith to control the circuit, in this case we use pin 7 as input port
![](https://gitlab.com/picbed/bed/uploads/e8692696c7583ae1fcd16918f94087d8/WX20200414-220404_2x.png)

```cpp
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


### 2.  Air sensor
 We use MQ-2 air sensor to do this test

 ![](https://gitlab.com/picbed/bed/uploads/015c4cc84f7fe84d194f026fff4d20f9/WX20200415-152026_2x.png)
```cpp
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


### 3. Temperature sensor
![](https://gitlab.com/picbed/bed/uploads/39121a601bd52777197a4c9b5de46621/temperature_tmp36pinout.gif)
![](https://gitlab.com/picbed/bed/uploads/831b78bcdd7c99281cbcc60f55bf0b5d/TMP36GZ.jpg)

```cpp
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

### 4.Sharp GP2Y10



![](https://gitlab.com/picbed/bed/uploads/6f700260306bc7f920364993e5e7cd44/9770feae06.png
)

```cpp
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



### 5. Ultrasonic sensor 

|Name|Parameter|
|----|----|
|Voltage|DC 5V|
|Current|15mA|
|Ultrasonic frequence|40KHz|
|Distance|20mm~4000mm|
|Precision|3mm|
|Degree|15|
|Signal|10us TTL|



##### Example 

```cpp
// circuit

/*
Arduino		SR04
5V		---	VCC
A0		---	Trig
A1		---	Echo
GND		---	GND
*/

// pin setting

#define TrigPin A0	
// __|^|_____________
// 10us or more HITH SIGNAL will drive it work for one time

#define EchoPin A1	
// ______|^^^^^^^^|__ 
// PULSE WIDTH stand for distance(the time of ultrasound transmit, both go and back)
// pulse width WILL NOT long than 38ms, it means timeout
// Distance = Speed x Time
// Speed of sound ~= 340m/s = 0.340mm/us

int count = 0;

long duration;
// PULSE WIDTH

void setup() {
    // set Serial communication
    Serial.begin(115200);
    // set pin mode
    pinMode(TrigPin, OUTPUT);
    pinMode(EchoPin, INPUT);
    // init pin
    digitalWrite(TrigPin, LOW);
    delay(1);
}

void loop() {
    Serial.println(count++);
    Serial.println(getDistance());
    Serial.println("");
    Serial.println("");
    delay(1000);
}

long getDistance() {
    // trig
    digitalWrite(TrigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(TrigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(TrigPin, LOW);
    // echo
    duration = pulseIn(EchoPin, HIGH); 	// unit: us
    return duration * 0.34029 / 2; 		// unit: mm
}

```
##### reference

[Arduino:HC-SR04  ultrasonic sensor](https://www.qutaojiao.com/8643.html)

[Arduino in W3CSCHOOL](https://www.w3cschool.cn/arduino/arduino_ultrasonic_sensor.html)

[Arduino PIR sensor](https://www.w3cschool.cn/arduino/arduino_pir_sensor.html)