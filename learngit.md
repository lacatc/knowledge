### 分布式版本控制系统
首先，分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。

使用版本管理控制系统，以纯文本编写文件，统一使用 UTF-8编码

### 完成git安装，设置自己名字和 Email
```
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
### 创建版本库 repository 

首先选择一个合适位置，创建空目录

	pwd  
	cd '合适位置'
	mkdir '目录名字'
	cd '新目录'       
	git init
 
### 将文件添加到 git 仓库   
	git add filename 
	git commit -m "输入提交的信息"
	git status #查看仓库的状态，常常观察到是发生修改，但是没有提交
	git diff #忘记之前是如何修改确认无误之后，再按照之前的步骤提交即可
	git add filename
	git commit -m "修改了哪些"

 
### 查看提交历史   
	git log 
	git log --pretty=oneline #显示主要的信息
	
### 版本穿梭	
	git reset --hard HEAD^ #HEAD,表示当前版本，HEAD~x 表示可以回去前x版本
	git reset --hard "版本号" #版本号想回到的版本
	git reflog  #记录了历史命令

### 暂存区
* 第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区stage；

* 第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支master。

### 撤销修改
 
	git reset HEAD filename#撤销暂存区修改，退到工作区
	git checkout -- filename #丢弃工作区的修改

 
### 工作区中删除文件
	git rm filename #删除版本库中文件
	git checkout -- filename #从版本库中替换之前的版本


### 本地库的所有内容推送到远程库 
将GitHub与本地连接(配置.ssh)，创建新的repository，在命令行中，cd 本地repository

	git remote add origin https://github.com/username/reponame.git #关联远程库
	git push -u origin master #第一次推送master分支的所有内容

把本地的master分支和远程的master分支关联起来
   
   	git push origin master # 之后只要本地commit，就可以将本地master最新修改推送到github

### 从远程库克隆到本地

	git clone "respository_address"