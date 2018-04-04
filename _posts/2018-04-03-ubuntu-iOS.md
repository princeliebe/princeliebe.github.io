---
tags: Systems Media
title: 在Linux下手工同步iOS
excerpt: iOS外号更新一次麻烦一次真没叫错
---


![cc](/public/cc.png)Also published on[S&C](https://soandcandy.us).


* TOC
{:toc}


----

用iOS设备有个烦人的问题，什么玩意都要iTunes，我不高兴用iTunes。仅仅支持OSX、Windows不说，耗费资源，Windows下还半死不活的，性子急一点的估计把键盘拍烂了。


以前它还出过Linux客户端的，得了，到后面直接没了。随着近段时间一下一个更新，一下又一个更新，老方法们都失效了，重新折腾。


### 写在前面 ###


- 系统：Ubuntu 16.04 LTS
- 设备：iPad Air iOS为11.2.5


手工同步仅仅是提供iTunes的类似功能，解决Liunx下连接iOS设备的问题。其他如**导出某云音乐**，安装破解版、盗版App的，可以右上角X了。实现的方法目前只能是**越狱**，不想越狱的话，只能是ipa破壳。


#### 软件列表 ####

部分已经系统自带，或可能版本较低需升级一下。在进行`./configure`或者`./autogen.sh`时会有提示。

- libusb
- usbmuxd
- libplist
- libimobiledevice
- libfuse
- ifuse
- meson
- ninja

其他软件例如

- make
- autoheader
- automake
- autoconf
- libtool
- pkg-config
- gcc
- cython
- OpenSSL

等等，通常已经自备，或者按安装提示按需安装就好。


### 连接iOS设备 ###

**Documents**通常会自动弹出。这个**Documents**其实是后来Apple加入的所谓**文件共享**功能，ipa内需要有键值**UIFileSharingEnabled**为*YES*。否则会显示：

```bash
  Failed to start AFC service 'com.apple.mobile.house_arrest' on the device.
```


![1](https://i.imgur.com/TLVXpCq.png)


1. 建立新目录，如`/home/zhang/air`；
2. 插上数据线，点击iOS设备弹出的**信任**；
3. 命令`ifuse /home/zhang/air`，挂载媒体库。

如果要挂载根目录root，需要越狱并安装AFC2服务。输入命令`ifuse --root /your dir`的时候会提示：

```bash

This service enables access to the root filesystem of your device.
Your device needs to be jailbroken and have the AFC2 service installed.
```


![2](https://i.imgur.com/PfKoOBz.png)


挂载媒体库以后，就可以用Linux系统自带的媒体管理软件对设备的文件进行管理，手工同步。

如音乐管理可采用**Rhythmbox**，图片可用**ShotWell**之类。

![3](https://i.imgur.com/bPb3J0o.png)


### 手工同步后 ###


卸载挂载点，`fusermount -u /your/DIR`即可。



更多ifuse命令[参考这里](https://github.com/libimobiledevice/ifuse)。


![so](/public/favicon.ico)


