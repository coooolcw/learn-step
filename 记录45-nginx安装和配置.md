安装  
`sudo apt-get install nginx`  
  
版本确认  
`nginx -v`  
  
启动  
`service nginx start`  
  
各个指令
`sudo service nginx {start|stop|restart|reload|force-reload|status|configtest|rotate|upgrade}`  
  
  
配置教程  
  
/usr/sbin/目录下是nginx命令所在目录，在/etc/nginx/目录下是nginx所有的配置文件，用于配置nginx服务器以及负载均衡等信息  
  
服务启动  
nginx  
服务停止  
$ nginx -s stop  
or  
$ nginx -s quit  
  

  
中文手册  
http://www.nginx.cn/doc/index.html  
  
简单的静态部署  
文件位置在/etc/nginx/  
修改sites-enabled中的default文件并重命名  
  
修改其中的字段  
```
server {
	listen 80;#监听端口

	root /web/dist;#静态文件目录


	server_name www.cooolcw.com; #匹配域名或者子域名

	location / {
		try_files $uri $uri/ =404;#匹配到的页面都导向404页面
		此段修改为
		try_files $uri $uri/ /index.html;  #将各种请求都重定向到index.html(毕竟单页应用)
	}
}
```
  
nginx的gzip启用  
  
配置位于/etc/nginx/nginx.conf  
  
https://www.cnblogs.com/kevingrace/p/10018914.html  
  
设置为
```
gzip on;

gzip_vary on;
# gzip_proxied any;
gzip_comp_level 6;
gzip_buffers 16 8k;
# gzip_http_version 1.1;
gzip_types text/plain text/css application/json application/javascript text/xml application/xml application/xml+rss text/javascript;
```


