---
tags: Media
title: 小米盒子3增强版刷机若干
excerpt: Mi Box 3 Enhanced，型号为MDZ-18-AA
comments: true
---


![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

----

小米盒子的版本五花八门，到现在已经出到4代，又C版本、S版本、mini、增强版、国际版...其实不用管那么多，翻转盒子看底部的型号即可对应。目前第4代盒子用的是`Android TV 6.0.1`，尚未有root的方法，意味着你享受着它比3代好那么一点点的硬件，却要忍受如图无比丑的界面。不行。

![米盒3界面](https://i.imgur.com/9KG4I34.jpg)

我们就拿能够搞点事情的小米盒子3增强版来刷机。说句实话，这个版本的界面实在令人受不了，广告还一波接一波的，必须干翻。

而小米盒子3增强版刷机后有两个选择：

- 电视版Android TV
- 手机版Android

Android TV大概就是下图的样子：

![Imgur](https://i.imgur.com/isPV8n6.jpg)

而手机版的可能熟悉多了，大概是以下样子：

![Imgur](https://i.imgur.com/C2i9dp7.jpg)


而两者有什么不同呢？

大同小异。除了界面，最大的不同更多是：

**稳定性** 。

例如，Android TV版的：

- `Kodi`经常性崩溃；
- `Netflix`无法使用；
- `Prime Vedio` 无法使用；
- TV版应用不多，你想要你不一定适配。

等等。

Android TV出了名多问题的，毕竟它现在还不是Google主推的项目。当然，你可以两个都试试。


### 刷机步骤 ###

**刷机有风险！请自行承担刷机后果。否则截至此处请关闭网页离开。
Use only the package created for your ROM version! Otherwise you can get a softbrick and/or bootloop!Install it only on top of an untouched ROM - reset to a factory ROM via recovery and do an update via Settings!**

1. 恢复出厂设置。
- 按住遥控上的`Home`键和`菜单`键，断开遥控和盒子的连接，然后**马上**断开盒子电源；
- 稍等片刻后，按住遥控上的`确定`键和`返回`键，插上盒子电源，直到出现Recovery的界面。

2. 查看出厂的系统版本。
出厂版本通常的1.4几，目前可以root的是`1.5.16`和`1.5.2`选择对应的升级版本。你需要根据你的出厂版本升级到`1.5.16`或者`1.5.2`。

升级到`1.5.16`还是`1.5.2`？
区别在于`1.5.2`不能刷机至`手机版`，`1.5.16`两者都可以。

升级版本在[我的Google Drive分享](https://drive.google.com/open?id=1KYQ6heom1RPdzXkD3VZooXmhrXbhQ7oZ)可以下载到。

3. 升级版本
把系统升级文件放在U盘`根目录`下，插上盒子，待识别后，重启至Recovery界面。系统就会自动识别出升级文件，并开始升级。

4.取得Root权限
升级版本后，下载对应的刷机文件。
`1.5.16`和`1.5.2`的刷机文件有些许不同，不要误用。

刷机文件在[我的Google Drive分享](https://drive.google.com/open?id=1KYQ6heom1RPdzXkD3VZooXmhrXbhQ7oZ)可以下载到。

- 安装`0_APPS`中的`1_Settings_1.0.apk`，打开并设置系统语言为English；
- 安装`2_KingRoot_4.8.0.apk`，打开并按提示提取Root权限；
- 安装`3_SManager_3.0.4.apk`，打开，选择`Browse as root`，把刷机文件夹`MDZ18AA_[ROM_Version]`整个复制到盒子的内置存储中`/storage/emulated/legacy`。
- 复制完成后，到`1_ROOT`文件夹中，执行`SuperSU.sh`。
- 选择独眼龙的`SU`标志，并按`RUN`执行。完成后选择专家模式，以`Normal`方式更新。
- 按提示重启后，你已取得Root权限。


#### 安装Android TV ####

- 打开SManager，进入`2_GAPPSTV`文件夹，执行`GappsTV.sh`，完成后便会重启。至此你将安装了**Android TV**。
- 重启至Recovery界面，清除所有数据，重启。
- 安装完成。

#### 按照手机版Android ####

- 同样道理，我们打开Smanager进入`2_GAPPS`文件夹，执行后即可获得手机版的系统。
- 重启至Recovery，双清重启。
- 安装完成。


### 安装Google Now Launcher 等应用 ###

Rom提供的launcher是Nova，我们在Google Play安装Google Now Launcher，安装Link2SD。用Link2SD把Google Now Launcher设置为系统应用，重启。

![Imgur](https://i.imgur.com/GIw7Z67.jpg)

接下来我们可以安装Google Assistant。

![Imgur](https://i.imgur.com/GHDg56H.jpg)

安装后你便可以`短按+长按`着`Home`键，启动语音功能。

再安装例如`Kodi 18`（上文提到TV版会崩溃的是指18）、`Netflix`等应用，尽情享受了。

由于这是手机版，部分安装的应用不能用遥控操作所有功能，你可以在手机上安装`投屏神器`，小米自家的应用，用鼠标模式操作上述应用。

如果你发现输入法无法使用，可以安装刷机文件里的`LeanbackIME.apk`。

Enjoy!

![so](/public/favicon.ico)


