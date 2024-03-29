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
sudo apt remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese transmission-common gnome-orca webbrowser-app gnome-sudoku  landscape-client-ui-install  onboard deja-dup
```
可选删除
```shell
sudo apt-get remove libreoffice* #自带office,WPS代替
sudo apt-get remove yelp #帮助
sudo apt-get remove blue* #蓝牙
sudo apt-get remove gnome-software #软件中心 apt够用 
sudo apt-get remove unity #换gnome
sudo apt-get remove gnome-system-monitor #系统监视器
sudo apt-get remove gnome-system-log #日志查看器
sudo apt autoremove
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
4. 必备软件
```shell
sudo apt-get install unrar #安装unrar程序
sudo apt-get install exfat-fuse #Ubuntu默认不支持exFat，需要手动安装exfat的支持
sudo apt-get install openssh-server #安装之后，就可以在Win下用ssh工具远程登陆了，当然也多了一个安全隐患，如果不想远程登陆本机的话，可以不装openssh-server
sudo apt-get install axel #多线程下载神器
sudo apt-get install apt-fast #用 axel 来加速 apt-get 软件安装的脚本,由于是多线程下载，所以加速效果还是很明显的。使用apt-fast 命令替代原apt-get 命令即可
sudo apt-get install git #git
sudo apt-get install vim #神器
sudo apt-get install pip #pip
sudo apt-get install shutter #截图
sudo apt-get install unity-tweak-tool #配置主题
sudo apt-get install wps-office 
sudo apt-get install gnome-mpv #视频播放
```
安装chrome，卸载Firefox
```shell
sudo wget http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
sudo apt-get update
sudo apt-get install google-chrome-stable

dpkg --get-selections | grep firefox
sudo apt-get purge firefox   firefox-globalmenu  firefox-gnome-support   firefox-locale-en   firefox-locale-zh-hans
```
5. 安装搜狗拼音输入法
```shell
sudo apt install fcitx-frontend-qt5
#拷贝libfcitxplatforminputcontextplugin.so文件到QT的安装目录
#给予执行权限(否则不生效)
cd /opt/Qt5.12.4/Tools/QtCreator/lib/Qt/plugins/platforminputcontexts
chmod 775 *
cd /opt/Qt5.12.4/5.12.4/gcc_64/plugins/platforminputcontexts
chmod 775 *
```
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
sudo apt-get install gnome-tweak-tool
# reconfigure (ubuntu16 的unity登陆界面可能会有问题)
sudo dpkg-reconfigure gdm3
```
8. 美化
```shell
sudo add-apt-repository ppa:noobslab/themes
sudo apt-get update
sudo apt-get install flatabulous-theme

sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update
sudo apt-get install ultra-flat-icons
```
9. 配置oh-my-zsh
```shell
sudo apt install zsh
sh -c "$(wget -O- https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

#https://www.jianshu.com/p/cbcd3ef1d9f3
```
10.配置conky
```shell
sudo apt install conky-all

sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt update
sudo apt install conky-manager

```
11. 环境变量
在bash配置文件中添加环境变量
```shell
#对所有用户有效修改/etc/profile
#对个人有效则修改~/.bashrc

#在PATH中找到可执行文件程序的路径。
export PATH =$PATH:$HOME/bin  
#gcc找到头文件的路径
C_INCLUDE_PATH=/usr/include/libxml2:/MyLib  
export C_INCLUDE_PATH  
#g++找到头文件的路径
CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/usr/include/libxml2:/MyLib  
export CPLUS_INCLUDE_PATH  
#找到动态链接库的路径
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/MyLib  
export LD_LIBRARY_PATH  
#找到静态库的路径
LIBRARY_PATH=$LIBRARY_PATH:/MyLib  
export LIBRARY_PATH  

#下面是在gcc命令中手动设置搜索路径：
#添加头文件搜索路径
# gcc foo.c -I /home/xiaowp/include -o foo  
 #添加动态库搜索路径
# gcc foo.c -L /home/xiaowp/lib -lfoo -o foo  
#添加静态库搜索路径
# gcc foo.c -L /home/xiaowp/lib -static -lfoo -o foo 
```