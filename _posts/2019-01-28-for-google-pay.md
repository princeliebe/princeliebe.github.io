---
tags: Android
title: Nexus 6P Android Pie downgrade.
excerpt: Nexus 6P降級
comments: true
---

![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

----

以往安卓手機的降級、回刷很簡單，拿官方ROM刷一下就可以了。但`Android 9.0`改變了數據加密方式，實施上述過程會有一點不同。

1. 下載**Full OTA**的ROM，注意不要使用`Factory Image`。
由於兩者在封裝上有些許不同，直接使用OTA的Zip文件即可。下載回來後放到手機內存中。

2. 進入recovery，直接刷入Zip文件。
刷入後需要WIPE，reset Factory Data。最好刷好以後**重啓到recovery**，再進行WIPE Data。

3. 重啓手機。

注意：如果已經在fastboot模式下進行了刷機操作，遇到**手機空間不足**類似提示，是因爲手機的數據加密方式改變而令它無法正確讀取區間。這時候你可以掛載Mount手機內存（系統、Data等），再把下載回來的刷機文件放進手機，切莫重啓。

![so](/public/favicon.ico)


