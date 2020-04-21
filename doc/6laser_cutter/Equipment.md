
##3. Practice  in Fablab Shanghai 

In group working,My classmate [Xi.tingxia ](http://fabacademy.org/2018/labs/fablaboshanghai/students/xi-tingxia/) and I learn it in  Fablab Shanghai and do the basic practice.

####3.1The basic the condition of Laser cutter(troteclaser Speedy 300)

![](https://ws1.sinaimg.cn/large/006tNc79gy1foljx06ljsj30u0140ju3.jpg)

| Type | parameter | 
| -------- | -------- |
| Laser type | CO₂ laser |  
| Work area | 726 x 432 mm |  
|		 Max. workpiece height | 125 - 305 mm |
| Machine size | 1128 x 911 x 1054 mm |  
| Laser power | 10 - 120 watts |

####3.2.Design in AutoCAD
 * We design a demo which can check the best parameter(power and speed).So we design 5 pcs cutting demo(the power is 100%,90%,80%,70%,60%) and 5 pcs engraving demo(the power is 60%,50%,40%,30%,20%). The speed are 20mm/s,30mmmm/s,40mm/s,50mm/s,60mm/s,70mm/s;
	![](https://ws3.sinaimg.cn/large/006tNc79gy1folmn0cp59j30hf0gf3z3.jpg)
	![](https://ws4.sinaimg.cn/large/006tNc79gy1follypu90gj31hc0u0ahg.jpg)
 * We change the color to make sure the laser cutter software's requirment(JobControl require the color in design file the same as the RGB color in JobControl or the software can't red it)
	![](https://ws4.sinaimg.cn/large/006tNc79gy1follyjuf6vj31hc0u0k0j.jpg)

 * Then we output ["test.dxf"](http://a360.co/2FfR0Bh) file and it can edit in CorelDRAW
	![](https://ws1.sinaimg.cn/large/006tNc79gy1follyf69orj31hc0u0tgi.jpg)

####3.3.Load plywood
The thichness  in laser cutter is 3mm, and the honeycomb platform will hold the board and small waste material will drop down 
	![](https://ws1.sinaimg.cn/large/006tNc79gy1folofm8psoj30u0140ju3.jpg)

####3.4 Check the focus point
 We can rise the platform and slow down when the measure apparatus almost touch the plywood.We stop rising when measure apparatus  touch the plywood. 
	![](https://ws4.sinaimg.cn/large/006tNc79gy1folpg4kl2lj30u01400vg.jpg)
Then close the Lid and prepare cutting.

####3.5 Data translate
We would translate in CorelDRAW and then slice data to G-code

* In CorelDRAW,we import the ["test.dxf"](http://a360.co/2FfR0Bh) into CorelDRAW using the command File > Import (Ctrl+I).Then print the design
		![](https://ws3.sinaimg.cn/large/006tNc79ly1foln41z5epj30ka0bft9g.jpg)
		![](https://ws2.sinaimg.cn/large/006tNc79ly1folnepxcx2j30jv0h1tfu.jpg)
* In [Jobcontrol software](https://www.troteclaser.com/fileadmin/content/pdf/Laser_Machines/Laser_Software/JobControl-TEC-en.pdf), Add [test file](http://a360.co/2FfR0Bh) ,and reference (array1)
	![](https://ws3.sinaimg.cn/large/006tNc79gy1folo5o8yl6j31kw0uiqks.jpg)
* Click "eye button"(array2) to Show the content of test file
* Double click empty space in workingspace or "setting" (array 3) to setting parameter.Define the power and speed The Heart of JobControl®. Predefi ned settings for different standard materials help we achieve the best possible engraving and cutting results.In this test we use plywood 3mm thickness. In addition, we can also save and manage your own materials
	![](https://ws3.sinaimg.cn/large/006tNc79gy1folo4vo9nyj313i0oitng.jpg)
* Click Ready(array4)and operate the laser cutter
* Wait for several minutes (the fan and smoke filter will filte some waste smoke ),then open the lid and take out the demo
	![](https://ws3.sinaimg.cn/large/006tNc79gy1folos0wu5lj30u0140tbj.jpg)

Because the time is limit, so I continue do my working in our school's lab

## 4. Practice 2 in UNNC's PDM lab
I do it in our school(UNNC)'s PDM lab. I use [60w redsail CO2 Laser cutter](http://www.easycut.cn/) to do the second part of laser cutter practice
![](https://ws1.sinaimg.cn/large/006tNc79ly1folkol34a1j30v01201ky.jpg)
 The basic the condition of Laser cutter(redsail M900)

| Type | parameter | 
| -------- | -------- |
| Laser type | CO₂ laser |  
| Work area | 600x900 mm |  
| Max. workpiece height | - |
| Machine size | 1500x1060x1140mm |  
| Laser power | 60 watts |

#### 4.1 Test1:Parameter test 
I do it to finish fablab parameter test, becasue I didn't finish all of them and the machine is different,so I do it again.
![](https://ws1.sinaimg.cn/large/006tNc79ly1fom86sn4ewj31kw16oe82.jpg)
![](https://ws4.sinaimg.cn/large/006tNc79gy1fom860y9o2j31kw16oe82.jpg)
![](https://ws2.sinaimg.cn/large/006tNc79ly1fom88hha30j31kw16o1kz.jpg)

The result is the following:

| Material | Thickness | Cutting | Power(%)| Speed(mm/s)| Engraving | Power(%)| Speed(mm/s)| 
| -------- | -------- | -------- |-------- | -------- | -------- | -------- | -------- |  
| Plywood | 1.0mm | Cutting |80 | 35 | Engraving | 20 | 80 | 
| Plywood | 2.0mm | Cutting |80 | 30 | Engraving | 20 | 80 |  
| Plywood | 3.0mm | Cutting |80 | 20 | Engraving | 20 | 80 |
| Cardboard | 1.0mm | Cutting |60 | 40 | Engraving | 20 | 80 |
| Cardboard | 1.5mm | Cutting |90 | 30 | Engraving | 20 | 80 | 
| Cardboard | 3.0mm | Cutting |100 | 20 | Engraving | 20 | 80 | 
| ABS | 1.0mm | Cutting |60 | 20 | Engraving | 10 | 80 | 
| Acrylic | 1.0mm | Cutting |100 | 30 | 1 | 1 | 1 |
| Acrylic | 2.0mm | Cutting |90 | 25 | 1 | 1 | 1 |
| Acrylic | 3.0mm | Cutting |100 | 18 | 1 | 1 | 1 |  

  

####4.2 Test2:Kelf test 
![](https://ws3.sinaimg.cn/large/006tNc79gy1fom74tgjutj31kw23vb29.jpg)
I use this test to make sure the kelf,In design model ,the rectange is 10x10mm

  ![](https://ws3.sinaimg.cn/large/006tNc79gy1fqs53z5tdsj313d0hk45g.jpg)
And the ```kelf=(110-107.6)/(11+1)=0.2mm```


####4.3 Test3:Engraving effect
According to test2, the parameter I use in this test is (speed 20mm/s, power 80%)
![](https://ws1.sinaimg.cn/large/006tNc79gy1fom76xepssj31kw16onpd.jpg)


####4.4  Press-fit construction kit(parameter design)
* Design 3D model in Fusion 360
 the basic shape is Hexagonal. Then made a connection method(in this part I didn't add kelf),and I would add it in Autodesk CAD.

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fqt96tg3vqj31540xcdp9.jpg)


I need to consider the kelf, so I use parameter design to update it as following:


![](https://ws1.sinaimg.cn/large/006Yi1XRgy1fs3lwu7kiqj31hc0u0wke.jpg)
![](https://ws1.sinaimg.cn/large/006Yi1XRgy1fs3lwuhb3vj30y70kl3zy.jpg)

The equation is the following:

![](https://ws1.sinaimg.cn/large/006Yi1XRgy1fs3lwuqbv1j31hc0u041k.jpg)


* Input in CAD[(reference the document in week3_computer_aided_design/3D_Design_Fusion360-Drawing)](http://fabacademy.org/2018/labs/fablaboshanghai/students/bob-wu/Fabclass/week3_computer_aided_design/3D_Design_Fusion360.html)
* Check the kelf again ,I choice the kelf 0mm, and 0.2mmm and after assembly it ,the left part(kelf 0.2mm) is good ,and the result verify the kelf in "4.2 Test2:Kelf test "
 ![](https://ws1.sinaimg.cn/large/006tKfTcgy1fqt9p9ixqqj31dn2561l0.jpg)
* According the above experience, I design the following 6 kinds of model
  ![](https://ws3.sinaimg.cn/large/006tKfTcgy1fqt9ydv14nj30wz0l0176.jpg)
* Use laser cutter to cut the board and take it out 
  ![](https://ws3.sinaimg.cn/large/006tKfTcgy1fqta0esxzoj31400u0dja.jpg)
  
   <iframe width="560" height="315" src="https://www.youtube.com/embed/kWGHEXc749Y" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
* Assembly 1: Flat shape
![](https://ws3.sinaimg.cn/large/006tKfTcgy1fqtack8tqej31kw16okjv.jpg)
I use four kinds of model to assemble them together and it make several different kinds of sharpe. the above picture is 4 kinds of assembly case
* Assembly 2: 3D model
 ![](https://ws4.sinaimg.cn/large/006tKfTcgy1fqtackr5h4j30u0140tcv.jpg)
 I use all of the model to assemble them together, and the above picture is a test in 3D model.
 
 In future, I would optimize the structure of the basic model to improve the following aspect
 * Compare different material to find better one (the plywood is easy to broken)
 * Optimize plug structure and enhance the strength
 * Design another plug method and make it has more opportunity to connect them together

#### 4.5 Penbox Practice
The design is finish in [Fusion page](http://fabacademy.org/2018/labs/fablaboshanghai/students/bob-wu/Fabclass/week3_computer_aided_design/3D_Design_Fusion360.html)

* Machine ready
	* Turn on Chiller unit, allow 10minutes stabilization before running it
	* Release top ’Stop’ button
	* Unlock interlock
	* Switch on red side ’ On’ switch
	* Insert material&clamp
	* Close safety enclosure
	* Switch on Infrared switch
	* Plug in compressor and turn on Extractor fan

*  Data :Insert key  and start up software and translate data from pc to laser cutter
	* I use the design data from fusion 360 last time I design.So I would download the data from Sheet1.dxf-sheet6.dxf
	* Import data:Open software(easycutter),then `file - import- data(sheet1.dxf-sheet6.dxf)`
	![](https://ws1.sinaimg.cn/large/006tNc79ly1fom3cnjyzvj30zk0sgwpq.jpg)

* Machine operating
	* Test the profile
	* Switch on Laser switch
	* Press ‘Start’ on machine to process
	* After cutting has finished, turn off Laser switch
	* Open safety enclosure and remove parts

*  Stop machine
	* Turn off Extractor fan and Unplug Compressor
	* Switch off infrared switch
	* Depress top ‘Stop’ switch
	* Lock interlock
	* Switch off red side switch
	* Turn off chiller unit

The following is the picture to show the condition of laser cutter
![](https://ws3.sinaimg.cn/large/006tNc79gy1fof11ggndhj31kw23ve81.jpg)
![](https://ws3.sinaimg.cn/large/006tNc79gy1fof11c2nmwj31kw16o1ky.jpg)
![](https://ws2.sinaimg.cn/large/006tNc79gy1fof1168vhgj31kw16o1ky.jpg)
![](https://ws2.sinaimg.cn/large/006tNc79gy1fof110jusqj31kw23vx6p.jpg)
![](https://ws2.sinaimg.cn/large/006tNc79gy1fof10vimhkj31kw23vnpd.jpg)



***
####Attachent: Laser cutter design data

1. [test.dxf](http://a360.co/2FfR0Bh)
2. [sheet1.dxf-sheet6.dxf](http://a360.co/2GqvwRm)
3. [Assembly model in fusion](https://a360.co/2r6WJmN)








