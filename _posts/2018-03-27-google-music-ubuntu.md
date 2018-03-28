---
tags: blog IT
title: 从网易云音乐转投Google Play Music之路
excerpt: Sometimes I miss the CD so much.
---

![cc](/public/cc.png)Also published on [S&C](https://soandcandy.us)

----


在90年代之前，音乐是一个完全不同的世界。《请回答，1988》里有意记录了这样的细节：从卡带到光盘的演变历史。然而1994至1996年间，MP3渐渐出现在全世界的音乐当中。二十多年过去，数字化和在线音乐已然成为主流。唱片公司从最开始激烈的抗拒变成主动运用，而版权战争未曾消停过，尤其是各种新手段、网络技术的发展加剧了混乱局面。


与中国目前的**版权割据**、**合而治之**的*头痛医头，脚痛医脚*不同，在美的在线音乐服务是一个成熟的体系。[Pandora](https://www.pandora.com/)、[Spotify](https://www.spotify.com/)、Apple Music、Google Play Music乐库大体相同，服务各异。只需要方便自己的设备接入即可。

相对于翻墙回去**卡顿**地享受例如网易云音乐这类服务，不如转投流畅的高音质同类产品中去。


### 多平台享受Google Play Music服务 ###

#### 电脑端管理 ####

系统：Ubuntu 16.04 LTS
管理：无损音乐转换、上传自有曲目
软件：**SoundConverter**、**cuetools**、**shntool**

以上提到的软件应用主要用途是进行cue文件拆分flac，音乐格式转换。首先安装软件：

- 在Ubuntu Software中安装SoundConverter。
- 命令行下安装cuetools和shntool。

```bash
sudo apt-get install cuetools shntool
```


值得一提的是Soundconverter是gnome下的图形化软件，Ubuntu 16.04 LTS换了桌面图形应用，因此源码安装的不适用，要安装Ubuntu Software的版本。

Google Play Music不能播无损格式，因此需要把我们自有的音乐上传mp3格式的。如果不是，则需用SoundConverter进行转换。


**如果格式是ape的多首曲目**

1. 先把ape转换称flac格式，把文件放到cue所在目录；
2. 运行`cuebreakpoints "CDImage.ape.cue" | shntool split -o flac "CDImage.flac"`命令，按cue文件的分隔，把flac文件分拆；
3. 重命名各个flac文件，批量转成mp3；
4. 上传到Google Play Music。

![示意图](https://i.imgur.com/0OJO6MG.png)


如果遇到cue是乱码的情况，把文本编辑器的格式换成中文或**UTF-8**即可。


#### 设备端同步 ####

上传完成后，各设备端都能在线播放了。也可以下载到设备端离线播放。


![So](/public/favicon.ico)



