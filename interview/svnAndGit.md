#### SVN的分支
#### trunk
----------这是SVN目录的主分支，表示日常开发中的项目，任何时候trunk里包含的都是最新的开发代码。这里的代码将会工作到你的下一个主要发布版本。  
#### branches /v1.0bugfix   
----------Experimental branches  
           有时你想将某个新技术引进项目。这很好，但是你当然不想赌上你的整个项目。  
----------Bug fix branches  
           分支也可以用于处理trunk或release branches里发现的严重的Bug。  
#### tags  /v1.0   /v2.0   
---------- 一般情况下，tag，是用来做一个milestone的，不管是不是release，都是一个可用的版本。tags，一般是只读的。  

### git和svn的区别
 1.git分布式,svn的集中式  
 svn就只有一个远程的仓库  
 1.如果没有了仓库的连接,就无法提交代码(失去了版本管理最基本的作用,提交,回滚,备份)  
 2.服务器没了,代码就没有了  
 git有本地仓库和远程仓库  
 git有本地仓库:随时就可以进行提交,随时都可以进行提交,回滚,备份功能  
 git远程仓库:共享自己的代码给别人  

 git分支管理灵活,比较强大,分支切换速度非常快-->分支是git的核心  
 git还可以很方便使用命令行操作  


###GitFlow 
 分支情况  
 dev:开发分支,类似svn里面trunk  
 master:标记分支,类似svn里面的tags  
 hotfixes:修复分支,类似svn里面的branches  
 release:发布版本的分支,发布版本的时候使用的分支  
 feature1:一个独立的功能  
 feature2:一个独立的功能  
 feature3:一个独立的功能  
 feature...:一个独立的功能   

 * 多人  
 user09(用户)-->登录功能(功能)-->user09(和用户同名的分支)  
 user10(用户)-->注册功能(功能)-->user10(和用户同名的分支)  
 结论:每个人都有自己的分支,这样的好处是什么?  
 1.不怕影响别人  
 2.代码安全性比较高  
 3.个人提交的频率也可以频繁些  
###管理员和开发者在gitFlow下应该持有哪些分支
 管理员  
 master  
 hotfixes  
 release  
 dev  
 开发者:  
 dev:  
 feature1:  

 1.只要参与开发,就有dev  
 2.每个参与开发的开发者有自己的功能分支(featureX)  

###管理员基于gitFlow需要做额外处理
 1.创建仓库  
 2.创建用户  
 3.分配权限  
 4.创建基本的android工程  
 5.本地代码和git服务器关联  
 6.git clone ssh://admin@billypc:29418/oschina31.git-->得到.git文件夹(隐藏文件)-->copy到项目根目录即可   
 7.修改.gitignore添加忽略  

 8.创建其他分支  
 hotfixes  
 release  
 dev-->push代码到远程仓库  
 admin-->因为管理员需要参与开发  
 9.进行初次提交 使用的工具是git gui(比as内置的插件好用)-->dev  
### 组员基于gitFlow需要做额外处理  
 1.检出项目-->基于远程的dev分支git clone -->本地就有一个dev  
 git clone --branch dev ssh://user09@billypc:29418/oschina31.git  
 2.创建自己的功能分支  

###基于GitFlow日常开发常见的操作-->admin/user09都是开发者
 日常操作-->没有冲突的情况  
 commit push -->在自己功能分支即可-->相当简单  
 合并功能代码到dev分支-->有难度  
 1.进行日常操作-->commit,push  
 2.切换到dev分支(本地分支)  
 1.保证当前的本地的dev和服务器上最新的dev保持一致-->  
 1.git fetch -->看远处分支代码是否有改变  
 远程的dev没有任何改变-->本地的代码就是最新的  
 远程的dev有改变-->合并远程的dev到本地的dev  
 3.合并对应功能代码-->本地的dev是最新的  
 4.push dev到远程-->告诉别人对应的改变  
 5.还想基于admin开发  
 1.切回admin  
 2.保证admin是最新的  
 1.合并本地的dev即可  
 3.继续开发  
