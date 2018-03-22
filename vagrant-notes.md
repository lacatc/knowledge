## Vagrant使用笔记

先安装好VirtualBox或VMvare，才能使用Vagrant。

以下是常用命令

- vagrant box add {title} {url} 其中，title是box文件在Vagrant中的名字，必须唯一。url是box的物理地址，可以是一个网址，也可以是本地的一个文件路径。当url是网址时，vagrant会调用内置的下载模块从服务器下载镜像到本地，Vagrant官网中提供的box都只能通过指定网址在线安装。

- vagrant box list  查看所有已添加的box

- vagrant init [option] [name url] 初始化配置

- vagrant up 在项目根目录运行，搭建虚拟机环境，启动虚拟机

- vagrant ssh 登陆虚拟机

- vagrant reload 重启虚拟机

- vagrant halt 关闭虚拟机

- vagrant status 查看虚拟机状态

- vagrant destory 将box从虚拟机卸载并删除

