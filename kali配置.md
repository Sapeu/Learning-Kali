# Kali配置

1. 更换软件源 编辑/etc/apt/sources.list

    - 默认源

    --- 
        deb http://http.kali.org/kali kali-rolling main contrib non-free
        deb-src http://http.kali.org/kali kali-rolling main contrib non-free

    - 中科大Kali源

    ---
        deb http://mirrors.ustc.edu.cn/kali kali-rolling main contrib non-free
        deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main contrib non-free

    - 阿里Kali源

    ---
        deb http://mirrors.aliyun.com/kali kali-rolling main contrib non-free
        deb-src http://mirrors.aliyun.com/kali kali-rolling main contrib non-free

2. gnome桌面设置

```shell
gsettings set org.gnome.desktop.session session-name gnome #这个模式比较流畅
gsettings set org.gnome.desktop.session session-name gnome-fallback #还原默认模式
gnome-shell –replace #在默认模式临时开启
```

3. Kali-linux设置vpn代理

```shell
apt-get install network-manager-openvpn-gnome
apt-get install network-manager-pptp
apt-get install network-manager-pptp-gnome
apt-get install network-manager-strongswan
apt-get install network-manager-vpnc
apt-get install network-manager-vpnc-gnome
/etc/init.d/network-manager restart5
```

4. 启动终端快捷键

> 系统
>> 设置
>>> 快捷键 
>>>>添加如下命令：`gnome-terminal`然后设置 快捷启动终端的键（ctrl+alt+T）

5. 配置java

```shell
gedit /etc/profile  # 最末尾添加
export JAVA_HOME=/usr/lib/jdk/jdk1.7.0_03
export JRE_HOME=/usr/lib/jdk/jdk1.7.0_03/jre 
export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH  
export CLASSPATH=$CLASSPATH:.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib
```

6. 配置Git

```shell
ssh-keygen -t rsa -C "xxxx@email.com"
git config --global user.name "xxxx"
git config --global user.email "xxxx@email.com"
```

7. 添加用户

```shell
useradd -m xxx
passwd xxx
usermod -a -G sudo xxx
chsh -s /bin/bash xxx
```

8. 安装和删除软件

```shell
apt-get install git
apt-get install fcitx fcitx-googlepinyin #输入法
apt-get install iceweasel-l10n-zh-cn #汉化浏览器
apt-get install gnome-tweak-tool #安装gnome管理软件
apt-get install synaptic  #安装新立德
apt-get install file-roller #安装解压缩软件
apt-get install clementine  #clementine音乐播放器
apt-get install smplayer #安装smplayer视频播放器
apt-get install  gdebi #有了这个安装软件就不用在终端中dpkg -i安装了，提供图形化软件安装方式
apt-get install nautilus-open-terminal #鼠标右键在当前目录打开终端
apt-get install flashplugin-nonfree #浏览器flash插件
apt-get install terminator #安装多窗口终端
apt-get install google-chrome-stable  #chrome浏览器
apt-get install libreoffice okular #安装libreoffce、pdf文档阅读器
apt-get install lxde-core lxde kali-defaults kali-root-login desktop-base #安装LXDE
apt-get install kali-defaults kali-root-login desktop-base kde-plasma-desktop # 安装KDE

# 删除软件
# 一、如果你知道要删除软件的具体名称，可以使用               =
sudo apt-get remove --purge 软件名称  
sudo apt-get autoremove --purge 软件名称 
# 二、如果不知道要删除软件的具体名称，可以使用
dpkg --get-selections | grep #软件相关名称
sudo apt-get purge #一个带core的package，如果没有带core的package，则是情况而定。
#清理残留数据
dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P 
apt-get remove lxde-core lxde # 删除LXDE
apt-get remove kde-plasma-desktop kde-plasma-desktop kde-standard # 删除KDE
```