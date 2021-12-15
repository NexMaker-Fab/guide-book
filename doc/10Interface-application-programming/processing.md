

## [Processing](https://processing.org/)
[Processing is a flexible software sketchbook and a language for learning how to code within the context of the visual arts. Since 2001, Processing has promoted software literacy within the visual arts and visual literacy within technology. There are tens of thousands of students, artists, designers, researchers, and hobbyists who use Processing for learning and prototyping.](https://processing.org/)

## 1. Software download
[Dowload according to your PC's OS](https://processing.org/download/)

## [2. Languge](https://processing.org/examples/)

#### [2.1. The structure of language](https://processing.org/examples/setupdraw.html)
```

/**
 * Setup and Draw. 
 * The code in setup() is run once when the program starts.
 * The code inside the draw() function runs continuously from top to bottom until the program is stopped. The
 * Reference from https://processing.org/examples/setupdraw.html
 
 **/

int y = 180;
void setup() {
  size(640, 360);  // Size must be the first statement
  stroke(255);  // Set line drawing color to white
}

void draw() { 
  background(0);  // Clear the screen with a black background
  line(0, y, width, y); 
  y = y - 1; 
  if (y < 0) { 
    y = height;
  }
} 

```
#### [2.2. Shape](https://processing.org/examples/shapeprimitives.html)
```
/**
Reference from https://processing.org/examples/shapeprimitives.html

 **/
void setup(){
size(640, 360);
background(0);
noStroke();
}

void draw(){

fill(204);
triangle(18, 18, 18, 360, 81, 360);

fill(102);
rect(81, 81, 63, 63);

fill(204);
quad(189, 18, 216, 18, 216, 360, 144, 360);

fill(255);
ellipse(252, 144, 72, 72);

fill(204);
triangle(288, 18, 351, 360, 288, 360); 

fill(255);
arc(479, 300, 280, 280, PI, TWO_PI);    //arc(center x,centery,x diameter,y diameter,start angle,end angle)HALF_PI is π/2,QUARTER_PI is π/4,TWO_PI  is 2π
}
```

#### [2.3. The define of shape](https://processing.org/tutorials/color)

```
void setup() {
size(200,200);

}

void draw() 
{
  background(255,255,255); //Setting the background to white
  fill(237,28,36); //Setting the interior of a shape (fill)
  stroke(0,0,0); // Setting the outline (stroke) to black
  strokeWeight(5); //the define of bold
  point(23,34); //just the color of fill
  ellipse(40,50,20,40);  // center x,center y, widtd,heigh
  rect(60,60,30,30);   //x and y is the coordinate of the rectangle. w and h is rectangle's width and height.
}
```


#### [2.4.Input: Mouse](https://processing.org/examples/mousepress.html)

```
/**
 * Mouse Press. 
 * 
 * Move the mouse to position the shape. 
 * Press the mouse button to invert the color. 
 */

void setup() {
  size(640, 360);
  noSmooth();
  fill(126);
  background(255);
}

void draw() {
  if (mousePressed) {
    stroke(255);
  } else {
    stroke(0);
  }
  line(mouseX-66, mouseY, mouseX+66, mouseY);
  line(mouseX, mouseY-66, mouseX, mouseY+66); 
}
```

#### [2.5. GUI:button](https://processing.org/examples/button.html)

```
/**
 * Button. 
 * 
 * Click on one of the colored shapes in the 
 * center of the image to change the color of 
 * the background. 
 */
 
int rectX, rectY;      // Position of square button
int circleX, circleY;  // Position of circle button
int rectSize = 90;     // Diameter of rect
int circleSize = 93;   // Diameter of circle
color rectColor, circleColor, baseColor;
color rectHighlight, circleHighlight;
color currentColor;
boolean rectOver = false;
boolean circleOver = false;

void setup() {
  size(640, 360);
  rectColor = color(0);
  rectHighlight = color(51);
  circleColor = color(255);
  circleHighlight = color(204);
  baseColor = color(102);
  currentColor = baseColor;
  circleX = width/2+circleSize/2+10;
  circleY = height/2;
  rectX = width/2-rectSize-10;
  rectY = height/2-rectSize/2;
  ellipseMode(CENTER);
}

void draw() {
  update(mouseX, mouseY);
  background(currentColor);
  
  if (rectOver) {
    fill(rectHighlight);
  } else {
    fill(rectColor);
  }
  stroke(255);
  rect(rectX, rectY, rectSize, rectSize);
  
  if (circleOver) {
    fill(circleHighlight);
  } else {
    fill(circleColor);
  }
  stroke(0);
  ellipse(circleX, circleY, circleSize, circleSize);
}

void update(int x, int y) {
  if ( overCircle(circleX, circleY, circleSize) ) {
    circleOver = true;
    rectOver = false;
  } else if ( overRect(rectX, rectY, rectSize, rectSize) ) {
    rectOver = true;
    circleOver = false;
  } else {
    circleOver = rectOver = false;
  }
}

void mousePressed() {
  if (circleOver) {
    currentColor = circleColor;
  }
  if (rectOver) {
    currentColor = rectColor;
  }
}

boolean overRect(int x, int y, int width, int height)  {
  if (mouseX >= x && mouseX <= x+width && 
      mouseY >= y && mouseY <= y+height) {
    return true;
  } else {
    return false;
  }
}

boolean overCircle(int x, int y, int diameter) {
  float disX = x - mouseX;
  float disY = y - mouseY;
  if (sqrt(sq(disX) + sq(disY)) < diameter/2 ) {
    return true;
  } else {
    return false;
  }
}
```


```
/**
 * Arm. 
 * 
 * The angle of each segment is controlled with the mouseX and
 * mouseY position. The transformations applied to the first segment
 * are also applied to the second segment because they are inside
 * the same pushMatrix() and popMatrix() group.
*/

float x, y;
float angle1 = 0.0;
float angle2 = 0.0;
float segLength = 100;

void setup() {
  size(640, 360);
  strokeWeight(30);
  stroke(255, 160);//grey data and transparent data;
  
  x = width * 0.3;
  y = height * 0.5;
}

void draw() {
  background(0);
  
  angle1 = (mouseX/float(width) - 0.5) * -PI;
  angle2 = (mouseY/float(height) - 0.5) * PI;
  
  pushMatrix();
  segment(x, y, angle1); 
  segment(segLength, 0, angle2);
  popMatrix();
}

void segment(float x, float y, float a) {
  translate(x, y);
  rotate(a);
  line(0, 0, segLength, 0);
}

```





## 3. Processing communication with Arduino
#### 3.1 Using Procssing  to control Arduino
![](https://gitlab.com/picbed/bed/uploads/a5a0f850c9da291e0183bc4212d13edc/atp2.png)

**Arduino coding**
```
int redPin = 3;
int greenPin = 4;
int bluePin = 5;

int c = 0;

void setup()
{
  Serial.begin(9600);  
  pinMode(redPin,OUTPUT);
  pinMode(greenPin,OUTPUT);
  pinMode(bluePin,OUTPUT);
}

void loop()
{
  if(Serial.available());
  c = Serial.read();
  if (c == 97)  //a in ASCII is 97
  {
    digitalWrite(redPin,HIGH);   
    delay(500);
    digitalWrite(redPin,LOW); 
  }
  if (c == 98)  //b in ASCII is 98
  {
    digitalWrite(greenPin,HIGH);   
    delay(500);
    digitalWrite(greenPin,LOW);    
  }
  if (c == 99)  
  {
    digitalWrite(bluePin,HIGH);   
    delay(500);
    digitalWrite(bluePin,LOW);
  }
}

```
**Processing coding**
```
import processing.serial.*;
Serial port;

void setup(){
  port=new Serial(this,"COM5",9600); //Arduino's com
  size(600,200);
}

void draw(){
  fill(255,0,0);
  rect(50,50,100,100);
  
  fill(0,255,0);
  rect(250,50,100,100);
  
  fill(0,0,255);
  rect(450,50,100,100);  
}

void mouseClicked(){
  if((mouseX>=50)&(mouseX<=150)&(mouseY>=50)&(mouseY<=150))
  {
    println("red");
    port.write("a");
  }
  else if((mouseX>=250)&(mouseX<=350)&(mouseY>=50)&(mouseY<=150))
  {
    println("green");
    port.write("b");
  }
  else if((mouseX>=450)&(mouseX<=550)&(mouseY>=50)&(mouseY<=150))
  {
    println("blue");
    port.write("c");
  }
}

```


#### 3.2 Using Arduino  to control Processing
![](https://gitlab.com/picbed/bed/uploads/ae08dcc49e8b1cdb1ba769f379c9069c/pta.png)

**Arduino coding**
```
int upPin = 3;
int downPin = 4;
int leftPin = 5;
int rightPin = 6; //分别控制上下左右

int up1,down1,left1,right1;

void setup() {
  pinMode(upPin,INPUT_PULLUP);
  pinMode(downPin,INPUT_PULLUP);
  pinMode(leftPin,INPUT_PULLUP);
  pinMode(rightPin,INPUT_PULLUP);
  Serial.begin(9600);  //比特率设置为一致方可通信
}

void loop() {
  
  up1 = digitalRead(upPin);
  down1 = digitalRead(downPin);
  left1 = digitalRead(leftPin);
  right1 = digitalRead(rightPin);  //按下开关对应的模拟针脚电平会发送改变
  
  if(up1 == 0)
  {
    delay(500);
    Serial.write("a");
  }
  else if(down1 == 0)
  {
    delay(500);
    Serial.write("b");
  }
  else if(left1 == 0)
  {
    delay(500);
    Serial.write("c");
  }
  else if(right1 == 0)
  {
    delay(500);
    Serial.write("d");
  }
}
```

**Processing coding**

```
import processing.serial.*;
Serial port;
int a = 300;
int b = 300;  //ab为圆心的坐标

void setup(){
  size(600,600);
  background(200,200,200);
  fill(255,0,0);
  ellipse(a,b,30,30); 
  port = new Serial(this,"COM4",9600);
}

void draw()
{
  while(port.available()>0)
  {
    char input = port.readChar(); //read information from Arduino 
    switch(input)
    {
      case'a':      
      background(200,200,200);
      fill(255,0,0); 
      b -= 20; 
      ellipse(a,b,30,30); 
      break;
      
      case'b':      
      background(200,200,200);
      fill(255,0,0); 
      b += 20;
      ellipse(a,b,30,30);
      break;  
      
      case'c':      
      background(200,200,200);
      fill(255,0,0); 
      a -= 20;
      ellipse(a,b,30,30); 
      break;
      
      case'd':      
      background(200,200,200);
      fill(255,0,0); 
      a += 20;
      ellipse(a,b,30,30); 
      break;
      default:break;
    }
  }
}
```
**3Processing communication with Arduino reference from  [web](https://blog.csdn.net/weixin_45037820/article/details/95666523) **

## 4. Reference
* [Official website](http://www.processing.org)
* [English tutorial](https://www.youtube.com/channel/UCvjgXvBlbQiydffZU7m1_aw)
* [Chinese tutorial](https://space.bilibili.com/9004724/#/channel/detail?cid=39462)
* [Basic information](https://www.iqiyi.com/w_19rs7xqamt.html)
* [Open source case](http://www.openprocessing.org)
* [爱上Processing](http://product.dangdang.com/25097342.html)
* [Learning Processing](https://www.amazon.com/gp/product/0123944430/ref=as_li_ss_tl?ref_=nav_ya_signin&linkCode=sl1&tag=processing09-20&linkId=fb0eeedd8fb1016a790e83d538a1c030)
* [Nature of code](http://product.dangdang.com/1088027649.html)
* [Processing, second edition: A Programming Handbook for Visual Designers and Artists](https://www.amazon.com/Processing-Programming-Handbook-Designers-Artists/dp/026202828X/ref=pd_sbs_14_3/138-9470288-0889131?_encoding=UTF8&pd_rd_i=026202828X&pd_rd_r=8f1bcb45-4a4d-4af7-bf79-6402171eeddf&pd_rd_w=uu2rD&pd_rd_wg=IrIOR&pf_rd_p=d2a3ee7d-5d69-4331-b32f-a3ce40b5e0d3&pf_rd_r=AHJNDP88XYMEQZQ2834M&psc=1&refRID=AHJNDP88XYMEQZQ2834M)