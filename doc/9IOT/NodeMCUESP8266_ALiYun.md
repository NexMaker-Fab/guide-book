## 1. Prepare

* Hardware: NodeMCU(In this example we choice [NodeMCU CP2102](https://item.taobao.com/item.htm?spm=a1z09.2.0.0.271a2e8ddxUY1V&id=540886181835&_u=e1kvrthkacf4))
* Software:Arduino IDE
    * We need change additional Boards Manages URL ,and it will help us to install ESP8266 libraries
    * Arduino IDE-File-Preference (this is for windows,if your PC is MAC,you can choice Arduino-Preference)
  * Change additional Boards Manages URL(http://arduino.esp8266.com/stable/package_esp8266com_index.json)
    ![](https://gitlab.com/picbed/bed/uploads/e83219459f6b001752e076784c08eec5/url.png)
    

* Arduino IDE's libraries
  * ESP8266WiFi:Open in Arduino IDE-TOOLs-Manage libraries, and search esp8266 ,then istall(need several minutes). If success,open TOOLS-borads and find "NodeMCU1.0(ESP-12E Module)"
    ![](https://gitlab.com/picbed/bed/uploads/48ce68210b243129faed1035dd138055/esp8266.png
)
    ![](https://gitlab.com/picbed/bed/uploads/4600dd4c09ced79bd7ee90ddd0839f9f/esp12e.png)
  * Crypto:[The library is split into four main sections: core, light-weight, legacy, and other.](https://rweather.github.io/arduinolibs/crypto.html)
    ![](https://gitlab.com/picbed/bed/uploads/46802adc37076bbb33b967b078929ea1/crypto.png)

  * PubSubClient:dowload in [google drive](https://drive.google.com/open?id=1pJhtYuMFT3AmbOuwvFcjD2AhxBNycaWU) and install in Arduino IDE(Sketch-Include  Library-Add .ZIP Library)
    ![](https://gitlab.com/picbed/bed/uploads/b492119b4e49ced062c280024f87ca42/addlib.png)
  * ArduinoJson v5:dowload in [google drive](https://drive.google.com/open?id=1B6HYMifYFhIFdC6_gnJQDl0BOi6KxO9E)(some with PubSubClient method)
  * Aliyun:download in[google drive](https://drive.google.com/open?id=1KgQqhhFs2PZr72o1Cfhy-LJQKAi2LyBd)(some with PubSubClient method)
* NodeMCU driver:Open the following [NodeMCU link](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers#windows) and install the version you need ,we can't find NodeMCU in PC's port if we dont't install it 
  
* IOT platform: [aliyun](www.aliyun.com),register by yourself



## 2. IOT platform setting
#### 2.1 Register, log in and go to IOT page 
![](https://gitlab.com/picbed/bed/uploads/04b273ac40bd1591a09681c24c03fe9a/iotcosole.png)
![](https://gitlab.com/picbed/bed/uploads/81b3581c6bf6143b001d22c6449c5503/iotenpage.png)
#### 2.2 Creat products in Devices part(this time we choice wifi method in networking connection method)
  ![](https://gitlab.com/picbed/bed/uploads/e1a3d564b0fa66a10b142414e4f41a42/1creatproduct.png)

  ![](https://gitlab.com/picbed/bed/uploads/d317ee8ea536f919d366353f433fa0c0/2setting_prodcut.png)
#### 2.3 Create device
![](https://gitlab.com/picbed/bed/uploads/88466b8ce48ecf45fd1eb26a96eba872/adddevice.png)

![](https://gitlab.com/picbed/bed/uploads/d1c50eef31164bb3d422054472766206/adddevice.png)
#### 2.4 Define feature of product
Click **Device-Product-Define Feature-Edit Draft**
![](https://gitlab.com/picbed/bed/uploads/652339a6cba54246c2af4b1592b20667/definefeature.png)

![](https://gitlab.com/picbed/bed/uploads/b8be03b445d6b2fab88a3b578cd7007b/editdraft.png)

![](https://gitlab.com/picbed/bed/uploads/f9967cf6adbc24030cf9826b079a429b/define_compornemnt.png)

You should remind Identifier here and we would use it in Arduino programing

![](https://gitlab.com/picbed/bed/uploads/71242c9d1354189e435efcda930e33f6/remind.png)

## 3.Arduino programming

Download arduino coding in [google drive](https://drive.google.com/open?id=1cAExMnKYho5SH_uD8sBeWB3pvG46BIUa)


get Alibaba Cloud's  device information(Product key,Device name,Device secrect)

![](https://gitlab.com/picbed/bed/uploads/b85ab619577765eb0d988dee03e47424/deviceview.png)

![](https://gitlab.com/picbed/bed/uploads/5081bf40696869151c19607d9c9ff4cd/deviceinformation.png)

```
#define PRODUCT_KEY     "******"//1.exchange  PRODUCT_KEY
#define DEVICE_NAME     "******"//2.exchange  DEVICE_NAME
#define DEVICE_SECRET   "******"//3.exchange DEVICE_SECRET
```
Fill your WiFi's name and password, if there is no password,just delete "******"and keep it empty


```
#define WIFI_SSID       "******"//4.exchange WIFI
#define WIFI_PASSWD     "******"//5.exchange WIFI password
```

Define setting post data and get data 

```
void mqtt_interval_post()
{
    char param[512];
    char jsonBuf[1024];
 
    //sprintf(param, "{\"MotionAlarmState\":%d}", digitalRead(13)); 7.define it according to your design
    sprintf(param, "{\"LightSwitch\":%d,\"range\":%d}",!digitalRead(LED),val);
    sprintf(jsonBuf, ALINK_BODY_FORMAT, ALINK_METHOD_PROP_POST, param);
    Serial.println(jsonBuf);
    mqttClient.publish(ALINK_TOPIC_PROP_POST, jsonBuf);
}
```
  we need define  according to Alibaba Cloud's information **LightSwitc**,**range**
  ```
  sprintf(param, "{\"LightSwitch\":%d,\"range\":%d}",!digitalRead(LED),val);
  ```

OK ,we can upload data and test example.


## 4. Test

* Cleck if it is online  then click **view** to check IP
  ![](https://gitlab.com/picbed/bed/uploads/9e62026e46b1cb32933dcdb3231c36af/online.png)
  ![](https://gitlab.com/picbed/bed/uploads/59fc5031dda373f2884a47823dbd7ee5/online2.png)

* Click Online debug to control the NodeMCU
  ![](https://gitlab.com/picbed/bed/uploads/82808e57fc4d8a1ee9fca2967637426f/online3.png)
  ![](https://gitlab.com/picbed/bed/uploads/be9361b1f132843925eea07ed58be88b/online5.png)
  ![](https://gitlab.com/picbed/bed/uploads/39f8e59a716e1e241bfc62144158ff63/online6.png)


* We rotate Potentiometer and then check the data if change

  ![](https://gitlab.com/picbed/bed/uploads/a75ff4b98bf2593803a266a46719de9c/onlinedebug.png)
  
## 5. Reference
* [NodeMCU](https://nodemcu.readthedocs.io/en/master/)
* [NodeMCU driver](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers#windows) 
* [Arduino coding](https://drive.google.com/open?id=1cAExMnKYho5SH_uD8sBeWB3pvG46BIUa)

* [Reference blog](https://blog.csdn.net/ziqi5543/article/details/88710552)
* [reference video](https://www.bilibili.com/video/BV15E411o73P?t=270)