---
tags: Markdown
title: 在Markdown中插入视听文件及其他
excerpt: Markdown语法并不支持音频、视频，那么如果处理视听文件？
---

![CC](/public/cc.png)Also published on [S&C](https://soandcandy.us).

----

* TOC
{:toc}


**Google Analytics**

先把Github Pages的一个*坑*填上。如果我们希望对自己的站点进行**网站流量**分析、统计，多数情况下是用**Google Analytics**。这个服务是05年的时候Google收购了它的前身Urchin，将收费服务开放免费使用。

它是把一段JS代码放入页面，每当运行该页面时，即会发送浏览者的国家、经由关键字等信息传递给站长。

我们先在[Google Analytics](https://analytics.google.com)开一个Account，设置property，Google Analytics就会给出Tracking Info，包括你的**Tracking ID**，和**Website Tracking**的JS代码。

- 把Tracking ID放入`_config.yml`文件中(option)；
- 把GA提供的JS代码放入`default`模板或者需要的页面中。

页面可以是在`_includes`下新建的一个`analytics.html`文件，单独在里面放置代码。


### Markdown插入视听文件 ###

事实上Markdown并不支持插入音频、视频，但是，Markdown支持**html**语法，我们可以通过html语句插入视听文件。用到的html标签是`iframe`，代码解释如下：

- div用于控制格式，若无则默认为居左；
- frameborder用于规定是否显示框架周围的边框，1为是，0为否；
- marginwidth及marginheight表示距离边缘的像素大小；
- width及height表示播放条的长度和宽度；
- src为播放链接，可以在如网易云音乐的生成外链播放器获取该链接，同时也获得以下代码，并可以自行更改；
- 也可将音频链接改为视频链接，从而播放视频。


**注意：**

音频和视频在默认情况下是会自动循环播放的，可以修改链接的值进行修改；

在src域中，auto值表示是否自动播放，当值为1时为自动播放，0则不是；

在src域中，有些链接会附有height或width值，其表示表示播放框的基本宽高，可以更换其值以获得想要的播放框大小，此时可以不用填写外部的width及height。

我们用一个例子来说明一下：

{% raw %}
```bash
<div> 
<iframe frameborder="no" marginwidth="0" marginheight="0" width=400 height=140 src="https://music.163.com/outchain/player?type=2&id=431610389&auto=0&height=66"></iframe>
</div>
```
{% endraw %}


效果如下：

{% include music.html id=431610389 %}

视频也可以，亦Youtube为例：


{% include youtube.html id=hIjhXLkFjPQ %}


由于版权保护问题，尤其现在中美贸易战，可能有的地区无法试听。吹神的**I DO**是找了这么多首能在US试听的歌了。但无法生成外链了。


### Markdown 折叠 ###

其实这也是通过`html`语法实现的功能，你可以测试一下（拒绝IE，它不支持）：

<details>
  <summary>我有些话想跟你说</summary>
    <p> 等等，让我想想是什么话。</p>
      <p> 哎呀，忘记了。</p>
      </details>


实现上述折叠效果的代码如下：

{% raw %}
```bash
<details>
  <summary>我有些话想跟你说</summary>
    <p> 等等，让我想想是什么话。</p>
      <p> 哎呀，忘记了。</p>
      </details>
```
{% endraw %}



### Markdown插入表格 ###

终于是一个Markdown本身就支持的功能了。**表格**、**制表**是我们在写作当中常用的一个功能。我们先看一个例子，看看在Markdown里用几行代码插入表格的效果是怎么样的：

{% raw %}

```
   | 一个普通标题 | 一个普通标题 | 一个普通标题 |
   | ------| ------ | ------ |
   | 短文本 | 中等文本 | 稍微长一点的文本 |
   | 稍微长一点的文本 | 短文本 | 中等文本 |

```
{% endraw %}

效果如下：


   | 一个普通标题 | 一个普通标题 | 一个普通标题 |
   | ------| ------ | ------ |
   | 短文本 | 中等文本 | 稍微长一点的文本 |
   | 稍微长一点的文本 | 短文本 | 中等文本 |


稍微再加一点要求，例如：**对齐**

```
   | 左对齐标题 | 右对齐标题 | 居中对齐标题 |
   | :------| ------: | :------: |
   | 短文本 | 中等文本 | 稍微长一点的文本 |
   | 稍微长一点的文本 | 短文本 | 中等文本 |

```

出来的表格样式则是这样：

| 左对齐标题 | 右对齐标题 | 居中对齐标题 |
| :------| ------: | :------: |
| 短文本 | 中等文本 | 稍微长一点的文本 |
| 稍微长一点的文本 | 短文本 | 中等文本 |


从上面的例子我们可以看到：

- 默认情况下，**标题栏居中对齐**，**内容居左对齐**；
- `|`、`-`、`:`这些符号之间，多余的空格会被忽略，布局由Markdown部署；
- `-:`表示内容和标题栏居右对齐；
- `:-`表示内容和标题栏居左对齐；
- `:-:`我们都猜到了，居中；
- `|`分隔**单元格**，`-`分隔表头和内容。


表格内支持插入其他Markdown**行内标记**，例如**加粗**、**斜体**、**链接**等等。


![SO](/public/favicon.ico)


