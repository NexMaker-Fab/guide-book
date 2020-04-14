## 1. [Official tutorial](https://www.arduino.cc/en/Tutorial/BuiltInExamples)


## 2.OUTPUT:LED

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
[Thinkercad](https://www.tinkercad.com/)(we can use autodesk account to signin)
We can use Thinkercad to drawing the circuit,coding,even simulation.
![](https://gitlab.com/picbed/bed/uploads/7d11837cdd18f5823c819aed39d3f9f5/1586871622107.jpg)
![](https://gitlab.com/picbed/bed/uploads/e864b069379a90bf83f9521268adfd73/Screen_Shot_2020-04-14_at_21.38.14.png)

## Input:switch
