vps阿里云国际-新加坡  
选择原因:价格比香港服务器低,延迟稍高,最大带宽30M,同样无需备案  
  
系统Ubuntu 18.04 64bit  
使用nvm管理node  
https://github.com/creationix/nvm  
参考教程为:(在页面较下位置)  
https://www.ostechnix.com/install-node-js-linux/  
待学习的使用方法说明  
https://www.kancloud.cn/summer/nodejs-install/71975  
  
验证  
输入nvm list  
输出default -> node (-> v11.14.0)  
node -> stable (-> v11.14.0) (default)  
stable -> 11.14 (-> v11.14.0) (default)  
  
在vps上建立项目文件夹  
cd到该文件夹  
将资源文件上传至vps  
  
安装express  
https://expressjs.com/zh-cn/starter/installing.html  
输入npm init 全部回车解决  
  
之后暂缓  
等vue学完一起进行  
  
  
ssh基础参考(未使用)  
http://www.ruanyifeng.com/blog/2014/03/server_setup.html  
  
ssh端口配置修改  
修改不需要前面带#  
直接输入Port \*\*\*\*\*   即可  
https://blog.csdn.net/Wangdada111/article/details/77406423  
https://help.aliyun.com/knowledge_detail/41212.html?spm=5176.2000002.0.0.63052f4aVdPs58  
  
待用  
https://segmentfault.com/a/1190000010098126  
https://segmentfault.com/a/1190000010205995  
https://segmentfault.com/a/1190000010213434  
https://segmentfault.com/a/1190000010281512  
  
一个较好的教程库  
js  
https://wangdoc.com/javascript/elements/index.html  
nodejs  
http://javascript.ruanyifeng.com/nodejs/basic.html  
  
git的使用教程  
https://www.liaoxuefeng.com/wiki/896043488029600  
  
git无法安装,使用  
sudo apt-get update更新一下再进行安装  
指令为  apt-get install git  
  
安装pm2  
npm install -g pm2  
pm2操作  
http://pm2.keymetrics.io/docs/usage/quick-start/  
