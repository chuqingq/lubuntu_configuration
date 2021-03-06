# 安装系统

## 安装方案：linuxmint

    sudo apt-get install language-pack-zh-hans # 中文
    安装terminator、wine
    软件管理器安装sublimetext、meld等
    下载安装网易云音乐、搜狗输入法、wps、
    安装mint-codecs：welcome -> install mint-codecs

## 安装：ubuntu

    修改为ustc和aliyun，然后更新缓存
    sougou input fonts: 32
    如果字体小（例如在2K屏上），可以整体放大：设置->字体->字体设置->文本缩放比例，改成1.1或1.2即可。
    如果是ubuntu18.04在matebook13上，缩放默认是200%，然后通过gnome-tweak-tool把字体缩放改称0.8即可。

## 配置语言和输入法

    系统设置->语言设置：chinese，china，应用到整个系统
    输入法：简体中文->安装，然后sudo apt remove fonts-arphic-ukai fonts-arphic-uming
    下载搜狗输入法并安装
    Fcitx配置：保留Keyboard-Chinese和搜狗拼音两种输入法即可。
    https://pinyin.sogou.com/linux/?r=pinyin

## 安装方案：deepin

* driver
    * 我这台电脑需要使用开源驱动，否则启动时没有图形界面。
    * 恢复方法：安装xserver-xorg-video-nouveau，卸载nvidia-legacy-340xx-driver。
* panel
    * 模式：高效模式
    * 位置：左
    * 大小：小
* 深度商店
    * terminator
    * sublime text 3（需要使用DejaVu Sans Mono字体，否则中文对不齐）
    * visual studio code
    * virtualbox
    * 迅雷急速版
* 控制中心
    * qdbus com.deepin.wm  /com/deepin/wm com.deepin.wm.TileActiveWindow 1 左平铺
    * qdbus com.deepin.wm  /com/deepin/wm com.deepin.wm.TileActiveWindow 2 右平铺

## 安装方案：lubuntu-lubuntu+lxde

    sudo apt remove lubuntu*
    sudo apt install lxde-core # lxde-common lxdm

## 安装方案：ubuntuserver+lxde

    https://help.ubuntu.com/community/Installation/MinimalCD/
    sudo apt install lxde-core lxdm xserver-xorg # lxdm可以换为lightdm


## 安装方案：ubuntu 16.04

好处：支持界面非整比例缩放。缩放比例调节1.5。


# 修改配置

## 修改源

    sudo sed -i 's/cn.archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list


## 安装linuxbrew

    http://linuxbrew.sh/

    jdk
    nodejs
    golang
    mongodb

## 软件

    # 卸载掉无用的软件
    sudo apt remove abiword gnumeric sylpheed transmission simple-scan pidgin
    # 开发相关
    sudo apt install vim g++ gdb make git fish vlc terminator chromium-browser catfish zeal meld
    # 办公
    sudo apt install libreoffice
    # mintinstall
    sublimetext、meld、vscode, cheese, 等

## chrome

### googlechrome

建议直接安装google-chrome,使用自带的flashplayer,不用安装pepperflash

    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb

    sudo dpkg -i google-chrome-stable_current_amd64.deb

### chromium+flash

    sudo apt-get update
    sudo apt-get install chromium-browser
    sudo apt-get install pepperflashplugin-nonfree
    sudo update-pepperflashplugin-nonfree --install
    卸载命令：
    sudo apt-get remove chromium-browser pepperflashplugin-nonfree
    # 貌似现在不装flash也可用

## 输入法

### 安装fcitx-googlepinyin

    sudo apt-get install fcitx fcitx-googlepinyin
    # 然后注销重新登录

### 解决中文输入法大黑框的问题

    sudo apt remove fcitx-module-kimpanel
    sudo reboot

## 安装linux搜狗输入法

    http://pinyin.sogou.com/linux/
    # 直接安装64位deb包，注销即可。

    # 卸载不用的输入法：
    sudo apt remove fcitx-pinyin fcitx-sunpinyin fcitx-table

## 安装autossh

    拷贝autossh到$GOPATH/bin/autossh
    apt install expect
    编辑~/.autosshrc

## 安装linux搜狗输入法

    http://pinyin.sogou.com/linux/
    # 直接安装64位deb包，注销即可。

    # 卸载不用的输入法：
    sudo apt remove fcitx-pinyin fcitx-sunpinyin fcitx-table

## 网易云音乐

    http://music.163.com/#/download

## sublimetext

    # 参考 https://www.sublimetext.com/docs/3/linux_repositories.html#apt
    wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
    sudo apt-get install apt-transport-https
    echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
    sudo apt-get update
    sudo apt-get install sublime-text
    # 安装sublime_im_fix修正输入法错误

## vscode

    # 方案1：从官方网站安装
    访问 https://code.visualstudio.com/Download 查看下载地址
    wget -c https://vscode.cdn.azure.cn/stable/a3db5be9b5c6ba46bb7555ec5d60178ecc2eaae4/code_1.32.3-1552606978_amd64.deb
    sudo apt install ./code_1.32.3-1552606978_amd64.deb

    # 方案2：从snap安装
    sudo snap install code --classic

## wps-office

    # 访问 http://www.wps.cn/product/wpslinux 获得下载地质
    wget -c https://wdl1.cache.wps.cn/wps/download/ep/Linux2019/8372/wps-office_11.1.0.8372_amd64.deb
    sudo apt install ./wps-office*.deb

    # 方案2：版本比较旧
    sudo snap install wps-office

## 安装source-code-pro字体

    下载地址：https://github.com/adobe-fonts/source-code-pro/downloads`
    安装步骤：http://blog.csdn.net/android_hasen/article/details/50523013`

    wget -c https://github.com/downloads/adobe-fonts/source-code-pro/SourceCodePro_FontsOnly-1.013.zip
    unzip SourceCodePro_FontsOnly-1.013.zip
    mkdir ~/.fonts
    cp SourceCodePro_FontsOnly-1.013/OTF/* ~/.fonts/
    fc-cache -fv

## 使用fish

    sudo apt install fish
    chsh -s /usr/bin/fish

## 安装autossh

    https://github.com/wufeifei/autossh
    sudo apt install expect
    cd ~/gopath/bin
    wget https://raw.githubusercontent.com/wufeifei/autossh/master/autossh
    chmod a+x autossh

## ss

    # 下载地址：当前最新版本3.0.1，支持CHACHA20-IETF-POLY1305加密。
    https://github.com/shadowsocks/shadowsocks-qt5/releases
    # 加权限
    chmod a+x Shadowsocks-Qt5-3.0.1-x86_64.AppImage
    # 启动
    ./Shadowsocks-Qt5-3.0.1-x86_64.AppImage
    # 修改配置或者从网盘直接下载json配置文件并导入

### 设置系统代理（目的是安装chromium的switchyomega插件）

    网络->网络代理->手动->socks主机配置为127.0.0.1:1080
    可以让chromium先用系统的设置

### chromium安装switchyomega插件

    https://github.com/FelisCatus/SwitchyOmega/releases
    https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif

### 导入switchyomega_options配置文件

### 开启chromium同步功能

## 安装redis、mongodb等

    sudo apt install redis-server mongodb
    # 停止自启动
    sudo update-rc.d redis-server disable
    sudo update-rc.d mongodb disable
    # 临时停止服务
    sudo service redis-server stop // redis和redis-server都可以
    mongodb ???
    # 查询服务
    service redis-server status // redis和redis-server都可以
    mongodb ???

