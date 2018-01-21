# Chromebook 在国内的使用
```
设备：Chromebook plus （Chromebook Thinkpad 13）
版本号：64.0.3282.101 beta
```
如果本文能够帮助到你们，麻烦请点个start  ￣へ￣
# 激活 初始化
因为寝室路由器的能直接接入万维网，那么激活 Chromebook 只要连上 wifi 就可以，登陆好个人的 google 账号，**google 会自动同步你所有的记录**，当然如果你嫌 Chromebook 安装的应用会影响到 pc 或 mac 端的使用，那么只要在设置同步里自行调整即可。~~（找了半天的.pac文件没找到比较尴尬，希望大家激活的时候都有好法子）~~
如果在 pc 端有 ss 的话，我可以分享一个可以用来激活的方法。
- 在 ss 设置中选择"允许来自局域网的连接"
- 然后在 Chromebook 上连上和 windows 同一局域网的 wifi
- 然后在 Chromebook 的网络设置中填入自动配置代理“http://windows电脑IP地址:SS代理端口/pac” 
  比如 http://192.168.199.143:1080/pac 
  
<p align="center">
  <img src="http://ove2oliz4.bkt.clouddn.com/18-1-21/43528189.jpg" width="700" height="500" alt="pac"/>
</p>

# 在 Chromebook 上使用 google play
不同设备支持 google play 的时间是不同的，有需求的同学可以参考 [Chrome OS Systems Supporting Android Apps](https://www.chromium.org/chromium-os/chrome-os-systems-supporting-android-apps)

在上面表里，tp13 是不支持 google play 的，但是没关系，你可以通过把 Chromebook 改成 **dev 或者 beta 版本**，就有可能可以使用 google play，虽说 play 里支持的 Android app 很少，但是你可以通过安装 apk 来安装常用的 app。比如 [ssr](https://file.qingjie.me/%E7%88%B1%E5%9B%BD%E8%BD%AF%E4%BB%B6/Android/ssr-3.4.0.8.apk)（有需求的同学可以直接点击下载）

现在大部分的 Chromebook 都支持 google play 了

更新完系统之后，打开设置看有没有亲爱的 google play 没有的话，~~再等等把。。。。~~别等了，换台 cb 吧

![](http://ove2oliz4.bkt.clouddn.com/17-10-24/15299468.jpg)

> ps 强烈建议下虚荣和炉石玩玩，支持触摸屏，也支持键盘操作。

## 还有一些 Chromebook 的小技巧

chrome://flags/#arc-vpn 有些同学会发现 ssr 不能让浏览器爬墙，你只要设置成 enable 就可以了

chrome://flags/#ash-enable-night-light **开启夜间模式**（可以在设置里的显示 调整色温和时间）

chrome://flags/#ash-debug-shortcuts **关闭 cb 的触摸屏或者触摸板**

```
Search+Shift+P = Toggle touchpad off/on
Search+Shift+T = Toggle touchscreen off/on
```
使用 **Smart Lock** 可以使用手机来解锁，beta版存在不稳定性

<p align="center">
  <img src="http://ove2oliz4.bkt.clouddn.com/18-1-21/10777512.jpg" width="430" height="350"/><img src="http://ove2oliz4.bkt.clouddn.com/18-1-21/13101252.jpg" width="430" height="350"/>
</p>
<p align="center">
  <img src="http://ove2oliz4.bkt.clouddn.com/18-1-21/41777477.jpg" width="300" height="400"/>
</p>

# crouton

先介绍一下 crouton 吧，其实 Chromebook 就是一台 **Linux** 电脑，只是配置比较差而已。那么就可以用终端来干更多的事情，比如一些开发啥的，毕竟是 Linux 呀。

如果有需求的话，接着往下看吧。也可以直接看文档[crouton git 链接](https://github.com/dnschneid/crouton)。

## 第一步 进入开发者模式

同时按下 esc + 刷新键(tp13 在第四个键) + 电源键即可，都是在最上面那一排。

然后 Chromebook 重启，然后按 Ctrl+D 继续，回车重启，上面的进度条走完了之后自动重启，就进入开发者模式了。

## 第二步 使用 crouton

[crouton](https://github.com/dnschneid/crouton/raw/master/installer/crouton)这是crouton的下载链接，下载完放在 Downloads 下。

用 Ctrl+ALT+T 调出 crosh 窗口，输入 shell。

查看 crouton 支持的 ubuntu 版本：
```
sh ~/Downloads/crouton -r list
```
```
sudo sh -e ~/Downloads/crouton -r trusty -t core,audio,xorg,x11,gtk-extra,unity,keyboard,cli-extra 下载 unity 14.04 ubuntu
或者
sudo sh ~/Downloads/crouton -t xfce 下载 xfce 桌面
```
但是我个人更喜欢 unity 的桌面一点(⊙﹏⊙)

如果不喜欢下载桌面也没事，可以只下载CLI，就是最简单的终端

```
sudo sh ~/Downloads/crouton -t core
```

进入桌面
```
sudo enter-chroot 进入终端
sudo startunity 启动桌面
sudo startxfce4 启动 xfce 桌面 
在 Chrome os 和 Linux 之间切换：

从 C 到 L：shift + ctrl + alt + 前进键
从 L 到 C：shift + ctrl + alt + 后退键
```
![通过 chrome 使用 Ubuntu 的终端](https://cdn.sspai.com/2017/10/25/ef596797a5aaeb85a20c426dc84bbee9.png)


## 第三步 Linux 开发配置
**个人使用习惯仅供参考**

其实一台低配的 Chromebook 装完 ubuntu 是有点吃力的，但是就是想折腾折腾。

~~打开终端输入，比较简单的下载了所以的先（之后没有需求的再删把。。）~~ 后面有新的推荐使用方法
```
sudo apt-get install ubuntu-desktop 			   //下载完整版 Ubuntu
sudo apt-get remove libreoffice-common -y          //删除 libreoffice
sudo apt-get remove unity-webapps-common -y        //删除 amazon
sudo apt-get remove thunderbird totem rhythmbox empathy brasero simple-scan gnome-mahjongg aisleriot gnome-mines cheese transmission-common gnome-orca webbrowser-app gnome-sudoku  landscape-client-ui-install onboard deja-dup -y
```
设置中文环境
```
sudo apt-get install language-pack-zh-hans language-pack-zh-hans-base language-pack-gnome-zh-hans language-pack-gnome-zh-hans-base
sudo apt-get install `check-language-support -l zh`
sudo localectl set-locale LANG=zh_CN.UTF-8
```

主题配置 （个人癖好）还有一直用的一个壁纸
```
wget -q -O - http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo sh -c 'echo "deb http://archive.getdeb.net/ubuntu xenial-getdeb apps" >> /etc/apt/sources.list.d/getdeb.list'
sudo add-apt-repository ppa:noobslab/themes
sudo add-apt-repository ppa:noobslab/icons
sudo apt-get update
sudo apt-get install ubuntu-tweak -y
sudo apt-get install flatabulous-theme -y
sudo apt-get install ultra-flat-icons -y
sudo apt-get install vpnc git -y
```

## 删除 ubuntu
```
sudo delete-chroot chrootname //chrootname: 所安装 ubuntu 的版本代号
```
## crouton 进阶使用
用多了，你可能会觉得**两个系统之间切换很麻烦**，对的。

**所以使用 xiwi**

先在 chrome 网上应用商店里下载 [cronton-integration](https://chrome.google.com/webstore/detail/crouton-integration/gcpneefbbnfalgjniomfjknbcgkbijom)

```
sudo sh ~/Downloads/crouton -t xfce,extension,xorg,xiwi //我是在 xfce 桌面下使用的 unity 也可行 但要求下载 extension,xorg,xiwi
sudo startxfce4 -X xiwi // 使用 xiwi 来实现 窗口化
```
![左边 chrome 右边 xfce 桌面](http://ove2oliz4.bkt.clouddn.com/17-10-30/43667450.jpg)

可以通过查看 [xiwi](https://github.com/dnschneid/crouton/wiki/crouton-in-a-Chromium-OS-window-(xiwi)) 的文档来使用，那么既然可以实现桌面的窗口化，那么也可以实现一部分应用的窗口化，比如 vscode

首先是在安装 vscode，**因为 chrome OS 和 Ubuntu 的 Downloads 文件夹是通用的**，可以直接在 chrome OS 下载到 Downloads 然后在 Ubuntu 里 cd 到 Downloads
```
sudo dpkg -i <file>.deb // 直接通过网页下载 .deb 包
sudo apt-get install -f // Install dependencies

xiwi -T code -f . //如果安装成功，可以直接执行这段命令
```
![](http://ove2oliz4.bkt.clouddn.com/17-10-30/13922414.jpg)

这样就是一个桌面 一个 chrome 一个 vscode 无论开发还是玩耍都是神器呀。

有需求的同学也可以参考 [wiki](https://github.com/dnschneid/crouton/wiki) crouton 的使用真的太厉害了。

## Chromebook 插件和应用推荐
- [listen1_chrome_extension](https://github.com/listen1/listen1_chrome_extension) 听歌利器，在 Chromebook 里更是神器，不用安装不兼容的 Android apps 
- [sendanywhere](https://send-anywhere.com/file-transfer) 传输利器，不管是插件还是应用
- tampermonkey 和 ublock 这种神器就不介绍了
- [Minimalist Markdown Editor](https://chrome.google.com/webstore/detail/minimalist-markdown-edito/pghodfjepegmciihfhdipmimghiakcjf?utm_source=chrome-app-launcher-info-dialog) Markdown 的编辑器简洁干净
- [Cog - System Info Viewer](https://chrome.google.com/webstore/detail/cog-system-info-viewer/difcjdggkffcfgcfconafogflmmaadco?utm_source=chrome-app-launcher-info-dialog) 查看性能的工具
- [pushbullet](https://www.pushbullet.com/) 和手机之间的通知同步
- ssr 大家懂得哈 可以实现很底层的爬墙
# 小生不才，一家之言，将就将就。
说说体验把，个人使用 thinkkpad 13 虽说没有小红点体验很不好，但是基于 chromeos 本子**不厚、不重、续航也不错**，是一款相当不错的本子，虽说分辨率低了点，最近的嵌入式实验课刚好可以使用，刷刷面试题也行，搞搞 github 也行，马马虎虎对于没有经济独立的爱折腾人群来说相当不错了，真的是物有所值。最后送上一张图。

三星的 Chromebook plus 体验比 tp 要给力很多，但是三星在品控上还需要加强一点，arm 的处理器有点鸡肋，Chromebook pro 应该蛮不错的，但是**价格**也有点虚高。

也可以看看 Medium 上别人的分享

- [Switching from a Mac to a Chromebook (as a web developer)](https://medium.com/@nshki_/switching-from-a-mac-to-a-chromebook-as-a-web-developer-761450c05a5a)

- [Owning a Chromebook](https://hackernoon.com/owning-a-chromebook-6a364c87d830)

![](http://ove2oliz4.bkt.clouddn.com/18-1-21/51670342.jpg)
