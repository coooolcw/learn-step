mongoDB基础教程  
===
  https://www.runoob.com/mongodb/mongodb-tutorial.html  
  菜鸟站,感觉一般般  
  
1.安装
===
主要注意点:  
https://stackoverflow.com/questions/52092528/invalid-domain-user-password-while-installing-mongodb-on-windows10  
在选择安装到系统服务/本地服务时,需要输入的账号密码是windows的账号密码  
domain则为.  

2.windows平台记得使用cmd不要使用powershell,不识别可执行文件  
===
win10打开管理员权限的cmd方法:搜索cmd然后右键.在运行中输入cmd则无法选择权限  
  
使用:  
===
1.运行  
---
使用cmd管理员权限cd到安装目录`C:\Program Files\MongoDB\Server\4.2\bin`  
语法  
`$ cd "C:\Program Files\MongoDB\Server\4.2\bin"`  
  
2.系统path配置  
---
系统属性==>高级==>环境变量==>系统变量==>path  
添加`C:\Program Files\MongoDB\Server\4.2\bin(可直接游览添加)`  
确定后生效  
    
3.mongo启动自动配置设置  
---
https://docs.mongodb.com/manual/administration/configuration/  
      
基础指令  
https://docs.mongodb.com/manual/tutorial/manage-mongodb-processes/  
默认值启用:mongod(一般不配置会报错)  
    
启动配置项:  
指定存储目录(例如存储在/srv/mongodb路径中)  
`mongod --dbpath /srv/mongodb/`  
    
指定tcp端口(端口12345)    
`mongod --port 12345`    
    
守护进程启动,并且输出日志  
`mongod --fork --logpath /var/log/mongodb.log`  
      
根据conf配置启动  
`mongod --config D:\mongodb\etc\mongo.conf`  
      
基本配置  
===
https://docs.mongodb.com/manual/administration/configuration/  
1.windows的cmd中,守护进程似乎有点问题  
例子中的conf配置  
    
```
processManagement ：  
  fork ： true 
```
需要删除   
linux应该是需要此配置的    
      
本地使用的配置  
```
      net:
         bindIp: localhost
         port: 27017
      storage:
         dbPath: D:/mongodb/data
      systemLog:
         destination: file
         path: "D:/mongodb/log/mongod.log"
         logAppend: true
      storage:
         journal:
            enabled: true
```
  
安全配置  
在windows中使用暂时可以直接bindIp: localhost,但是在vps上必须配置此项目  
https://docs.mongodb.com/manual/administration/configuration/#security-considerations  
例子  
```
      net:
         bindIp: localhost,10.8.0.10,192.168.4.24,/tmp/mongod.sock
      security:
         authorization: enabled
```  

安全相关  
===
    https://docs.mongodb.com/manual/security/  
    在vps架设时再回来查阅  
      
windows服务相关 
===
安装服务  
`mongod --config D:\mongodb\etc\mongo.conf --install`   
此时可按照运行指令进行配置  
删除服务
cmd中运行  sc.exe delete MongoDB
或者mongod.exe --remove --serviceName "MongoDB"  
    
也可以在bin下修改mongod.cfg文件(未尝试)
    
atlas 
===
配置和使用  
https://www.tracymc.cn/archives/1430  
  
  
linux平台的安装  
===
根据官方文档https://docs.mongodb.com/manual/tutorial/install-mongodb-on-ubuntu/    
依次输入    
`wget -qO - https://www.mongodb.org/static/pgp/server-4.2.asc | sudo apt-key add -`  
`echo "deb [ arch=amd64 ] https://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list`  
`sudo apt-get update`  
`sudo apt-get install -y mongodb-org`  
  
linux相关文件位置 
===
conf文件  
/etc/mongod.conf  
data文件夹  
/var/lib/mongodb  
log文件夹  
/var/log/mongodb  

linux平台指令  
===
sudo service mongod start  
sudo service mongod stop  
sudo service mongod restart  
  
linux平台安全配置  
===
基本配置已经自动设置完了,暂时不启用账号,只允许本地连接

linux平台mongoshell配置
===
默认安装后的可执行文件目录  
/usr/bin  
添加到path的指令  
`export PATH=user/bin:$PATH`  
此后即可直接输入mongo使用mongoshell

mongoshell常用指令
===
`db`显示正在使用的db  
  
`use <database>`切换使用的数据库,若不存在会创建  
  
`show dbs`显示可用的数据库  
  
创建一个数据库和集合  
```
use myNewDatabase
db.myCollection.insertOne( { x: 1 } );
```
[shell指令速查](https://docs.mongodb.com/manual/reference/mongo-shell/)  
  
[mongodb import](https://docs.mongodb.com/manual/reference/program/mongoimport/)  
[mongodb export](https://docs.mongodb.com/manual/reference/program/mongoexport/)  
  
import指令范例(注意不要在mongoshell内使用,这是独立的可执行文件)  
`mongoimport --db cwweb --collection cwblogs --file /web/mongodbcache/blogs.json`


mongoose
===
中文文档  
https://mongoosedoc.top/  
http://www.mongoosejs.net/  
英文官网  
https://mongoosejs.com/  
  
增删改查  
https://www.cnblogs.com/tugenhua0707/p/9256605.html  
