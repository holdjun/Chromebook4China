# chromebook 在国内的使用
## 本文不考虑其他情况 一切以个人需求出发
```
设备：  Chromebook Thinkpad 13
版本号：63.0.3239.7 dev
```
如果本篇文章能够帮助到你们，麻烦请点个start

# 激活 初始化
因为寝室路由器的能直接接入万维网，那么激活 chromebook 只要连上 wifi 就可以，登陆好个人的 google 账号，google 会自动同步你所有的记录，当然如果你嫌 chromebook 安装的应用会影响到 pc 或 mac 端的使用，那么只要在设置同步里自行调整即可。（找了半天的.pac文件没找到比较尴尬，希望大家激活的时候都有好法子）

# 在 Chromebook 上使用 google play
不同设备支持 google play 的时间是不同的，有需求的同学可以参考[Chrome OS Systems Supporting Android Apps](https://www.chromium.org/chromium-os/chrome-os-systems-supporting-android-apps)

在上面表里，tp13 是不支持 google play 的，但是没关系，你可以通过把 Chromebook 改成开发者版本，就可以使用 google play，虽说 play 里支持的 Android app 很少，但是你可以通过安装 apk 来安装常用的 app。比如 $$r 虚荣等等。

![](http://ove2oliz4.bkt.clouddn.com/17-10-24/83972814.jpg)
![](http://ove2oliz4.bkt.clouddn.com/17-10-24/88479891.jpg)
![](http://ove2oliz4.bkt.clouddn.com/17-10-24/9636210.jpg)

更新完系统之后，打开设置看有没有亲爱的 google play 没有的话，再等等把。。。。

![](http://ove2oliz4.bkt.clouddn.com/17-10-24/15299468.jpg)

ps 强烈建议下虚荣玩玩，支持触摸屏，也支持键盘操作。

# crouton
## 进入开发者模式
同时按下 esc + 刷新键(tp13 在第四个键) + 电源键即可，都是在最上面那一排。

然后 Chromebook 重启，然后按 Ctrl+D 继续，回车重启，上面的进度条走完了之后自动重启，就进入开发者模式了。

[crouton git 链接](https://github.com/dnschneid/crouton)可以直接看文档。

[crouton](https://github.com/dnschneid/crouton/raw/master/installer/crouton)这是crouton的下载链接，下载完放在 Downloads 下。

用 Ctrl+ALT+T 调出 crosh 窗口，输入 shell。

查看 crouton 支持的 ubuntu 版本：
```
sh ~/Downloads/crouton -r list
```
下载 unity 14.04 ubuntu
```
sudo sh -e ~/Downloads/crouton -r trusty -t core,audio,xorg,x11,gtk-extra,unity,keyboard,cli-extra
```
接着等待，在网络好的情况下半小时差不多了，最后要求输入用户名和密码。

crouton 的文档里也有例子
```
sudo sh ~/Downloads/crouton -t xfce
sudo enter-chroot startxfce4 
```
但是我个人更喜欢 unity 的桌面一点(⊙﹏⊙)

进入 unity桌面
```
sudo startunity

在 chrome os 和 Ubuntu 之间切换：

从 C 到 U：shift + ctrl + alt + 前进键
从 U 到 C：shift + ctrl + alt + 后退键

sudo enter-chroot     不开启桌面在 Chromebook os 里使用 Ubuntu 的终端。
```
![通过 chrome 使用 Ubuntu 的终端](https://cdn.sspai.com/2017/10/25/ef596797a5aaeb85a20c426dc84bbee9.png)


## ubuntu 开发配置
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
先在 chrome 网上应用商店里下载 [cronton-integration](https://chrome.google.com/webstore/detail/crouton-integration/gcpneefbbnfalgjniomfjknbcgkbijom)
```
sudo sh ~/Downloads/crouton -t xfce,extension,xorg,xiwi //我是在 xfce 桌面下使用的 unity 也可行 但要求下载 extension,xorg,xiwi
sudo startxfce4 -X xiwi // 使用 xiwi 来实现 窗口化
```
![左边 chrome 右边 xfce 桌面](http://ove2oliz4.bkt.clouddn.com/17-10-30/43667450.jpg)

可以通过查看 [xiwi](https://github.com/dnschneid/crouton/wiki/crouton-in-a-Chromium-OS-window-(xiwi)) 的文档来使用，那么既然可以实现桌面的窗口化，那么也可以实现一部分应用的窗口化，比如 vscode

首先是在安装 vscode，因为 chrome OS 和 Ubuntu 的Downloads 是通用的，可以直接在 chrome OS 下载到 Downloads 然后在 Ubuntu 里 cd 到 Downloads
```
sudo dpkg -i <file>.deb // 直接通过网页下载 .deb 包
sudo apt-get install -f // Install dependencies

xiwi -T code -f . //如果安装成功，可以直接执行这段命令
```
![](http://ove2oliz4.bkt.clouddn.com/17-10-30/13922414.jpg)

这样就是一个桌面 一个 chrome 一个 vscode 无论开发还是玩耍都是神器呀。

有需求的同学也可以参考[wiki](https://github.com/dnschneid/crouton/wiki) crouton 的使用真的太厉害了。

## chromebook 插件和应用推荐
- [listen1_chrome_extension](https://github.com/listen1/listen1_chrome_extension) 听歌利器，在 chromebook 里更是神器，不用安装不兼容的 Android apps 
- [sendanywhere](https://send-anywhere.com/file-transfer) 传输利器，不管是插件还是应用
- tampermonkey 和 ublock 这种神器就不介绍了
- [Minimalist Markdown Editor](https://chrome.google.com/webstore/detail/minimalist-markdown-edito/pghodfjepegmciihfhdipmimghiakcjf?utm_source=chrome-app-launcher-info-dialog) Markdown 的编辑器简洁干净
- [Cog - System Info Viewer](https://chrome.google.com/webstore/detail/cog-system-info-viewer/difcjdggkffcfgcfconafogflmmaadco?utm_source=chrome-app-launcher-info-dialog) 查看性能的工具
- [QQaPad](http://im.qq.com/apad/) HD 版的 qq 能完美兼容 chromebook 也不会和手机QQ 有冲突
- ssr 大家懂得哈 可以实现很底层的爬墙
# 小生不才，一家之言，将就将就。
说说体验把，个人使用 thinkkpad 13 虽说没有小红点体验很不好，但是基于 chromeos 本子不厚、不重、续航也不错，是一款相当不错的本子，虽说分辨率低了点，最近的嵌入式实验课刚好可以使用，刷刷面试题也行，搞搞 github 也行，马马虎虎对于没有经济独立的爱折腾人群来说相当不错了，真的是物有所值。最后送上一张图。
![](http://ove2oliz4.bkt.clouddn.com/17-10-30/69715262.jpg)
