---
tags: IT Jekyll
title: 为站点增加几个常用功能
excerpt: e.g. Google Analytics, Share button, Social, etc.
---


Also published on [S&C](https://soandcandy.us).
![CC](https://creativecommons.org/licenses/by-sa/4.0/)

----

**给站点增加了几个常用功能，笔记如下。**

### Post Archives ###
按照站点选择的方式或主题不同而各有异同。主要的语法是：

#### archives.html 文件 ####

通常`archives.html`文件会放在站点根目录下方便访问和放置。它的主要内容是：


{% raw %}
```bash
{% for post in site.posts %}
  {% capture month %}{{ post.date | date: '%m%Y' }}{% endcapture %}
    {% capture nmonth %}{{ post.next.date | date: '%m%Y' }}{% endcapture %}
        {% if month != nmonth %}
              {% if forloop.index != 1 %}</ul>{% endif %}
                    <h5>{{ post.date | date: '%B %Y' }}</h5><ul>
                        {% endif %}
                          <li><span class="time">{{ post.date | date: "%d/%m/%Y" }}</span>    <a href="{{ post.url }}">{{ post.title }}</a></li>
                          {% endfor %}
```
{% endraw %}

文件的作用就是按时间为分类list post。那么，我们需要在某个或某些页面放置一个链接，方便访问。以本站点为例，这个链接放置在侧栏中：

{% raw %}
```bash
<li class="sidebar-nav-item"><a href="{{ site.baseurl }}/archives/">Posts Archives</a></li>
```
{% endraw %}


或者，有时你需要在主页上放置一个链接，例如：


{% raw %}
```bash
      {% if page.archives %} <a href='{{ site.baseurl }}{{ page.archives }}'> Posts</a>{% endif %}
            {% endif %}
```
{% endraw %}


根据站点的实际情况进行修改即可。


### 404 页面 ###

Github Pages默认有一个404页面，如果你需要自定义，404页面的跳转也很简单。

1. 在你的站点repo中，切换至`master`分支，根目录下新建一个`404.html`或`404.md`文件；
2. 在404文件开头设置YAML头信息，如`permalink: /404.html`；
3. 增加其它你希望在404页面显示的内容；
4. 收工或push完了收工。


Github能够从YAML头信息处得知那就是你希望跳转的404页面。如图所示：

![404](https://i.imgur.com/ZIaQbUq.png)


### 社交按钮 ###

主要分两步进行：

#### 1. 录入社交账号信息 ####

在站点设置文件`_config.yml`中放入类似以下的内容：

```bash
twitter_username:  princeliebe
```


#### 2. 显示页面增加按钮 ####

以twitter为例，在相应的页面中，放入以下语句：

{% raw %}
```bash
      {% if site.twitter_username %}
            <a href="https://www.twitter.com/{{ site.twitter_username }}" target="_blank" style="text-decoration:none">
                    <i class="fa fa-fw fa-twitter"></i>
```
{% endraw %}


### 增加分享选项 ###

计划进行的是：读者浏览post的时候，文末增加**分享**按钮，例如分享到twitter。我们需要做的就是在post的layout模板里面，增加一段语句：

{% raw %}
```bash
<footer class="post-footer">
             <section class="share">
                             <h5>分享|Share</h5>
                                             <a class="icon-twitter" href="https://twitter.com/intent/tweet?text=&quot;{{ page.title }}&quot;%20{{ site.url }}{{ page.url }}%20via%20&#64;princeliebe">
                                                                 <span class="hidden">Twitter</span>
                                                                                 </a>
                                                                                             </section>     
                                                                                                     </footer>
```
{% endraw %}

如上述语句中，`分享 | Share`的内容、`via`后面的内容，可根据自己的实际情况设置。其他分享按钮做法类似。


想到再补充。

![So](/public/favicon.ico)


