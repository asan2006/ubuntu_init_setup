# ubuntu_init_setup
## ubuntu 16.04（vmware）  
1. 安装vmware-tools  
```shell
  sudo ./vmware-install.pl
```
2. 删除不常用软件  
libreoffice-common libreoffice（可以换 WPS）  
unity-webapps-common Amazon 链接  
thunderbird 雷鸟邮件客户端  
totem 自带的播放器  
rhythmbox 自带的音乐播放器  
empathy 自带的即时聊天应用  
brasero 自带的光盘刻录器  
simple-scan 扫描仪  
gnome-mahjongg 对对碰游戏  
aisleriot 纸牌游戏  
gnome-mines 扫雷游戏  
cheese webcam 应用  
gnome-sudoku 数独游戏  
transmission-common BT 客户端    
gnome-orca 屏幕阅读  
webbrowser-app Ubuntu 自带的浏览器（有了 chrome 和 Firefox 根本用不到这个）  
landscape-client-ui-install landscape 远程控制软件  
deja-dup 备份  
onboard 屏幕键盘  
```shell
sudo apt purge libreoffice-common  
sudo apt purge unity-webapps-common  
sudo apt purge thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese gnome-sudoku transmission-common gnome-orca webbrowser-app landscape-client-ui-install 
sudo apt purge deja-dup onborad
```
3. 更换阿里源
```shell
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo gedit /etc/apt/sources.list
```
更改如下：
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted
#Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main restricted multiverse universe
#Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main restricted multiverse universe
#Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb http://mirrors.aliyun.com/ubuntu/ xenial multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates multiverse
deb http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-backports main restricted universe multiverse
#Added by software-properties
deb http://archive.canonical.com/ubuntu xenial partner
deb-src http://archive.canonical.com/ubuntu xenial partner
deb http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main restricted multiverse universe
#Added by software-properties
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-security multiverse
```
4. 安装chrome，卸载Firefox
```shell
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable

dpkg --get-selections | grep firefox
sudo apt-get purge firefox   firefox-globalmenu  firefox-gnome-support   firefox-locale-en   firefox-locale-zh-hans
```
5. 安装搜狗拼音输入法
6. 安装tsocks
```shell
sudo apt-get install tsocks
```
7. 安装gnome
```shell
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt update
sudo apt dist-upgrade
sudo apt install gnome gnome-shell
```