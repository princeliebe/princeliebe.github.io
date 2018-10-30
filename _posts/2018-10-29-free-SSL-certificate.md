---
tags: IT
title: Let's Encrypt的免费SSL认证
excerpt: 备份留存
---


![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

----

测试环境：Vultr一键安装WordPress的LNMP，系统CentOS 6。

1. 首先安装git

先安装依赖包

```
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel

yum install gcc perl-ExtUtils-MakeMaker
```

再卸载旧版（如有）

```
   yum remove git
```

下载解压

```
cd /usr/src
wget https://github.com/git/git/archive/v2.5.0.tar.gz
tar -zxvf v2.5.0.tar.gz
```

注意：如果出现错误提示，可以先上去网址看看具体是哪个包，名字相应修改。

安装

```
cd git-2.5.0
make prefix=/usr/local/git all
make prefix=/usr/local/git install
echo "export PATH=$PATH:/usr/local/git/bin" >> /etc/bashrc
source /etc/bashrc
```

检查版本

```
git --version
```

返回以下即正确

```
git version 2.5.0
```

以git 方式安装certbot

```
git clone https://github.com/certbot/certbot
```

当然也可以用wget方式安装certbot-auto，它会自动安装相关依赖，certbot-auto使用与certbot一样。

```
wget https://dl.eff.org/certbot-auto -O /sbin/certbot-auto
chmod a+x /sbin/certbot-auto
```

注意：以上举例命令是把certbot-auto安装到sbin 目录下。

2. certbot方式认证

用winSCP登陆服务器，在根目录创建一个叫做.well-known 的隐藏文件夹，设置可以读写。注意文件夹前面有一点，才是隐藏文件夹。然后打开你网站域名的nginx设置文件。在苏歌的例子中，该文件放在`/etc/nginx/conf.d`中，对应的设置文件名字是wordpress_http.conf。根据当初安装环境，每个人的系统和安装目录不一定相同，对应的路径要随之修改。如果你和苏歌的安装环境一致，也不要用错文件，另外的那个wordpress_https.conf不要去管它。

在nginx设置文件的service模块，增加以下语句：

```
location ~ /.well-known {
allow all;

}
```

增加完以后，代码应类似如下这样：

```
server {

listen 80;

server_name //你的网站域名 如多个空格再写;

root /var/www/html/blog;

localtion / {

......

}

location ~ /.well-known {

allow all;

}

}
```
再次提醒，不是所有路径都一样，例如上述的root 路径，或者你的是没有blog这个目录。多看看语句，就大概知道什么意思。做完上述步骤，重启nginx。

```
service nginx reload
```

随后，

```
/sbin/certbot-auto certonly --webroot -w /var/www/html/blog -d 你的网站域名
```

这个命令的意思是：用安装在`/sbin`下的certbot-auto 仅作认证，网站的根目录在`/var/www/html/blog`处。如果你有多个域名，指向同一个网站IP，后面再加-d 另一个域名，就可以了。这样，两个域名都用同一张证书进行认证。

然后填写一些必要信息后，证书生成，保存在`/etc/letsencrypt/live/你的网站域名`下，当然，如果提示目录不存在，你可以手动建立“你的网站域名”文件夹，再试一次。

3. 配置nginx

在拿到证书后，我们要开始配置 Nginx 来使用这些证书。我们需要再一次打开网站的配置文件，并且让 Nginx 监听 443 端口、配置 SSL 地址以及配置 80 自动跳转。我们直接修改刚才那个配置文件，把 Listen 80; 改成 Listen 443 ssl; ，修改完之后的配置文件是这样的：

```
server {

listen 80;

server_name 你的域名;

return 301 https://$host$request_uri;

}

server {

listen 443;

server_name 你的域名;

root /var/www/html/blog;

ssl_certificate /etc/letsencrypt/live/你的域名/fullchain.pem;

ssl_certificate_key /etc/letsencrypt/live/你的域名/privkey.pem;

localtion / {

...............

}

location ~ /.well-known {

allow all;

}

}
```

第一段是80跳转，即http强制转到https，第二段监听443端口，打开ssl认证，其他就是你证书存放的位置。然后保存，重启nginx。报错的话，一般是路径问题，修改成自己的实际路径就可以。重启nginx前，使用`nginx -t`检查一下，也是很好的习惯。

LetsEncrypt的证书三个月有效，请记得续期。或者安装crontab做一个计划任务，让它自动续期。centos一般已经安装，未安装的自行搜索。

```
crontab -e
```

然后，粘贴以下命令

```
30 3 * * 1 /sbin/certbot-auto renew --quiet --no-self-upgrade

35 3 * * 1 /etc/init.d/nginx reload
```

保存退出。这个命令的意思是，每周一凌晨 3 点 30 分对证书进行续签，并且在 3 点 35 分重启一下 Nginx 。你可以安装自己的习惯自行修改，或者按官方隔两天更新一次也可以的！


需要注意的是，以上路径需要改为你安装certbot或certbot-auto的路径。

![so](/public/favicon.ico)


