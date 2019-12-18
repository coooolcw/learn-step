根据工作实际修改

本地创建ssh以及登陆到github  
https://www.liaoxuefeng.com/wiki/896043488029600/896954117292416  
  
  
手把手git教程  
https://blog.csdn.net/qq_36150631/article/details/81038485  
  
  
主要指令  
1.`git init`  
一般用cli不需要输入  
2.`git add .`  
添加目录下所有文件到git的仓库  
3.`git commit -m "更新描述"`  
注意更新描述必须输入,可以是中文  
文件提交到仓库(保存)  
4.`git remote add origin *****`(github上的地址)  
添加远程目录  
把一个已有的本地仓库与之关联  
origin可修改,一般不变,表示是远程库  
5.`git push -u origin master`(第一次推送)  
把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程  
以后推送  
`git push origin master`  
  
  
其他指令  
1.`$ git status`  
查看状态,修改和提交情况  
2.`$ git diff`  
查看不同  
3.`$ git reset --hard HEAD`  
回复上n次commit的状态  HEAD表示当前版本  上一个版本就是HEAD^ 两个是HEAD^^ 上n个版本就是HEAD~n  
也可以使用commit id  
4.`$ git reflog`  
查询每次commit的commit id,可用于回溯  
5.
