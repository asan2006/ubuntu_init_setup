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
