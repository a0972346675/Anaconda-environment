# Anaconda-environment

(1)Anaconda虛擬環境建置 Conda
參考網址  https://ithelp.ithome.com.tw/articles/10262541

------------------------------------------------------------

建立虛擬環境

conda create --name car_env python=3.11 #在--name後面自行命名環境名稱

進入虛擬環境

conda activate car_env

安裝自己的pip: 
我们自己建立的conda環境裏，可能没有pip，此时進入自己的conda環境也會默认用base环境的pip，这就需要我们自己将pip安装入本环境，尽量不要使用base的pip在其他环境装包，这样也会装在base里，有产生版本冲突的可能（上文已讲）。在自己conda环境安装pip使用如下命令：

（進入環境後）
 conda install pip

載入opencv套件
pip install opencv-python

安裝dlib會報錯: 解法!
------------------------------------------------------------

Error in installing dlib library in python3.11
參考這一篇文章 https://stackoverflow.com/questions/74476152/error-in-installing-dlib-library-in-python3-11
解法: python要搭配合適的dlib版本，目前python3.11沒支援dlib，所以要降版本到python3.6

降版本到 pip install python=3.9

這時可以安裝相對應dlib版本了(下載合適版本，從這裡選擇)
https://github.com/shashankx86/dlib_compiled

安裝dlib
pip install dlib-19.8.1-cp36-cp36m-win_amd64.whl

另外，numpy也要安裝合適對應版本
(可以參考numpy衝突說明: [numpy1.19.4与python3.9版本冲突解决]  https://blog.csdn.net/weixin_47154407/article/details/110673550 )

先解安裝  pip uninstall numpy

再安裝相對應版本  pip install numpy==1.19.3

先解安裝  pip uninstall scipy
再安裝相對應版本 pip install scipy==1.5.4

安裝PIL套件   pip install Pillow

------------------------------------------------------------

心跳模組實驗 (手指心跳脈搏感測模組 / 心率偵測)
感測器採購: https://shop.playrobot.com/products/finger-pulse-heartbeat-detection-sensor

這個模組採用超亮紅外(IR)LED漢光敏晶體管來探測手指的脈搏，紅色LED會隨著脈搏閃動，當血壓脈搏通過手指時，電阻便會有微小的變化，只要你有Arduino控制器，就可以製造出自己的脈搏偵測機！

規格：

+ 接5v
  
s 接信号

- 接GND

程式碼：
------------------------------------------------------------

// Pulse Monitor Test Script
int sensorPin = 0;
double alpha = 0.75;
int period = 100;
double change = 0.0;
double minval = 0.0;
void setup ()
{
  Serial.begin (9600);
}
void loop ()
{
    static double oldValue = 0;
    static double oldChange = 0;
 
    int rawValue = analogRead (sensorPin);
    double value = alpha * oldValue + (1 - alpha) * rawValue;
 
    Serial.print (rawValue);
    Serial.print (",");
    Serial.println (value);
    oldValue = value;
 
    delay (period);
}

------------------------------------------------------------


