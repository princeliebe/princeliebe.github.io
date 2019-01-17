---
tags: IT
title: 建立数据库连接时出错
excerpt: WordPress经常出现这错误
comments: true
---


![cc](/public/cc.png) Also published on [S&C](https://soandcandy.us)

----

晚上登陆网站的时候，随意点开链接发现出错，提示：建立数据库连接时出错。由于此前有过一次删除虚拟主机重新部署的惨痛经历，这个出错提示着实吓我一跳。

之前，由于遗忘数据库密码，用了过期的办法修改wp_option.php以致数据库奔溃，不得不重头再来。自那以后亦备份了重要的设置文件以防不测。此番看到是数据库问题，便首先想到可能是wp_option的问题。

1. WordPress配置中的数据库登陆凭据不正确

用WinSCP上传wp_option.php备份文件至服务器，覆盖。失败。提示：建立数据库连接时出错。

2. 数据库表损坏

有时升级、安装插件或配置错误，均可能导致数据库表损坏。不明来历而且未经查看的插件最好谨慎安装。如果是这样，可以启动内置的修复程序尝试修复。因无访问限制，涉及安全问题，默认情况下它是被禁用的。我们通过对wp_option.php文件进行编辑：

 

```
   sudo nano /var/www/html/wp_config.php
```


如果是管理员账户则不需要sudo。在空白行添加代码：

 
```
define('WP_ALLOW_REPAIR ', true);
```


然后登陆https或`http://域名/wp-admin/maint/repair.php`尝试修复。如果成功，需要删除刚才输入的代码。对于我，失败。提示依旧是：建立数据库连接时出错。

3. 亲爱的数据库崩溃

我开始怀疑数据库是不是偷懒了。通常WordPress对主机的资源占用较多，数据库亦同样。如果网站访问人数急增，常常会引起崩溃。或者，虚拟主机的内存较小时，也经常引起程序崩溃。因为系统会kill掉进程。于是开始查看程序的内存占用：

 
```
sudo netstat -plt
```
 

果然去偷懒了！里面没有mysql 或类似的服务。于是手动启动。问题解决。

如果不放心，可以查看开机启动项目，看看有没mysql 进程，没则添加进去即可。




![so](/public/favicon.ico)

