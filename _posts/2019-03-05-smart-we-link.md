---
tags: IT
title: 平價智控方案
excerpt: 比智能插頭更便宜的控制方式
comments: true
---

![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

自從上次實施了[簡單的NFC或QR控制智能家居一例](https://soyee.me/2019/02/15/nfc-tag-toggle/)以後，芝麻同學每次回房睡覺都會對着他的小夥伴喊：“Goo Goo!”，意圖自行開燈。當然他仍不懂喚醒Google Assistant的Magic Word是要“Hey，Goo Goo!”。好動如他卻迷上另一樣東西。

![Imgur](https://i.imgur.com/pShHZRz.jpg)

他喜歡在媽媽看你電視的時候關掉插座。我只有尋覓一個他暫時關不掉的方案。換掉插座嘛？當然要是換，但是家中的盒子因爲遙控被芝麻藏起來找不到，仍然需要**開**、**關**這個動作，沒有開關的插座要拔來拔去實在麻煩。但如果開關是音控的，就愜意許多了。於是**兒子開關**（誤）**SONOFF**便是首選。

![Imgur](https://i.imgur.com/d6Hdv7r.jpg)

#### 選擇理由 ####

**首先是便宜**。6刀的價格比動輒20刀、30刀的智能插座有些優勢。其次是**適合多個電器控制**。由於看電視需要同時用到**電視盒子**、**音響**、**電視（顯示屏）**，把他們統統插在插座上，一起控制是最好的方式。再次，它**支持多種控制方式**，譬如Google Assistant、Alexa、IFTTT等。

唯一的缺點可能就是，它需要接線。遇上需要接地線的電器，它就沒有了接地線的功能。


#### 安裝使用 ####

這款迷你智能開關的安裝使用十分簡單。

只需要把插座的**零線**插入**N**口，**火線**插入**L**口，兩端同樣處理即可。唯一需要注意的是，美標零線一般是白色，如果線體沒有標識，插座的寬口就是零線。火線則是黑色，或插座的窄口。

![Imgur](https://i.imgur.com/0LVsGKe.jpg)

而在中國，除了看N或L的標識，零線一般是藍色，火線則爲紅色。

接線以後，下載說明書中的App，**eWeLink**安裝。

- 手機連上WiFi；
- 打開eWeLink新增設備（可能需要授權給它獲取無線網絡）；
- 按着迷你智能開關的黑色按鈕5秒，LED快速閃爍；
- 應用就會自動識別設備。

![Imgur](https://i.imgur.com/WqusUHV.png)

新增全部設備後，你打開Google Assistant或Alexa等智能助手新增與**Smart We Link**、**eWeLink Smart Home Fan**（Alexa中）的連接，就可以使用上述語音助手控制。

當然，你也可以參照前一篇文章中IFTTT的設置，使用IFTTT控制它們。

![Imgur](https://i.imgur.com/kTvI8ht.jpg)

你大概能夠利用它來：

- 定時控制；
- 回家、離家自動開關；
- 設置按鈕控制；
- 郵件報警；
- 利用Google Sheet記錄開關歷史。
- 自行設計Trigger。

如此一來，只要設置妥當，當我離家的時候，它就可以自動幫我關掉暖氣、冷氣，媽媽說我再也沒有健忘症了。


![so](/public/favicon.ico)


