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





