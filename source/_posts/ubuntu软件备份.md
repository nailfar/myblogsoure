---
title: ubuntu软件备份
date: 2016-09-14 13:00:52
tags: ubuntu 
---

## 方式一：

在一台电脑上安装好所有的软件后，如何在别的机器上也批量安装上同样的软件，而无需一个一个重新安装呢？方法如下：
在已经安装和配置好的电脑上，不要删除`/var/cache/apt/archives`目录，执行下面的命令，生成当前安装软件的内容列表

``dpkg --get-selections | grep -v deinstall > ubuntu.files``

然后把ubuntu.files和archives目录中的所有内容都cp到别的机器对应的目录。
<!--more-->
重装后，配好sources.list

``sudo apt-get update``

``sudo apt-get dist-upgrade``

``dpkg --set-selections < ubuntu.files``

``sudo dselect``

按下 i

然后一路回车下去。



## 方式二：

　　在重装前要备份安装软件的列表，软件源，用户文件

　　1.备份已安装软件包列表

　　``dpkg --get-selections > /home/user/package.selections``

　　2.备份Home下的用户文件夹

　　如果你已经将Home放在额外的分区，这一步就不必了，复制所有用户文件夹下的所有内容到另外的分区，注意要包含隐藏文件(Ctrl+Hide)

　　3.备份软件源列表，将/etc/apt/文件夹下的sources.list拷贝出来保存即可

　　新系统安装后的恢复：

　　1.复制备份的Sources.list文件到新系统的/etc/apt/目录，覆盖原文件，并替换(Ctrl+H)文档中的intrepid为jaunty。然后更新软件源(sudo apt-get update)。

　　2.重新下载安装之前系统中的软件(如果你安装的软件数量比较多，可能会花费较长时间)

　　``sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade``

　　3.最后将备份的主文件夹(/home/用户名)粘贴并覆盖现有主文件夹

　　用这个方法我们可以基本在不丢失现有系统和软件设置的情况下使用全新的Ubuntu系统了!
