# Git 基础

1. 创建版本库learngit

`$ mkdir learngit`
`$ cd learngit`
`$ git init　`

2. 添加和提交readme.txt
   `$ git add readme.txt`
   `$ git commit -m "wrote a readme file"`

这里需要了解git的工作区和暂存区的概念，当执行命令add的时候，其实是将数据提交到了暂存区，而commit命令则将暂存区的数据提交到当前的分支上。所以，我们可以多次add数据到暂存区，然后一次性进行commit。
另外，创建库learngit的时候，系统会默认创建分支master，并由指针HEAD指向master

3. 撤销修改
   `$ git checkout -- file`  　*这个命令是摊销工作区中的修改*
   `$ git reset HEAD file` 　*可以把暂存区的修改撤销掉，重新放回工作区，HEAD表示最新版本*
4. 远程仓库
首先，注册bitBucket账号，然后在git shell中先生成一个SHH key，这个Key是本地和远程仓库时行通讯的凭证。
   `$ ssh-keygen -t rsa -C "youremail@example.com"`
将目录下的公有key，粘贴到bitBucket上的SHH通讯账号上，这样就和bitBuket上的账号进行了授权。
这种做法很不方便，通过HTTP授权的方式即在clone的时候直接输入账号密码就行了。
5. 添加远程库
   `$ git remote add origin git@bitbucket.com:tulingjiang/learngit.git`
这个命令是将本地库与bitbucket上的库进行连接，origin是Git默认远程库的叫法。
下一步，就可以将本地库所有的内容推到远程库上。
   `$ git push -u origin master`
把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
由于远程库是空的，第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。以后再进行推送时，只要如下这个命令就好：
   `$ git push origin master`
6. 从远程库克隆
   `$ git clone git@bitbucket.com:tulingjiang/gitskills.git`
7. 创建与合并分支
   `$ git checkout -b dev`
   `git checkout`
命令加上-b参数表示创建并切换，相当于以下两条命令：
   `$ git branch dev`
   `$ git checkout dev`
必须要了解分支的本质，在Git中，当前的分支是由HEAD的指向决定的，也就是说，刚刚开始的时候，HEAD指向master，如果创建并且`checkout`进了一个分支，实际上执行的是创建了一个指针指向了master相同的提交，然后再将HEAD指向了新创建的那个分支。**工作区的数据是没有任务变化的！**而后，对工作区的修改和提交只针对当前分支了，比如新提交一次，新分支就向前移了一步，而master指针不变。
   `$ git merge dev`　*合并dev分支到master分支中去*
注意到，这种模式的合并叫作`Fast-forward`，即快进模式，也就是直接把`master`指向`dev`的当前提交，速度很快，但并不是任何时间都可以这样合并的。
8. 解决冲突
当两个分支都同时进行了修改时，提交就可能出现冲突，这个时候，Git会提示冲突，冲突的地方修改后才可进行提交。
9. 分支管理策略
通常，合并分支时，如果可能，Git会用`Fast forward`模式，但这种模式下，删除分支后，会丢掉分支信息。如果要强制禁用`Fast forward`模式，Git就会在`merge`时生成一个新的`commit`，这样，从分支历史上就可以看出分支信息。
   `$ git merge --no-ff -m "merge with no-ff" dev`
   前面说过，`Fast forward`模式其实就是直接将master指针指向了分支的提交，而用`--no-ff`之后，就新创建了一个`commit`，合并后的历史有分支，能看出来曾经做过合并，而`Fast forward`合并就看不出来曾经做过合并。
10. 关于fork和pull request机制
在bitBucket上进行项目操作的基本流程应该如下：
  - 首先是fork一个他人的仓库，这是bitBucket操作，它会复制他人的仓库到你的bitBucket账号下面。
  - 接着进行clone操作，这是Git操作，使用该操作让你发送"请给我发一份我仓库的复制文件"的命令给bitBucket。现在这个仓库就会存储在你本地计算机上。
  - 而后进行文件等的更新操作后，进行PUSH操作，这操作会将你在本地所做的更新提交至bitBucket上自己账号相应的库上。
  - 最后，如果你认为之前fork的库的作者会接受你的修改，你就可以给他发送一个pull request。这是bitBucket操作，询问对方是否愿意接受你的"pull request"，当然，接不接受完全取决于他自己。

##一些使用笔记
####删除远程分支
如果想在服务器上删除 serverfix 分支，运行下面的命令：

$ git push origin :serverfix

有种方便记忆这条命令的方法：记住git push [远程名] [本地分支]:[远程分支] 语法，如果省略 [本地分支]，那就等于是在说“在这里提取空白然后把它变成[远程分支]”。

####修改最后一次提交
如果提交完了才发现漏掉了几个文件没加，或者提交信息写错了，想要撤消刚才的提交操作，可以使用--amend选项重新提交：

    $ git commit --amend

这个命令将使用当前的暂存区域快照提交，如果刚才提交完没有任何改动，相当于重新编辑提交说明，但将要提交的文件快照和之前的一样。

如果是刚才提交忘了暂存某些修改，可以先补上暂存操作，然后再运行--amend提交：

    $ git commit -m 'initial commit'
    $ git add forgotten_file
    $ git commit --amend

上面的三条命令最终只产生一个提交，第二个提交命令修正了第一个提交内容。

###rebase和merge
merge 命令，它会把两个分支最新的快照以及二者最新的共同祖先进行三方合并，合并的结果是产生一个新的提交对象。
而 rebase 则是把当前分支产生的变化补丁在你要 base 去的分支上重新打一遍，这样，就可以把在一个分支里提交的改变移到另一个分支里重放一遍。
比如:
<pre>$ git checkout experiment
$ git rebase master</pre>

其中，experiment分支就是需要 rebase 的分支，往 master 里 base .
它的原理是回到两个分支最近的共同祖先，根据当前分支（也就是要进行 rebase 的分支 experiment）后续的历次提交对象生成一系列文件补丁，然后以基底分支（也就是主干分支 master）最后一个提交对象为新的出发点，逐个应用之前准备好的补丁文件，最后会生成一个新的合并提交对象，从而改写 experiment 的提交历史，使它成为 master 分支的直接下游。