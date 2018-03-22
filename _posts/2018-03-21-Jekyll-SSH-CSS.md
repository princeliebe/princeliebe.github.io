---
tags: IT Jekyll
title: 关于Github Pages的若干坑
excerpt: 可以随便，但选择唔求其
---

Also published on [S&C](https://soandcandy.us)

CC 4.0 BY-SA

----

* TOC
{:toc}


### 1. SSH key的生成坑 ###

处于试验效果，开启了两个不同账户的repo。为第二个repo开启**SSH key**的时候，遇到了一个小坑。关于Github SSH key的生成，手记如下：

#### Generating SSH key ####

1. 打开Teminal，像我们[前文](https://soyee.me/2018/03/12/Use-Github-Pages-and-Jekyll-Build-Bolg/)提到的，输入以下命令：

```bash
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

引号部分用你Github的注册邮箱代替。这里有一个小坑就是，如果你把别的账号之邮箱拿来生成了SSH key，用在本账号中，git push的时候就会一直用`别的账号`push。

2. 生成私钥和公钥的目录
```bash
  Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]
```

3. 密码
```bash
  Enter passphrase (empty for no passphrase): [Type a passphrase]
  Enter same passphrase again: [Type passphrase again]
```

4. 查看你的key
```bash
  ls -al ~/.ssh
```

5. 将你的SSH key加到ssh-agent
```bash
  ssh-add ~/.ssh/id_rsa
```

#### Add to Github ####

到你的Github账户**setting**处加入刚才生成的公钥


### 2. Permalinks的坑 ###

**Permalinks**就是每个post的固定地址。在`_config.yml`文件中，一般会有如下所示的定义：
```bash
  # Permalinks
  permalink:        pretty
```

务必注意`pretty`的定义，不同主题的定义不同，如果你更换主题，这个变量是不同的。



### 3. Jekyll图片自适应 ###

通常，Jekyll对于页面的图片是不会进行自适应的。即：不同分辨率的屏幕查看的页面表现均不同、不同设备查看页面均不同...

因此我们要通过别的美化措施来实现**图片随网页大小自动缩放**。在对page、post、default等模板的CSS定义文件中，增加以下语句：

{% raw %}
```bash
  img {
      max-width: 100%;
          height: auto;
              width: auto\9;
                  }
```
{% endraw %}

不要用别的其他命令，自适应最理想。

### 4. Git环境配置 ###

记录在此备忘

```bash
  $git config --global user.name "用户名"
  $git config --global user.email "你的邮件地址"
  $mkdir 用户名.github.com && cd 用户名.github.com
  $git init 
  $git remote add origin https://github.com/用户名/用户名.github.com.git
  $git pull origin master
```

该部分与SSH key生成相关，[回去看看](#Generating SSH key)




![icon](/public/favicon.ico)


