---
tags: IT
title: Simple to control
excerpt: 簡單的NFC或QR控制智能家居一例
comments: true
---

![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

#### 事由 ####

自上次家裏偶爾出現的一起事件，再度萌生了利用智能手段控制家居、家電的想法。而粗略瀏覽了市面現有的各式**智能家居**產品，不外乎燈光、空調、監控設備、洗衣機、烘衣機等等，作爲過渡的連接產品，智能插頭、開關、調節器等亦不少。可惜作爲煮飯佬的好幫手，智能控制煤氣爐的連接產品並未上市。唯一一款完成衆籌**Inirv**家的Smart Konb也只是在預購階段。

但芝麻同學十分喜歡和**Google Assistant**說話，十分喜歡幫爸爸媽媽開燈、關燈、沖水...做家務。於是趁着貝爾金家的**wemo smart plug**有折扣，敗了兩個。

這款smart plug和市面大多數同類產品一樣，除了本廠App以外，基本支持Google Assistant以及Amazon Alexa的語音控制。但這些沒有給你**折騰**的地方。於是把目光瞄向**NFC**。

##### 應用場景 #####

1. 遺忘補救

離家後發現，尚未關閉某電器**電源**！此處電器是不夠智能的，包括但不限於**電磁爐**、**冷暖氣**、**音響**諸如此類。

2. 預先控制。

譬如回家前先把空調打開。又或者不想**摸黑開燈**。又或者營造**有人在家**的場景等等。

##### 需要設備 #####

- 開啓NFC的手機
- 智能開關如本文的wemo smart plug
- 可寫入的NFC tag及應用App
- 開啓IFTTT開發者平臺Maker Channel

當然，除了本文折騰的NFC方式，你還可以利用**IFTTT**的功能，設置更多個性化的控制手段，例如短信、電話、郵件等控制方式。

#### 簡易教程 ####

折騰的思路是：把一條web信息寫入NFC tag，當手機接觸NFC tag時，利用IFTTT的服務控制wemo開關。

##### IFTTT #####

Maker Channel現在是IFTTT開發者平臺的功能之一，17年已更名爲**Webhooks service**。使用該服務，你仍需要開啓了開發者平臺，目前是免費的。開啓後，你需要新增你的Service，簡單填寫你Service的名字、描述、分類等信息即可。

回到IFTTT，新增一個Applet。

![New Applet](https://i.imgur.com/IbhdFYX.png)

**this**選擇**webhooks**，**Event Name**隨意填寫，例如Light。

![webhooks](https://i.imgur.com/cmc0U1B.png)

![event](https://i.imgur.com/hQsXaTj.png)

**that**選擇你要控制的服務，例如本文是wemo smart plug。某些服務需要它授予IFTTT權限認證。

##### 授權 #####

在本文中，wemo處於安全考慮，需要在它家的App上授予IFTTT權限。下載wemo App，在setting的**connect to our smart home partners**即可完成認證。

##### web信息 #####

在[IFTTT](https://ifttt.com/maker_webhooks)的webhooks服務，setting處可以查到你的web信息。打開這個web後，可以看到**To trigger an Event**的提示，在event處填入你之前填寫的event name（本文是Light），把整條網址抄下來。

##### 寫入NFC tag #####

使用如NFC tools的寫入應用，新增一條URL記錄，內容就是上述網址。寫入tag即可。當你每次接觸NFC tag的時候，就能控制。

#### 中國式應用 ####

根據IFTTT服務webhooks的原理，你也可以把上述的網址轉換成**QR**編碼，**掃一掃**也能實現控制功能。

需要謹記的是，**切莫泄漏**你的QR編碼，切莫泄漏你的控制web信息，不然我家芝麻就來幫你開燈了。


![so](/public/favicon.ico)


