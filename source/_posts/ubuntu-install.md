---
title: ubuntu install
date: 2016-09-12 17:03:08
tags: ubuntu
---
/home/nailfar/projects/UbuntuInstall/README.md
#Ubuntu 安装教程
##pre 预备
* windows环境下 格式化一个空盘  100G左右 不低于10G  视个人情况而定 
	计算机->管理->磁盘管理->选择一个盘——添加压缩卷->分配大小——不格式化
	挂载linux以后windows下看不见此盘符
	linux下可以访问其他硬盘

* [下载ubuntu镜像文件 ios](http://www.ubuntu.com/desktop/get-ubuntu/download)

* 下载ultralISO 刻录U盘映像 --启动盘

<!--more-->


##1 物理安装
* 1 开机F12 + FN 设置启动项 u盘启动  自动进入安装模式 ，选择语言地区 
  不要联网安装速度很慢

* 2 选择安装Ubuntu 与windows共存
   磁盘挂载  设置交换区  2G
   格式化主分区  剩余磁盘的空间（100-2）G

* 3 选择地区  键盘布局  英语（美国）随意

* 4 用户名  计算机名字 越短越好 影响后面敲代码  密码 简单点  影响操作  后期可以更改不要太纠结

* 5 自动安装完成

 

##2工具安装

* 1 nginx 
	一键安装	
	``
	sudo apt-get install nginx
	``
	查找
	``
	find / -name  nginx 
	``
	配置 
	
    ``/etc/nginx/nginx.conf``

* 2 vscode
	[官网下载](https://code.visualstudio.com/c?utm_expid=101350005-27.GqBWbOBuSRqlazQC_nNSRg.2&utm_referrer=http%3A%2F%2Fcn.bing.com%2Fsearch%3Fq%3Dvscode%26go%3D%25E6%258F%2590%25E4%25BA%25A4%26qs%3Dn%26form%3DQBLH%26pq%3D%25E5%258F%258C%25E5%25B1%2582%25E6%25BB%259A%25E5%258A%25A8%26sc%3D0-4%26sp%3D-1%26sk%3D%26cvid%3DA6C99B72D9834CFE8BDDFE5DAFE850C0) 
	sublime 
	自己找
	vim
	``
	sudo apt-get install vim
	`` 
* 3 	
	* nodejs npm 
	
	``
	sudo add-apt-repository ppa:chris-lea/node.js

	sudo apt-get update

	sudo apt-get install nodejs
	``
	* webstorm
	[下载](http://www.jetbrains.com/webstorm/)	
	
	``
	解压到文件夹
	bin/webstorm.sh 启动 
	``
	* angular-cli 
	
	``
	npm install angular-cli -g
	``
	添加环境变量
	``
	~/.bashrc 中添加	
	export PATH="/usr/local/myapp/nodejs/bin:$PATH"
	export PATH="/usr/local/myapp/nodejs/lib/node_modules/angular-cli/bin:$PATH"	
	``
	* typedscript 
	* angular 
	用angular-cli 自动初始化typedscript angular环境
* 4 fildler mono 
	安装mono

	``sudo apt-get install  mono-complete``
	
    [下载mono版本findler](http://fiddler.wikidot.com/mono) 

	运行Findler.exe
	.sh脚本

    ```
	#!/bin/sh
	mono /home/nailfar/devTools/app/Fiddler.exe
	```

	启动脚本


* 5 virtualbox 虚拟机 ： win7  qq  微信  钉钉  ps  ...
	方法一	
	``
	sudo apt-get install virtualbox-5.0
	``
	[方法不行参见教程](http://jingyan.baidu.com/article/870c6fc3092aedb03fe4be28.html)
	方法二
	ubuntu软件中心直接安装
* 6 安装代理shadowsocks 
	
    ```
	1. sudo apt-get update

	2. sudo python --version

	3. apt-get install python-gevent python-pip

	4. pip install shadowsocks

	5. 找到shadowsocks文件夹的命令： sudo find / -name shadows*

	"/"是根目录下， *是通配符

	6. 修改config.js  放在对应文件bin目录下 例： /home/nailfar/.local/bin/sslocal

	{
	    "server" : "162.211.225.220",
	    "server_port" : 8520,
	    "local_port":1080,
	    "password" : "Plywood!",
	    "method":"rc4-md5",
	    "timeout":600
	}

	```

	开机自启动

	``
	??
	`` 
	挂载后台线程脚本
	
    ```bash
	#!/bin/sh
	sudo nohup /home/nailfar/.local/bin/sslocal -c /home/nailfar/.local/bin/config.json -d start
	```
	chrome 代理切换插件
	
    ```bash
	??百度switchsharp
	```
	系统自身代理设置
	
    ```bash
	桌面右上角->系统设置->网络->网络代理
	```
* 7谷歌浏览器安装
	-自带浏览器颜色字体不协调
	[官网下载deb](https://www.google.com/chrome/browser/desktop/index.html)
	安装见下
		
* 其他工具安装
	ios
	安卓
	php
	java
	数据库mysql
	``自求多福``
	


##3设置

* host ：/etc/hosts 

* 环境变量：临时设置重启后无效： export PATH=路径:$PATH 
	永久设置：修改文件 ~/.profile   ~/.bashrc  末尾追加 export PATH=路径:$PATH 



##4其他

*deb 程序包安装

```bash
dpkg -i xxx.deb
```
查看安装的deb

```bash
dpkg -l |grep xx*
```
卸载

```bash
dpkg -p xxxx
```

启动

dash  搜索启动

查找安装目录手动启动

```bash
find / -name xxx
```
查看进程

```bash
ps -aux |grep java
```





