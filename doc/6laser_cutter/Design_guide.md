

## 1.The basic the condition of Laser cutter(HX960)

|Product|HX960      | 
| ------------- |-----:|	
|Working area|900*600mm|
|Machine size |1500*1200*1100mm    | 
| Engraving speed|0-600mm/s|   	
| Laser power|80W  |
|Resolution ratio|0.025mm|
|The min word|Chinese Character2mm /letter1mm|
|Power|AC220V±10%,50HZ,<2500W|
|Formate|AI, BMP、GIF、JPEG、PCX、TGA、CDR、DWG、TIFF、PLT、DXF|
	

## 2.Power and speed
In this part ,we use 2mm transparent acrylic.

 * We design a demo which can check the best parameter(power and speed).So we design 9 pcs cutting demo(the power is 90%,80%,70%,60%,50%,40%,30%,20%,10%). The speed are 10mm/s, 20mm/s,30mmmm/s,40mm/s,50mm/s,60mm/s;

 * We change the color to make sure the laser cutter software's requirment

![](https://gitlab.com/picbed/bed/uploads/ebe5beac6cd8304960a49adb79e8c2f6/WechatIMG102.png)

Then update to machine and process, we get the following result

![](https://gitlab.com/picbed/bed/uploads/97e7e00d30aa0f6cc81bfc4f410bc357/WechatIMG105.jpeg)
After analysis, we can get the following result.


| Power\Speed| 10 | 20 | 30| 40| 50 | 60| 
| -------- | -------- | -------- |-------- | -------- | -------- | -------- | -------- |  
| 10 | N | N |N | N | N | N| N | 
| 20 |Y | N |N | N | N | N| N | 
| 30| Y | Y |N | N | N | N| N | 
| 40| Y | Y |N | N | N | N| N |
| 50| Y | Y |Y| N | N | N| N |
| 60 |  Y | Y |Y| N | N | N| N |
| 70 |  Y | Y |Y| N | N | N| N |
| 80 |  Y | Y |Y| N | N | N| N |
| 90 |  Y | Y |Y| N | N | N| N |
***Remind:This table for 2mm transparent acrylic***
In future,we would update more different kinds material and thickness.


## 3. Kerf


![](https://gitlab.com/picbed/bed/uploads/4e42be41dfca878f1703ae3525a82420/kerfdesign.png)
In this part ,we would test the kerf(the diameter of laser).Obviously ,the laser has diameter.We can use 10 rectange to measure it.The width of rectange is 5mm.


![](https://gitlab.com/picbed/bed/uploads/a9fda7c135f66cdd45bbf8a6a0ede412/laserpoint.png)

The circle is the diameter of laser




![](https://gitlab.com/picbed/bed/uploads/9012f42584bd8ea2c9cce67918937f15/WechatIMG91.jpeg)

After process, we measure the size is 48.06mm,so the kerf is 

kerf= (50-48.06)/20=0.097mm









## Reference

1. [test.dxf](http://a360.co/2FfR0Bh)
2. [sheet1.dxf-sheet6.dxf](http://a360.co/2GqvwRm)
3. [Assembly model in fusion](https://a360.co/2r6WJmN)


