---

title: Mac 下启动Apache 设置虚拟主机

---

### Mac 下启动Apache 服务器

​	1.打开终端，开启Apache

​		sudo apachectl start	//开启

​		sudo apachectl restart	//重启

​		sudo apachectl stop	//关闭

​		在浏览器输入 localhost 	网页出现 It works！

​	2.Apache 服务器的文件路径（/Library/WebServer/Documents)

​		浏览器默认加载的文件是index.html.en

​	3.测试

​		创建一个文件，如test.html

​		接下来访问 localhost/test.html

### 设置虚拟主机

​	Apache的默认根目录在 /Library/WebServer/下，配置虚拟主机后可以不理会默认的网站根目录，根据自己的需要在合适的地方建立不同的网站目录

1. 在终端运行“`sudo vi /etc/apache2/httpd.conf`”，打开Apche的配置文件
2. 在httpd.conf中找到“`#Include /private/etc/apache2/extra/httpd-vhosts.conf`”，去掉前面的“`＃`”，保存并退出。
3. 运行“`sudo apachectl restart`”，重启Apache后就开启了虚拟主机配置功能。
4. 运行“`sudo vi /etc/apache2/extra/httpd-vhosts.conf`”，就打开了配置虚拟主机文件httpd-vhost.conf，配置虚拟主机了。需要注意的是该文件默认开启了两个作为例子的虚拟主机：

``` 
<VirtualHost *:80>
    ServerAdmin webmaster@dummy-host.example.com
    DocumentRoot "/usr/docs/dummy-host.example.com"
    ServerName dummy-host.example.com
    ErrorLog "/private/var/log/apache2/dummy-host.example.com-error_log"
    CustomLog "/private/var/log/apache2/dummy-host.example.com-access_log" common
</VirtualHost>
 
<VirtualHost *:80>
    ServerAdmin webmaster@dummy-host2.example.com
    DocumentRoot "/usr/docs/dummy-host2.example.com"
    ServerName dummy-host2.example.com
    ErrorLog "/private/var/log/apache2/dummy-host2.example.com-error_log"
    CustomLog "/private/var/log/apache2/dummy-host2.example.com-access_log" common
</VirtualHost>
```

而实际上，这两个虚拟主机是不存在的，在没有配置任何其他虚拟主机时，可能会导致访问localhost时出现如下提示：

```
Forbidden
You don't have permission to access /index.php on this server
```

最简单的办法就是在它们每行前面加上#，注释掉就好了，这样既能参考又不导致其他问题。

5.添加如下配置

```
<VirtualHost *:80>
    DocumentRoot "/Library/WebServer/Documents"
    ServerName localhost
    ErrorLog "/private/var/log/apache2/localhost-error_log"
    CustomLog "/private/var/log/apache2/localhost-access_log" common
</VirtualHost>
 
<VirtualHost *:80>
    DocumentRoot "/Users/snandy/work"
    ServerName mysites
    ErrorLog "/private/var/log/apache2/sites-error_log"
    CustomLog "/private/var/log/apache2/sites-access_log" common
    <Directory />
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order deny,allow
                Require all granted
                Allow from all
      </Directory>
</VirtualHost>
```

保存退出，并重启Apache。

6.运行“`sudo vi /etc/hosts`”，打开hosts配置文件，加入"`127.0.0.1 mysites`"，这样就可以配置完成sites虚拟主机了，可以访问“http://mysites”了，在10.8之前Mac OS X版本其内容和“http://localhost/~[用户名]”完全一致。

7.注意，记录log的“`ErrorLog "/private/var/log/apache2/sites-error_log"`”也可以删掉，但记录日志其实是一个好习惯，在出现问题时可以帮助我们判断。如果保留这些log代码，一定log文件路径都是存在的，如果随便修改一个不存在的，会导致Apache无法服务而没有错误提示，这个比较恶心。
