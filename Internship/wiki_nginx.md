# Nginx学习笔记

## Nginx在windows上的安装

**[官网下载地址](https://nginx.org/en/download.html) 选择 Windows 版本下载并解压**

![picture 1](images/d378b17e239edfe0a78984ec044f8ccbd63bfa756b28557d6991e5b7aaeedf55.png)  

<br>

## Windows下Nginx的启动、停止等命令

1. 启动

        start nginx

2. 停止

        nginx.exe -s stop
    或

        nginx.exe -s quit

    > stop是快速停止nginx，可能并不保存相关信息；quit是完整有序的停止nginx，并保存相关信息。

3. 重新载入Nginx
   
        nginx.exe -s reload

4. 重新打开日志文件

        nginx.exe -s reopen

5. 查看Nginx版本

        nginx -v

<br>

## Nginx配置文件nginx.conf详解

**参考文章1：**[Nginx 配置详解](https://www.runoob.com/w3cnote/nginx-setup-intro.html)

**参考文章2：**[Nginx配置文件（nginx.conf）详解，轻松掌握nginx~](https://blog.51cto.com/lidabai/5267712)

**nginx.conf配置文件**

```
#全局块：配置影响nginx全局的指令。一般有运行nginx服务器的用户组，nginx进程pid存放路径，日志存放路径，配置文件引入，允许生成worker process数等。
#user  nobody; #配置用户或者组，默认为nobody
worker_processes  1; #允许生成的进程数，默认为1，工作进程数量（根据硬件调整，通常等于CPU数量或者2倍于CPU）

#制定日志路径，级别。这个设置可以放入全局块，http块，server块，级别以此为：debug|info|notice|warn|error|crit|alert|emerg
#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid; #指定nginx进程运行文件存放地址


#events块：配置影响nginx服务器或与用户的网络连接。有每个进程的最大连接数，选取哪种事件驱动模型处理连接请求，是否允许同时接受多个网路连接，开启多个网络连接序列化等。
events {
    worker_connections  1024; #最大连接数，默认为1024
}


#http块：可以嵌套多个server，配置代理，缓存，日志定义等绝大多数功能和第三方模块的配置。如文件引入，mime-type定义，日志自定义，是否使用sendfile传输文件，连接超时时间，单连接请求数等。
http {
    include       mime.types; #定义MIME-Type（网络资源的媒体类型），nginx作为web服务器必须能够识别前端请求的资源类型。引用外部文件mime.types。
    default_type  application/octet-stream; #配置用于处理前端请求的MIME类型（默认为text/plain）

    #自定义格式
    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main; #配置服务日志的存放路径、日志格式、临时存放日志的内存缓存区大小

    sendfile        on; #允许sendfile方式传输文件，可以在http块，server块，location块。
    #tcp_nopush     on; #tcp_nopush = on 会设置调用tcp_cork方法，这个也是默认的，结果就是数据包不会马上传送出去，等到数据包最大时，一次性的传输出去，这样有助于解决网络堵塞。

    #keepalive_timeout  0;
    keepalive_timeout  65; #连接超时时间，可以在http，server，location块。

    #gzip  on; #开启Gzip功能，对响应数据进行在线实时压缩；

    #server块：配置虚拟主机的相关参数，一个http中可以有多个server。
    server {
        listen       80; #监听端口
        server_name  localhost; ##监听地址

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        ##请求的url过滤，正则匹配，~为区分大小写，~*为不区分大小写。
        location / {
            root   html; #根目录
            index  index.html index.htm; #设置默认页
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

}
```

<br>

## 如何解决Switchhosts提示没有写入 Hosts 文件的权限

推荐文章：[Switchhosts没有写入host文件的权限的解决方法](https://www.cnblogs.com/boboray/p/16453721.html)

<br>

## Nginx配置二级目录
**Nginx try_files配置**
<br>
推荐文章：[Nginx的try_files指令详解](https://blog.csdn.net/zzhongcy/article/details/110181195)

        location /abc {
            try_files /abc.html @qwe; #检测文件abc.htm,如果存在正常显示,不存在就去查找@qwe值
        }

<br>

## Location配置文件

推荐文章：[一文理清 nginx 中的 location 配置（系列一）](https://segmentfault.com/a/1190000022315733)

推荐文章：[nginx 详解](https://huaweicloud.csdn.net/6356112ed3efff3090b5995c.html?spm=1001.2101.3001.6650.7&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-7-118417969-blog-77199813.235^v27^pc_relevant_3mothn_strategy_and_data_recovery&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-7-118417969-blog-77199813.235^v27^pc_relevant_3mothn_strategy_and_data_recovery&utm_relevant_index=8)

```
#全局块：配置影响nginx全局的指令。一般有运行nginx服务器的用户组，nginx进程pid存放路径，日志存放路径，配置文件引入，允许生成worker process数等。
#user  nobody; #配置用户或者组，默认为nobody
worker_processes  1; #允许生成的进程数，默认为1，工作进程数量（根据硬件调整，通常等于CPU数量或者2倍于CPU）

#制定日志路径，级别。这个设置可以放入全局块，http块，server块，级别以此为：debug|info|notice|warn|error|crit|alert|emerg
#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid; #指定nginx进程运行文件存放地址


#events块：配置影响nginx服务器或与用户的网络连接。有每个进程的最大连接数，选取哪种事件驱动模型处理连接请求，是否允许同时接受多个网路连接，开启多个网络连接序列化等。
events {
    worker_connections  1024; #最大连接数，默认为1024
}


#http块：可以嵌套多个server，配置代理，缓存，日志定义等绝大多数功能和第三方模块的配置。如文件引入，mime-type定义，日志自定义，是否使用sendfile传输文件，连接超时时间，单连接请求数等。
http {
    include       mime.types; #定义MIME-Type（网络资源的媒体类型），nginx作为web服务器必须能够识别前端请求的资源类型。引用外部文件mime.types。
    default_type  application/octet-stream; #配置用于处理前端请求的MIME类型（默认为text/plain）

    #自定义格式
    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main; #配置服务日志的存放路径、日志格式、临时存放日志的内存缓存区大小

    sendfile        on; #允许sendfile方式传输文件，可以在http块，server块，location块。
    #tcp_nopush     on; #tcp_nopush = on 会设置调用tcp_cork方法，这个也是默认的，结果就是数据包不会马上传送出去，等到数据包最大时，一次性的传输出去，这样有助于解决网络堵塞。

    #keepalive_timeout  0;
    keepalive_timeout  65; #连接超时时间，可以在http，server，location块。

    #gzip  on; #开启Gzip功能，对响应数据进行在线实时压缩；

    #server块：配置虚拟主机的相关参数，一个http中可以有多个server。
    server {
        listen       80; #监听端口
        server_name  www.chenhanlin.com; ##监听地址

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        ##请求的url过滤，正则匹配，~为区分大小写，~*为不区分大小写。
        location / {
            root   html; #根目录
            index  chenhanlin.html index.htm; #设置默认页
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }

    server {
        listen       80; #监听端口
        server_name  www.kylin.com; ##监听地址

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        ##请求的url过滤，正则匹配，~为区分大小写，~*为不区分大小写。
        location ~ / {
            root   html; #根目录
            index  kylin.html index.htm; #设置默认页
        }

        location ~ ^/abc$ {
            try_files /abc.html @qwe; #检测文件abc.htm,如果存在正常显示,不存在就去查找@qwe值
        }

        location ~ ^/def$ {
            try_files /def.html @qwe; #检测文件def.htm,如果存在正常显示,不存在就去查找@qwe值
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }

    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}

}
```

<br>