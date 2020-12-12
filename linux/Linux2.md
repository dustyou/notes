---
groupgrouptypora-root-url: image
typora-root-url: image
---

# Linux



# 第 8 章 实操篇 用户管理

### 8.1 基本介绍

给大家画了一个示意图，帮助大家理解用户管理的规则

![](/Snipaste_2020-10-07_14-09-33.png)

说明

1、Linux系统是一个多用户多任务的操作系统，任何一个要使用系统资源权限的用户，都必须手续哎你想系统管理员申请一个账号，然后以这个账号进入系统

2、Linux的用户需要至少要属于一个组



### 8.2 添加用户

####  8.2.1 基本语法

useradd 【选项】 用户名

#### 8.2.2 实际案例

添加一个用户 xm

![](/Snipaste_2020-10-07_14-20-48.png)

特别说明：

cd  表示 change directory 切换目录

#### 8.2.3 细节说明

1、当创建用户成功，会自动创建和用户同名的目录

2、也可以通过 useradd -d 指定目录 新的用户名 给新创建的用户指定家目录

![](/Snipaste_2020-10-07_14-23-10.png)

### 8.3 给用户指定或者修改密码

![](/Snipaste_2020-10-07_14-24-45.png)

![](/Snipaste_2020-10-07_14-25-02.png)

### 8.4 删除用户

#### 	8.4.1 基本语法

​	userdel 用户名

#### 	8.4.2 应用案例

​		1、删除用户xm 但是要保留家目录

![](/Snipaste_2020-10-07_14-29-03.png)

​		2、 删除用户 xh 以及用户主目录

![](/Snipaste_2020-10-07_14-29-09.png)

#### 	8.4.3 思考题

​		在删除用户时，我们一般都不会将家目录删除

### 8.5 查询用户

#### 	8.5.1 基本语法

​		id 用户名

#### 	8.5.2 应用实例

​		案例1 请查询 root 信息

![](/Snipaste_2020-10-07_14-33-34.png)

#### 	8.5.3 细节声明

​		1、当用户不存在的时候，返回无此用户

### 8.6 切换用户

#### 	8.6.1 介绍

​		在操作 Linux中，如果当前用户的权限不够，可以通过 su - 指令 切换到高权限用户，比如 root

#### 	8.6.2 基本语法

​		su - 切换用户名

#### 	8.6.3 应用实例

​		1、创建一个用户 zf 执行密码 然后切换到 zf

![](/Snipaste_2020-10-07_14-37-55.png)

#### 	8.6.4 细节说明

1、从权限高的用户切换到权限低的用户，不需要输入密码，反之需要

2、当需要返回到原来用户时，使用exit指令

### 8.7 用户组

#### 	8.7.1 介绍

​		类似于角色，系统可以对有共性的多个用户进行统一的管理	

#### 	8.7.2 增加组

​		groupadd 组名

#### 8.7.3 案例演示

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-47-42.png)

#### 8.7.4 删除组

指令(基本语法)

groupdel 组名

#### 8.7.5 案例演示

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-48-30.png)



### 8.8 增加用户时直接加上组

#### 8.8.1 指令(基本语法)

​	useradd -g 用户组 用户名

#### 8.8.2 案例演示

增加一个用户 zwj 直接将指定的 wudang

​	![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-50-47.png)

### 8.9 修改用户的组

#### 8.9.1 指令(基本语法)

usermod -g 用户组 用户名

#### 8.9.2 案例演示

创建一个shaolin组，让zwj 用户到shaolin

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-51-54.png)



### 8.10 /etc/passwd文件

用户(user)的配置文件，记录用户的各种信息

每行的含义，用户名:口令用户标识号。注释性描述，主目录 登录Shell

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-54-22.png)

### 8.11 /etc/shadow 文件

口令的配置文件

每行的含义:登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动
时间:失效时间:标志

### 8.12 /etc/group 文件

组(group)的配置文件，记录 Linux包含组的信息

每行含义:组名:口令:组标识号:组内用户列表

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_14-56-45.png)



# 第 9 章 实操篇 实用指令

### 9.1 指定运行级别

运行级别说明:

0:关机

1:单用户[找回丢失密码]

2:多用户状态没有网络服务

3:多用户状态有网络服务

4:系统未使用保留给用户

5:图形界面

6:系统重启

常用运行级别是3和5，要修改默认的运行级别可改文件

/etc/inittab 的 id:5:initdefault这一行中的数字

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_15-27-52.png)

#### 9.2 切换到指定运行级别的指令

#### 9.2.1 基本语法

init [012356]

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_15-28-40.png)

#### 9.2.3 面试题

如何找回root密码 如果我们不小心 忘记root密码 怎么找回

思路 进入到单用户模式，然后修改 root密码 因为进入单用户模式 root 不需要密码就可以登录

参考教程链接

https://blog.csdn.net/dannistang/article/details/80224871



9.3 帮助指令

9.3.1 介绍

​	当我们对某个指令不熟悉时，我们可以使用 Linux 提供的指令来了解这个指令的使用方法

9.3.2 man 获得帮助信息

1、基本语法

man [命令或配置文件](功能描述，获取帮助信息)

2、应用实例

​	案例，查看ls命令的帮助信息

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_15-34-05.png)

#### 9.3.3 help指令

1、基本语法

​	help 命令(功能描述 获取shell内置命令的帮助信息)

2、应用实例

​	案例: 查看 cd 命令的帮助信息

![](D:\java\脑图\Linux\image\Snipaste_2020-10-07_15-36-37.png)

### 9.3.4 当一个指令不熟悉如何学习的建议

百度更直接



### 9.4 文件目录类

#### 	9.4.1 pwd 指令

​	基本语法 

​		pwd 功能描述 显示当前工作目录的绝对路径

​	应用案例

![](/Snipaste_2020-10-07_16-04-46.png)

#### 	9.4.2 ls 指令

​		基本语法

​			ls [选项] [目录或者是文件]

​		常用选项

​			-a 显示当前目录所有的文件和目录，包括隐藏

​			-l 以列表形式显示

​		应用实例

​		查看当前目录的所有内容信息

![](/Snipaste_2020-10-07_16-09-12.png)

![](/Snipaste_2020-10-07_16-09-22.png)

#### 9.4.3 cd 指令

基本语法

​	cd [参数] 功能描述 切换到指定目录

常用参数

​	绝对路径和相对路径

​	如何理解绝对路径和相对路径

![](/Snipaste_2020-10-07_16-11-13.png)

应用实例

​	案例1、使用绝对路径切换到 root 目录

​	cd /root

​	案例2 使用相对路径到 root目录

​	这里我们需要知道 该用户目录在那个目录下。才能写出这个指令，假设在 /usr/lib

​	cd ../../root

​	案例3、表示回到当前目录的上一级目录

​	cd ..

​	案例4、回到家目录

​	cd 

​	cd ~

#### 9.4 mkdir 指令

​	mkdir 指令用于创建目录

​	基本语法

​		mkdir [选项] 要创建的目录

​	常用选项

​		-p 创建多级目录

应用实例

案例1、创建一个目录 /home/dog

![](/Snipaste_2020-10-07_16-15-06.png)

​	案例2、创建多级目录 /home/animal/tiger

![](/Snipaste_2020-10-07_16-15-19.png)

#### 9.4.5 rmdir 指令

​	介绍

​		mkdir 指令删除空目录

​	基本语法

​	 mkdir [选项] 要删除的空目录

​	应用实例

1、删除一个目录 /home/dog

![](/Snipaste_2020-10-07_16-17-45.png)

2、使用细节

rmdir 删除的是空目录 如果目录下有内容时无法删除

提示 如果需要删除非空目录，需要使用 rm -rf 要删除的目录

![](/Snipaste_2020-10-07_16-18-42.png)

#### 9.4.6 touch 指令

touch 指令创建空文件

基本语法

​	touch 文件名称

应用实例

1、创建一个空文件 hello.txt

![](/Snipaste_2020-10-07_16-19-59.png)

#### 9.4.7 cp指令

cp 指令拷贝文件到指定目录

基本语法

​	cp[选项] source dest

常用选项

​	-r递归复制整个文件夹

应用实例

1、将 /home/aaa.txt 拷贝到 /home/bbb 目录下[拷贝单个文件]

![](/Snipaste_2020-10-07_16-21-30.png)

2、递归复制整个文件夹

将/home/test 整个目录拷贝到 /home/zwj 目录

![](/Snipaste_2020-10-07_16-22-10.png)

使用细节

​	强制覆盖不提示的方法  \cp

![](/Snipaste_2020-10-07_16-22-49.png)

#### 9.4.8 rm 指令

rm 指令移除 [删除] 文件或目录

基本语法

​	rm [选项] 要删除的文件或目录

常用选项

​	-r 递归删除整个文件夹

​	-f 强制删除不提示

应用案例

1、将/home/aaa.txt删除

![](/Snipaste_2020-10-07_16-24-33.png)

2、递归删除整个文件夹 /home/bbb

![](/Snipaste_2020-10-07_16-24-57.png)

使用细节

​	强制删除不提示的方法 带上-f参数即可

![](/Snipaste_2020-10-07_16-25-36.png)

#### 9.4.9 mv 指令

mv 移动文件或目录或重命名

基本语法

​	mv oldNameFile newNameFile 重命名

​	mv /temp/movefile /targetFolder 移动文件

应用实例

1、将/home/aa.txt 重新命名为pig.txt

![](/Snipaste_2020-10-07_16-27-05.png)

2、将/home/pig.txt 文件移动到rooot目录下

![](/Snipaste_2020-10-07_16-27-38.png)

#### 9.4.10 cat 指令

cat 查看文件内容 只读形式打开

基本语法

 	cat [选项] 要查看的文件

常用选项

​	-n 显示行号

应用实例

1、/etc/profile 文件内容 并显示行号

![](/Snipaste_2020-10-07_16-28-58.png)

使用细节

cat 只能浏览文件 不能修改文件，为了浏览方便 一般会带上 管道命令

cat 文件名 | more 分页浏览

#### 9.4.11 more指令

more 指令时一个基于V1编辑器的文本过滤器，它以全屏幕的方式按页显示文本的内容，more指令中内置了若干快捷键

基本语法

​	more 要查看的文件

应用实例

1、采用more查看文件

![](/Snipaste_2020-10-07_16-32-32.png)

快捷键

![](/Snipaste_2020-10-07_16-32-42.png)

#### 9.4.12 less 指令

less指令用来分屏查看文件内容，它的功能与more指令类似，但是比more指令更加强大，支持
各种显示终端。less指令在显示文件内容时，并不是一-次将整个文件加载之后才显示，而是根据显示
需要加载内容，对于显示大型文件具有较高的效率。

基本语法

​	less 要查看的文件

应用案例

1、采用less查看一个大文件

![](/Snipaste_2020-10-07_16-33-48.png)

快捷键

![](/Snipaste_2020-10-07_16-33-59.png)

9.4.13 >指令 和 >> 指令

介绍

【>】 输出重定向 会将原来文件内容覆盖

【>>】追加 不会覆盖原来的文件内容，而是追加到文件的尾部

基本语法

1、ls -l > 文件  功能描述 列表的内容写入文件 a.txt中 覆盖写

![](/Snipaste_2020-10-07_16-36-14.png)

2、ls -al >> 文件 功能描述 列表的内容追加到文件 aa.txt的末尾

![](/Snipaste_2020-10-07_16-37-15.png)

3、cat 文件 1 > 文件2 功能描述 将文件1的内容覆盖到文件2

![](/Snipaste_2020-10-07_16-38-03.png)

4、echo "内容" >> 文件

应用案例

1、将/home 目录下的文件列表 写入到 /home/info.txt中

![](/Snipaste_2020-10-07_16-38-55.png)

2、将当前日历信息追加到 /home/mycal文件夹中

![](/Snipaste_2020-10-07_16-39-36.png)

#### 9.4.14 echo指令

echo 输出内容到控制台

基本语法

​	echo [选项] [输出内容]

应用实例

1、使用echo指令输出环境变量，输出当前环境路径

![](/Snipaste_2020-10-07_16-43-00.png)

2、使用echo输出 helloworld

#### 9.4.15 head 指令

head 用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容

基本语法

​	head 文件 功能描述 查看文件头10行内容

​	head -n 5 文件 查看文件头5行内容 5可以是任意数

应用实例

1、查看/etc/profile 的前面5行代码

![](/Snipaste_2020-10-07_16-45-47.png)

9.4.15 tail指令

tail用于输出文件中尾部的内容 默认情况下 tail指令显示文件后的10行内容

基本语法

​	1、tail 文件 (功能描述 查看文件后10行内容)

​	2、tail -n 5 查看文件后5行

​	3、tail -f 文件 实时追踪该文档所有更新，工作中经常使用

应用案例

1、查看/etc/profile 最后5行代码

![](/Snipaste_2020-10-07_16-49-00.png)

2、实时监控 mydate.txt 看看文件有没有变化 是否看到 追加的日期

![](/Snipaste_2020-10-07_16-49-35.png)

#### 9.4.17 ln指令

软链接也叫符号链接，类似于windows里的快捷方式，主要存放了链接其他文件的路径
●基本语法
		In-s [原文件或目录] [软链接名] (功能描述: 给原文件创建一个软链接)
●应用实例
		案例1:在/home目录下创建一一个软连接linkToRoot, 连接到/root 目录

![](/Snipaste_2020-10-07_16-53-34.png)

![](/Snipaste_2020-10-07_16-53-49.png)

细节说明

当我们使用pwd指令查看目录时，任然看到的是软连接所在的目录

#### 9.4.18 history 指令

查看已经执行过的历史命令 也可以执行历史命令

基本语法

history

应用案例

1、显示所有历史命令

![](/Snipaste_2020-10-07_17-03-20.png)

2、显示最近使用过的10个指令

![](/Snipaste_2020-10-07_17-03-41.png)

3、执行临时编号为5 的指令

![](/Snipaste_2020-10-07_17-04-18.png)

### 9.5 时间日期类

9.5.1 date指令-显示当前日期

基本语法

![](/Snipaste_2020-10-07_17-04-53.png)

案例

1、显示当前时间信息

![](/Snipaste_2020-10-07_17-05-23.png)

9.5.3 cal 指令

查看日历指令

基本语法

cal [选项]  不加选项 显示本月日历

案例

1、显示当前

![](/Snipaste_2020-10-07_17-06-36.png)

9.6 搜索查找类

9.6.1 find 指令

find指令从指定目录向下递归地遍历各个子目录，将满足条件的文件或目录显示在中断

基本语法

​	find [搜索范围] [选项]

选项说明

![](/Snipaste_2020-10-07_17-07-58.png)

案例

1、按文件名 根据名称查找/home 目录下的hello.txt文件

![](/Snipaste_2020-10-07_17-09-04.png)

2、按拥有者 查找/opt目录下 用户名称为 nobody的文件

![](/Snipaste_2020-10-07_17-09-59.png)

3、查找整个linux文件大于20m的文件(+n 大于 -n小于)

![](/Snipaste_2020-10-07_17-10-35.png)

4、查询 / 目录下 所有的 .txt文件

![](/Snipaste_2020-10-07_17-11-47.png)

#### 9.6.2 locate指令

locaate指令可以快速定位文件路径。locate指令利用事先建立的系统中所有文件名称及路径的locate数据库实现快速定位给定的文件。Locate指令无需遍历整个文件系统，查询速度较快。为了保证查询结果的准确度，管理员必须定期更新locate时刻。
●基本语法
	locate搜索文件
●特别说明，
	由于locate指令基于数据库进行查询，所以第一次运行前，必须使用updatedb指令创建locate数据库。
●应用实例
案例1:请使用locate指令快速定位hello.txt 文件所在目录

![](/Snipaste_2020-10-07_17-12-59.png)

#### 9.6.3 grep 指令和 管道符号 |

grpe 过滤查找，管道符 | 表示将前一个命令的处理结果输出传递给后面的命令处理

基本语法

​	grep [选项] 查找内容 源文件

常用选项

![](/Snipaste_2020-10-07_17-14-26.png)

应用案例

1、在hello.txt中 查找yes所在行 并且显示行号

![](/Snipaste_2020-10-07_17-17-04.png)

### 9.7 压缩和解压类

#### 9.7.1 gzip/gunzipz指令

gzip用于压缩文件 gunzip用于解压

基本语法

gzip 文件 压缩文件 只能将文件压缩成*.gz文件

gunzip文件.gz 解压缩文件命令

应用案例

1、gzip压缩文件  将hello.txt压缩

![](/Snipaste_2020-10-07_17-18-52.png)

2、gunzip 解压缩

![](/Snipaste_2020-10-07_17-19-34.png)

细节说明 当我们让你使用gzip对文件进行压缩后，不会保留原有的文件



9.7.2 zip/unzip 指令

zip 用于压缩文件 unzip用于解压缩的 在项目打包发布过程中很有用

基本语法

​	zip [选项]XXX.zip 将要压缩的呢容

​	unzip [选项]XXX.zip 功能描述 解压缩文件

zip常用选项

​	-r 递归压缩 即压缩目录

unzip常用选项

​	-d <目录> 指定解压文件存放的目录

应用实例

1、将/home下所有文件压缩成 mypackage.zip

![](/Snipaste_2020-10-07_17-31-46.png)

2、将mypackage.zip文件 解压到/opt/tmp目录下

​	![](/Snipaste_2020-10-07_17-32-49.png)

#### 9.7.3 tar 指令

tar 指令是打包指令 最后打包成的是 .tar.gz的文件

基本语法

tar  [选项] XXX.tar.gz 打包的内容 压缩后的文件格式 tar.gz

选项说明

![](/Snipaste_2020-10-07_17-34-48.png)

应用实例

1、压缩多个文件 将/home/al.txt 和/home/a2.txt 压缩成 a.tar.gz	

![](/Snipaste_2020-10-07_17-35-42.png)

2、将/home的文件夹 压缩成myhome.tar.gz

![](/Snipaste_2020-10-07_17-36-07.png)

3、将 a.tar.gz 解压到当前目录

![](/Snipaste_2020-10-07_17-36-27.png)

4、将myhome 加压到 /opt/目录下

![](/Snipaste_2020-10-07_17-36-56.png)



# 第 10 章 实操篇 组管理和权限管理

### 10.1 Linux 组基本介绍

在Linux中每个用户必须属于一个组，不能独立于组外，在Linux中每个文件有所有者，所在组，其他组的概念

1、所有者

2、所在组

3、其他组

4、改变用户所在的组

![](/Snipaste_2020-10-07_20-23-24.png)

#### 10.2 文件目录 所有者

一般为文件的创建者，谁创建了该文件，就自然成为了该文件的所有者

#### 10.2.1 查看文件的所有者

1、指令 ls -hal

2、应用实例 创建一个组 police 再创建一个用户 tom 将 tom放在police组 然后使用tomg来创建一个文件 ok.txt 看看情况如何

![](/Snipaste_2020-10-07_20-25-23.png)

#### 10.2.2 修改文件所有者

指令 chown 用户名 文件名

应用案例

1、使用 root 创建一个文件 apple.txt 然后将其所有者修改成 tom

![](/Snipaste_2020-10-07_20-26-14.png)

### 10.3 组的创建

#### 10.3.1 基本命令

groupadd 组名

#### 10.3.2 应用实例

创建一个组 monster

创建一个用户 fox 并放入monster组中



### 10.4 文件/目录 所在组

当某个用户创建了一个文件后，默认这个文件的所在组就是该用户所在的组

#### 10.4.1 查看文件/目录所在组

基本指令

ls -ahl

应用实例

10.4.2 修改文件所在的组

基本指令

chgrp 组名 文件名

应用实例

使用 root 用户创建文件 orange.txt 看看当前这个文件属于那个组，然后将这个文件所在组，修改成police组

![](/Snipaste_2020-10-07_20-44-30.png)

### 10.5 其他组

除文件的所有者和所在组的用户外，系统的其他用户都是文件的其他组

### 10.6 改变用户所在组

在添加用户时，可以指定将该用户添加到哪个组中，同样的用root的管理权限可以改变某个用户
所在的组。

#### 10.6.1 改变用户所在组

1、usermod -g 组名 用户名

2、usermod -d 目录名 用户名 改变该用户登录的初始目录

#### 10.6.2. 应用案例

创建一个土匪组(bandit) 将tom这个用户从原来所在的police组，修改到bandit(土匪)组

![](/Snipaste_2020-10-07_20-48-58.png)

### 10.7 权限的基本介绍

ls -1中显示的内容如下:
-rwxrw-r-- 1 root root 1213 Feb 2 09:39 abc
0-9位说明
1)第0位确定文件类型(d,-,1,c,b) .
2)第1-3位确定所有者(该文件的所有者)拥有该文件的权限。--User
3)第4-6位确定所属组(同用户组的)拥有该文件的权限，--Group
4)第7-9位确定其他用户拥有该文件的权限--Other

![](/Snipaste_2020-10-07_20-50-40.png)

### 10.8 rwx权限详解

#### 10.8.1 rwx作用到文件

1、[r] 代表可读(read) 可以读取 查看

2、[w] 代表可写(write) 可以修改 但是不代表可以删除，删除一个文件的前提条件是对该文件所在目录有写权限，才能删除文件

3、[x] 代表可执行(execute) 可以被执行

#### 10.8.2 rwx 作用到目录

ls -l 显示内容如下 记住

-rwxrw-r-- 1 root root 1213 Feb 2 09:39 abc

10个字符确定不同用户能对文件干什么
第一个字符代表文件类型:文件 (-),目 录(d),链接(1)
其余字符每3个-组(rwx)读(r) 写(w) 执行(x)
第一组rwx:文件拥有者的权限是读、写和执行
第二组rw-:与文件拥有者同一组的用户的权限是读、写但不能执行
第三组r-:不与文件拥有者同组的其他用户的权限是读不能写和执行
可用数字表示为:r=4,w=2,x=1因此rwx=4+2+1=7
1 						文件:硬连接数或目录: 子目录数
root 					用户
root					组
1213					文件大小(字节)，如果是文件夹，显示4096 字节
Feb 2 09:39		最后修改日期

### 10.10 修改权限-chmod

10.10.1 基本说明

​	通过chmod指令 可以修改文件或目录的权限

10.10.2 第一种方式 +、-、= 变更权限

u:所有者	g:所有组	 o:其他人	 a:所有人(u、 g、o的总和)
1) chmod u=rwx,g=x,o=x 文件目录名
2) chmod	o+w	文件目录名
3) chmod	a-x	文件目录名

案例演示

1、给abc文件 的所有者读写执行的权限，给所在组读执行权限 给其他组读执行权限

![](/Snipaste_2020-10-08_13-28-19.png)

2、给 abc文件的所有者除去执行的权限，增加组写的权限

![](/Snipaste_2020-10-08_13-28-50.png)

3、给abc文件的所有用户添加读的权限

![](/Snipaste_2020-10-08_13-29-39.png)

#### 10.10.3 第二种方式 通过数字变更权限

规则: r=4 w=2x=1l	,rwx=4+2+1=7 .
chmod u=rwx,g=rx,0=x	文件目录名
相当于chmod	751	文件目录名

案例演示

1、要求将 /home/abc.txt 文件权限修改成 rwxr-xr-t 使用数字的方式实现

rwx=4+2+1=7

r-x=4+1=5

r-x=4+1=5

指令 chmod 755 /home/abc.txt

### 10.11 修改文件所有者-chown

10.11.1 基本介绍

chown newowner file 改变文件的所有者

chown newownergroup file 改变用的的所有者和所有组

-R 如果是目录 则使其下所有子文件或目录递归生效

#### 10.11.2 案例演示

1、请将 /home/abc.txt 文件的所有者修改成 tom

![](/Snipaste_2020-10-08_13-33-24.png)

2、请将/home/kkk 目录下所有的文件和目录的所有者都修改成tom

首先我们应该使用root操作

![](/Snipaste_2020-10-08_13-34-06.png)

### 10.12 修改文件所在组 -chgrp

#### 10.12.1 基本介绍

chgrp newgroup file 改变文件的所有组

#### 10.12.2 案例演示

1、请将/home/abc.txt 文件的所有组修改成bandit(土匪)

chgrp bandit /home/abc.txt

2、请将 /home/kkk 目录下所有的文件和目录的所在组都修改成 bandit(土匪)

chgrp -R bandit /home/kkk

![](/Snipaste_2020-10-08_13-36-36.png)

### 10.13 最佳实践-警察和土匪游戏

police，bandit
jack, jerry:警察
xh, xq:土匪
1、创建组
bash> groupadd police
bash> groupadd bandit
2、创建用户

![](/Snipaste_2020-10-08_13-37-34.png)

3、jack 创建一个文件 自己可以读写 本组人 可以读 其他组没任何权限

![](/Snipaste_2020-10-08_13-38-22.png)

4、 jack 修改该文件 让其他组人可以读 本组人可以读写

![](/Snipaste_2020-10-08_13-38-50.png)

5、xh 投靠警察 看看是否可以读写

先用root 修改xh组

![](/Snipaste_2020-10-08_13-39-27.png)

使用jack给他的家目录 /home/jack 的所在组一个rx的权限

![](/Snipaste_2020-10-08_13-40-00.png)

xh需要重新注销在到jack 目录就可以操作，jack的文件

![](/Snipaste_2020-10-08_13-40-32.png)



# 第 11 章 实操篇 crond任务调度

### 11.1 原理示意图

![](/Snipaste_2020-10-08_16-14-53.png)

### 11.2 概述

任务调度 是指系统在某个时间执行的特定的命令或程序

任务调度分类

1、系统工作，有些重要的工作必须周而复始的执行，如病毒扫描等

2、个别用户工作，个别用户可能希望执行某些程序，比如mysql数据库备份

### 11.3 基本语法

crontab [选项]

#### 11.3.1常用选项

![](/Snipaste_2020-10-08_16-17-25.png)

### 11.4 快速入门

#### 11.4.1 任务的要求

设置任务调度文件: /etc/crontab
设置个人任务调度。执行crontab -e
接着输入任务到调度文件
如: */1 ****1s -1 /etc/> /tmp/to.txt
意思说每小时的每分钟执行ls - 1/etc/ > /tmp/to.txt命令

#### 11.4.2 步骤如下

1、cron -e

2、 */1 * * * * ls -l /etc >> /tmp/to.txt

3、当保存退出后就程序

4、在每一分钟都会自动的调用 ls -l /etc >> /tmp/to.txt

#### 11.4.3 参数细节说明

![](/Snipaste_2020-10-08_16-20-06.png)

### 11.5 任务调度的几个应用实例

11.5.1 案例1 每隔1分钟 就将当前的日期信息，追加到 /tmp/mydate 文件中

1、先编写一个文件 /home/mytask1.sh

​	date >> /tmp/mydate

2、给 mytask1.sh 一个可以执行的权限

​	chmod 744 /home/mytask1.sh

3、crontab -e

4、*/1 * * * * /home/mytask1.sh

5、成功

#### 11.5.2 案例2 每隔1分钟 将当前日期和日历追加到 /home/mycal 文件中

1、先编写一个文件 /home/mytask2.sh

​	cal >> /tmp/mydate

2、给 mytask1.sh 一个可以执行的权限

​	chmod 744 /home/mytask2.sh

3、crontab -e

4、*/1 * * * * /home/mytask2.sh

5、成功

#### 11.5.3 案例3 每天凌晨2:00 将mysql数据库 testdb 备份到文件中 mydb.bak

1、先编写一个文件 /home/mytask3.sh

​	/usr/local/mysql/bin/mysqldump -uroot -p root testdb > /tmp/mydb.bak

2、给 mytask1.sh 一个可以执行的权限

​	chmod 744 /home/mytask3.sh

3、crontab -e

4、0 2 * * * /home/mytask3.sh

5、成功

### 11.6 crond 相关指令

1、conrtab -r 终止任务调度

2、crontab -l 列出当前有那些任务调度

3、service crond restart [重启任务调度]



# 第 12 章 实操篇 Linux磁盘分区、挂载

### 12.1 分区基础知识

#### 	12.1.1 分区的方式

1) mbr分区:
1.最多支持四个主分区
2.系统只能安装在主分区
3.扩展分区要占一个主分区
4.MBR最大只支持2TB，但拥有最好的兼容性.

2) gtp分区:
1.支持无限多个主分区(但操作系统可能限制，比如windows 下最多128个分区)
2最大支持18EB的大容量(1EB=1024 PB, 1PB=1024 TB )
3.windows7 64位以后支持gtp

#### 12.1.2 windows 下的磁盘分区

![](/Snipaste_2020-10-08_18-37-04.png)

### 12.2 Linux分区

#### 12.2.1原理介绍

1、Linux来说无论有几个分区，分给哪一目录使用，它归根结底就只有一个根目录，一个独立且
唯一的文件结构，Linux中每个分区都是用来组成整个文件系统的一- 部分。
2、Linux采用了一种叫“载入”的处理方法，它的整个文件系统中包含了一整套的文件和目录，
且将-一个分区和一个目录联系起来。这时要载入的-一个分区将使它的存储空间在-一个 目录下获得。
3、示意图

![](/Snipaste_2020-10-08_18-37-47.png)

#### 12.2.2 硬盘说明

1)Linux硬盘分IDE硬盘和SCSI硬盘，目前基本上是SCSI硬盘
2)对于IDE硬盘，驱动器标识符为“hdx~",其中“hd"表明分区所在设备的类型，这里是指IDE硬
盘了。“x”为盘号(a 为基本盘，b为基本从属盘，c为辅助主盘，d为辅助从属盘)，“一”代表分区，
前四个分区用数字1到4表示，它们是主分区或扩展分区，从5开始就是逻辑分区。例，hda3 表示为
第一个IDE硬盘上的第三个主分区或扩展分区,hdb2表示为第二个IDE硬盘上的第二个主分区或扩展
分区。
3)对于SCSI硬盘则标识为“sdx~"，SCSI 硬盘是用“sd"来表示分区所在设备的类型的，其余则
和IDE硬盘的表示方法- -样。

12.2.3 使用lsblk 指令查看当前系统的分区情况

![](/Snipaste_2020-10-08_18-38-56.png)

### 12.3 挂载的经典案例

需求是给我们的Linux系统增加一个新的硬盘 并且挂载到/home/newdisk

![](/Snipaste_2020-10-08_18-43-34.png)

#### 12.3.1 如何增加一块硬盘

1 )虚拟机添加硬盘
2)分区	fdisk /dev/sdb
3)格式化	mkfs -t ext4 /dev/sdbl
4)挂载先创建 - -个/home/newdisk, 挂载 	mount /dev/sdb1	/home/newdisk
5)设置可以自动挂载(永久挂载，当你重启系统，仍然可以挂载到/home/newdisk)。
vim /etc/fstab
/dev/sdb1	/home/newdisk	ext4	defaults	00

### 12.4 具体的操作步骤整理

#### 12.4.1 虚拟机增加硬盘步骤1

在[虚拟机]菜单中，选择[设置]，然后设备列表里添加硬盘，然后一路[下一步]，中间只
有选择磁盘大小的地方需要修改，至到完成。然后重启系统(才能识别) !

![](/Snipaste_2020-10-08_18-53-56.png)

#### 12.4.2 虚拟机增加步骤2

分区命令fdisk /dev/sdb
开始对/sdb分区
●m	显示命令列表
°p	显示磁盘分区同fdisk - 1
*n	新增分区
●d	删除分区
.w	写入并退出
说明:开始分区后输入n， 新增分区，然后选择p，分区类型为主分区。两次回车默认剩余全部空间，最后输入w 写入分区并退出，若不保存退出输入q

![](/Snipaste_2020-10-08_18-56-12.png)

#### 12.4.3 虚拟机增加硬盘步骤3

格式化硬盘

分区命令 mkfs -t ext4 /dev/sdb1

其中ext4 是分区类型

#### 12.4.4 虚拟机增加硬盘步骤 4

挂载:将一个分区与一个目录联系起来，
●mount	设备名称	挂载目录
●例如:mount	 /dev/sdbl	/newdisk
●umount	设备名称	或者.	挂载目录
●例如:	umount	/dev/sdbl	或者	umount	/newdisk

#### 12.4.5 虚拟机增加硬盘步骤5

永久挂载 通过修改 /etc/fstab 实现挂载

添加完成后 执行mount -a 即刻生效

![](/Snipaste_2020-10-08_19-00-48.png)

### 12.5 磁盘情况查询

#### 12.5.1查询系统整体磁盘使用情况

基本语法

df -h

应用实例

查询系统整体磁盘使用情况

![](/Snipaste_2020-10-08_19-03-28.png)

#### 12.5.2 查询指定目录的磁盘占用情况

基本语法

du -h /目录

查询指定目录的磁盘占用情况，默认为当前目录

-s	指定目录占用大小汇总
-h	带计量单位
-a	含文件
--max-depth=1	子 目录深度

-c	列出明细的同时，增加汇总值

应用实例

查询 /opt 目录的磁盘占用情况 深度为1

![](/Snipaste_2020-10-08_19-05-21.png)

### 12.6 磁盘情况 工作实用指令

1、统计 /home 文件夹下文件的个数

![](/Snipaste_2020-10-08_19-06-04.png)

2、统计 /home 文件夹下目录个数

![](/Snipaste_2020-10-08_19-06-21.png)

3、统计 /home 文件夹的个数

![](/Snipaste_2020-10-08_19-09-14.png)

4、统计文件夹目录个数 包括子文件夹里的

![](/Snipaste_2020-10-08_19-09-37.png)

5、以树状显示目录结构

![](/Snipaste_2020-10-08_19-09-54.png)

# 第 13 章 实操篇 网路配置

### 13.1 Linux网络配置原理图(含虚拟机)

目前我们的网络配置采用的是 NAT

![](/Snipaste_2020-10-09_09-24-17.png)

### 13.2 查看网络IP 和 网关

#### 13.2.1 查看虚拟网络编辑器

![](/Snipaste_2020-10-09_09-25-25.png)

#### 13.2.2 修改 ip 地址 (修改网络的ip)

![](/Snipaste_2020-10-09_09-25-58.png)

#### 13.2.3 查看网关

![](/Snipaste_2020-10-09_09-26-38.png)

#### 13.2.4 查看 windows 环境中 VMent8的配置(ifconfig命令)

1、使用ifconfig查看

2、界面查看

![](/Snipaste_2020-10-09_09-27-41.png)

### 13.3 ping 测试主机之间网络连通

#### 13.3.1 基本语法

ping 目的主机

#### 13.3.2 应用实例

测试当前服务器是否可以连接百度

ping	baidu.com

### 13.4 linux网络环境配置

#### 13.4.1 第一种方法(自动获取)

![](/Snipaste_2020-10-09_09-29-30.png)

缺点: linux启动后会自动获取IP,缺点是每次自动获取的ip地址可能不-一样。这个不适用于做服
务器，因为我们的服务器的ip需要时固定的。

#### 13.4.2 第二种方法(指定固定的ip)

说明
直接修改配置文件来指定IP，并可以连接到外网(程序员推荐)，编辑
/etc/sysconfig/network- scripts/ifcfg-eth0
要求:将ip地址配置的静态的，ip 地址为192. 168.184.130

![](/Snipaste_2020-10-09_09-30-31.png)

修改后 一定要重启服务

1、service network restart

2、reboot 重启系统

![](/Snipaste_2020-10-09_09-31-11.png)           

#  第 14 章 实操篇 进程管理

### 14.1 进程的基本管理

1、在LINUX中，每个执行的程序(代码)都称为一个进程。每-一个进程都分配-一个ID号。
2、每-一个进程，都会对应-一个父进程，而这个父进程可以复制多个子进程。例如www服务器。
3、每个进程都可能以两种方式存在的。前台与后台，所谓前台进程就是用户目前的屏幕.上可以进
行操作的。后台进程则是实际在操作，但由于屏幕上无法看到的进程，通常使用后台方式执行。
4、一般系统的服务都是以后台进程的方式存在，而且都会常驻在系统中。直到关机才才结束。

#### 14.2.1 说明：

查看进行使用的指令是 ps 一般来说使用的参数是 ps-aux

![](/Snipaste_2020-10-09_10-46-16.png)

![](/Snipaste_2020-10-09_10-46-26.png)

#### 14.2.2 ps 指令详解

1、指令 ps -aux |grep xxx 比如我看看有没有 sshd服务

2、指令说明

.System V展示风格
●USER:用户名称
●PID:进程号
.%CPU:进程占用CPU的百分比
●%MEM:进程占用物理内存的百分比
●VSZ:进程占用的虚拟内存大小(单位: KB)
●RSS:进程占用的物理内存大小(单位: KB)
●TT:终端名称,缩写.
●STAT:进程状态，其中S-睡眠，s- 表示该进程是会话的先导进程，N-表示进程拥有比普通优先级更低的优先级，R-正在运行，D-短期等待，Z-僵死进程，T-被跟踪或者被停止等等
●STARTED:进程的启动时间
●TIME: CPU时间，即进程使用CPU的总时间
●COMMAND:启动进程所用的命令和参数，如果过长会被截断显示

#### 14.2.3 应用实例

要求，以全格式显示当前所有的进程，查看进程的父进程

![](/Snipaste_2020-10-09_10-48-25.png)

ps-ef是以全格式显示当前所有的进程
●-e显示所有进程。-f全格式。
●是BSD风格
●UID:用户ID
●PID:进程ID
●PPID:父进程ID
●C: CPU用于计算执行优先级的因子。数值越大，表明进程是CPU密集型运算，执行优先级会降低;数值越小，表明进程是I/O密集型运算，执行优先级会提高
●STIME:进程启动的时间
●TTY:完整的终端名称
●TIME: CPU 时间
●CMD:启动进程所用的命令和参数
思考题，如果我们希望查看sshd 进程的父进程号是多少，应该怎样查询?

![](/Snipaste_2020-10-09_10-48-53.png)

### 14.3 终止进程 kill  和killall

#### 14.3.1 介绍

若是某个进程执行一半需要停止时，或是已消了很大的系统资源时，此时可以考虑停止该进程。
使用kill命令来完成此项任务。

#### 14.3.2 基本语法

kill [选项] 进程号(功能描述:通过进程号杀死进程)
killall进程名称(功能描述:通过进程名称杀死进程，也支持通配符，这在系统因负载过大而变
得很慢时很有用)

#### 14.3.3 常用选项

-9 表示强迫进程立即停止

#### 14.3.4 最佳实践

案例1、踢掉某个非法登录用户

![](/Snipaste_2020-10-09_10-51-11.png)

案例3 种植多个gedit 编辑器 killall 通过进程名称来终止进程

![](/Snipaste_2020-10-09_10-52-32.png)

案例4 强制杀掉一个终端

![](/Snipaste_2020-10-09_10-53-03.png)

### 14.4 查看进程树 pstree

#### 14.4.1 基本语法

pstree[选项] 可以更加直观的来看进程信息

#### 14.4.2 常用选项

-p 显示进程PID

-u:显示进程的所属用户

#### 14.4.3 应用案例

1、请你将树状的形式显示进程pid

![](/Snipaste_2020-10-09_10-54-57.png)

2、请你树状的形式进程用的id

pstree -u 即可

### 14.5 服务(Service 管理)

#### 14.5.1 介绍

服务(service)本质就是进程，但是是运行在后台的，通常都会监听某个端口，等待其它程序的请
求，比如(mysql , sshd防火 墙等)，因此我们又称为守护进程，是Linux中非常重要的知识点。[原 
理图]

![](/Snipaste_2020-10-09_10-55-57.png)

#### 14.5.2 service管理指令

service 服务名 【start|stop |restart |reload|status】

在Centos7中命令使用systemctl

#### 14.5.3 使用案例

1、查看当前防火墙的状况 关闭防火墙和重启防火墙

![](/Snipaste_2020-10-09_10-57-27.png)

Centos7中 systemctl start firewalld

#### 14.5.4 细节讨论

1、关闭或者启用防火墙后，立即生效 [telnet 测试 某个端口就行]

![](/Snipaste_2020-10-09_10-58-44.png)

2、这种方式只是临时生效 当重启系统后还是回归以前服务的设置

如果希望设置某个服务自启动或关闭永久生效 要使用chkconfig指令 

#### 14.5.5 查看服务名

方式1、使用setup ->系统服务 就可以看到

![](/Snipaste_2020-10-09_11-00-56.png)

#### 14.5.6 服务的运行级别(runlevel)

查看或者修改默认级别:
vi /etc/inittab
Linux系统有7种运行级别(runlevel):常用的是级别3和5
●运行级别0:系统停机状态，系统默认运行级别不能设为0，否则不能正常启动
●运行级别1:单用户工作状态，root 权限，用于系统维护，禁止远程登陆
●运行级别2:多用户状态(没有NFS)，不支持网络
●运行级别3:完全的多用户状态(有NFS)，登陆后进入控制台命令行模式
●运行级别4:系统未使用，保留
●运行级别5: X11控制台，登陆后进入图形GUI模式
●运行级别6:系统正常关闭并重启，默认运行级别不能设为6，否则不能正常启动

#### 14.5.7 开机流程说明

![](/Snipaste_2020-10-09_11-01-42.png)

#### 14.5.8 chkconfig指令

介绍

通过 chkconfig 命令 可以给每个服务的各个运行级别设置自启动/关闭

基本语法

1、查看服务 chkconfig --list|grep xxx

![](/Snipaste_2020-10-09_11-02-55.png)

![](/Snipaste_2020-10-09_11-03-05.png)

#### 14.5.9 应用案例

1)案例1:请显示当前系统所有服务的各个运行级别的运行状态
	bash> chkconfig --list
2)案例2:请查看sshd服务的运行状态
	bash> service sshd status
3)案例3:将sshd服务在运行级别5下设置为不自动启动，看看有什么效果?
	bash> chkconfig --level 5 sshd off
4)案例4:当运行级别为5 时，关闭防火墙。
	bash> chkconfig --level 5 iptables off
5)案例5:在所有运行级别下， 关闭防火墙
	bash> chkconfig iptables off
6)案例6:在所有运行级别下， 开启防火墙
	bash> chkconfig iptables on

#### 14.5.10 使用细节

1、chkconfig 重新设置服务后自启动或关闭，需要重启机器 reboot才能生效

### 14.6 动态监控进程

#### 14.6.1 介绍

top与ps命令很相似。它们都用来显示正在执行的进程。Top与ps最大的不同之处，在于top在
执行一段时间可以更新正在运行的的进程。

#### 14.6.3 选项说明

![](/Snipaste_2020-10-09_11-05-39.png)

#### 14.6.4 应用实例

1、监视特定用户

top 输入此命令 回车键 查看执行过程

u 然后输入u 回车 在输入用户名 即可

![](/Snipaste_2020-10-09_11-06-47.png)2、

2、 终止指定的进程

k 然后输入k 回车 在输入要结束的进程ID号

![](/Snipaste_2020-10-09_11-08-00.png)

3、指定系统状态的更新时间 每隔10秒自动更新 默认是3秒

bash> top -d 10



#### 14.6.5 查看系统网络情况 netstat(重要)

基本语法

netstat[选项]

netstat -anp

选项说明

-an 按一定顺序排序输出

-p 显示那个进程在调用

应用案例

查看系统所有的网络服务

![](/Snipaste_2020-10-09_11-10-24.png)



# 第 15 章 实操篇 RPM 和 YUM

### 15.1 rpm 包的管理

#### 15.1.1 介绍

​	一种用于互联网下载包的打包及安装工具，它包含在某些Linux分发版中。它生成具有.RPM
扩展名的文件。RPM是RedHat Package Manager( RedHat软件包管理工具)的缩写,类似windows
的setup.exe,这一文件格式名称虽然打上了RedHat 的标志，但理念是通用的。
Linux的分发版本都有采用(suse,redhat, centos等等)，可以算是公认的行业标准了。

#### 15.1.2 rpm包的简单查询指令

查询以及安装的rpm列表 rpm -qa | grep xx

请查询看下一下 当前 linux有没有安装firefox

![](/Snipaste_2020-10-09_11-43-24.png)



#### 15.1.3 rpm报名基本格式

一个rpm包名: firefox-45.0.1-1 .el6. .centos.x86_ _64.rpm
名称: firefox
版本号: 45.0.1-1

适用操作系统: el6.centos.x86_ _64
表示centos6.x的64位系统.
如果是i686、i386 表示32位系统，noarch 表示通用。。

15.1.4 rpm包的其他查询指令

rpm -qa 查询所有所安装的所有 rpm 软件包

rpm -qa | more 分页显示

rpm -qa |grep X[rpm -qa |grep firefox]

![](/Snipaste_2020-10-09_11-44-53.png)

pm-q软件包名: 查询软件包是否安装

rpm -q firefox

rpm-qi软件包名:查询软件包信息

![](/Snipaste_2020-10-09_11-45-14.png)

rpm -qi file

rpm -ql软件包名:查询软件包中的文件

rpm -ql firefox

![](/Snipaste_2020-10-09_11-45-37.png)

pm-qf文件全路径名查询文件所属的软件包
rpm -qf /etc/passwd
rpm -qf /root/installlog

![](/Snipaste_2020-10-09_11-46-15.png)

15.1.5 卸载rpm 包

基本语法

rpm -e RPM 包名称

应用案例

1、删除firefox软件包

![](/Snipaste_2020-10-09_11-47-00.png)

●细节问题
1)如果其它软件包依赖于您要卸载的软件包，卸载时则会产生错误信息。
如: $rpm-efoo
removing these packages would break dependencies: foo is needed by bar- 1.0-1
2)如果我们就是要删除foo 这个rpm包，可以增加参数--nodeps ,就可以强制删除，但是- -般
不推荐这样做，因为依赖于该软件包的程序可能无法运行
如: $ rpm -e --nodeps foo
带上--nodeps就是强制删除。

#### 15.1.6 安装rpm包

基本语法

rpm -ivh RPM 包全路径名称

●参数说明
	i=install安装
	v= -verbose提示
	h=hash进度条
●应用实例
1)演示安装firefox浏览器
步骤先找到firefox的安装rpm包,你需要挂载上我们安装centos的iso文件，然后到/media/下去找rpm找。
cp firefox-45.0.1-1 .el6 centos .x86_ _64.pm /opt/

![](/Snipaste_2020-10-09_11-48-26.png)

### 15.2 yum

#### 15.1 介绍：

Yum是一个Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包
并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包。使用yum的前提是可以联
网。

![](/Snipaste_2020-10-09_12-31-39.png)

#### 15.2.2 yum的基本指令

●查询yum服务器是否有需要安装的软件
	yum listlgrep xx	软件列表
●安装指定的yum包
	yum install XXx	下载安装

#### 15.2.3 yum 应用案例

1、请用yum的方式来安装firefox

![](/Snipaste_2020-10-09_12-33-43.png)

2、安装

![](/Snipaste_2020-10-09_12-32-56.png)

会安装最新版本的软件

![](/Snipaste_2020-10-09_12-34-33.png)



# **第** 16章 JavaEE 定制篇 搭建 JavaEE 环境

### 16.1 概述

#### 16.1.1 示意图

![](/Snipaste_2020-10-09_13-41-56.png)

### 16.2 安装JDK

#### 16.2.1 安装步骤

1、先通过软件上传文件 到 /opt目录下

2、解压缩到/opt tar -axvf

3、配置环境变量的配置文件 vim /etc/profile

![](/Snipaste_2020-10-09_13-43-27.png)

JAVA_HOME=/opt/jdk.1.7.0_79

PATH=/opt/jdk1.7.0_79/bin:$PATH

export JAVA_HOME PATH

3、需要注销用户 环境变量才能生效

logout或重启

4、在任何环境下都能使用java 或 javac

![](/Snipaste_2020-10-09_13-45-49.png)

#### 16.2.3 测试是否能安装成功

编写简单helloworld.java 

![](/Snipaste_2020-10-09_13-46-25.png)



### 16.3 安装tomcat

#### 16.3.1 步骤

1、解压到/opt

![](/Snipaste_2020-10-09_13-49-07.png)

2、启动 tomcat /.startup.sh

先进入到 tomcat 的 bin目录

![](/Snipaste_2020-10-09_13-49-55.png)

![](/Snipaste_2020-10-09_13-50-13.png)

使用Linux本地浏览器就能访问到tomcat

3、开放端口8080 外网能才能访问到 tomcat

```bash
1、Centos7 命令
查看防火墙状态 systemctl status firewalld
开启防火墙 systemctl start firewalld  
关闭防火墙 systemctl stop firewalld
开启防火墙 service firewalld start 
若遇到无法开启
先用：systemctl unmask firewalld.service 
然后：systemctl start firewalld.service

2、对外开发端口
查看想开的端口是否已开：
firewall-cmd --query-port=6379/tcp

3、添加指定需要开放的端口：
firewall-cmd --add-port=123/tcp --permanent
重载入添加的端口：
firewall-cmd --reload
查询指定端口是否开启成功：
firewall-cmd --query-port=123/tcp

移除指定端口：
firewall-cmd --permanent --remove-port=123/tcp
```

#### 16.4 Eclipse的安装

#### 16.4.1 步骤

1、解压缩到/opt

![](/Snipaste_2020-10-09_13-53-53.png)

2、启动eclipse 配置jre和server

启动方式1、创建一个快捷方式

启动方式2、进入到eclipse解压后的文件夹 然后执行 ./eclipse 即可

3、编写jsp页面 测试成功

![](/20201009135519.png)

### 16.5 mysql的安装和配置

#### 16.5.1 安装步骤和文档

![](/Snipaste_2020-10-09_14-10-38.png)

#### 16.5.2 严格按照文档执行



### 16.6 Redisa 安装

#### 16.6.1 redis 下载

https://redis.io/download

![](/Snipaste_2020-10-10_09-30-41.png)

这里下载的是5.0.9版本 6.0版本目前安装会出现问题

#### 16.6.2 将 redis 安装文件上传到 linux 服务器

1、解压

tar -zxvf redis-XXX.tar.gz

2、进入到 reids目录 进行编译

make

![](/Snipaste_2020-10-10_09-33-43.png)

3、安装并指定安装目录

**make install PREFIX=/usr/local/redis**

![](/Snipaste_2020-10-10_09-35-33.png)

4、拷贝 redis.conf 配置文件

![](/Snipaste_2020-10-10_09-36-43.png)

5、修改 redis.conf 配置文件

![](/Snipaste_2020-10-10_09-38-25.png)

6、启动 redis-server 和 redis-cli 进行测试

指定配置文件进行启动

![](/Snipaste_2020-10-10_09-39-15.png)

![](/Snipaste_2020-10-10_09-39-34.png)

指定端口进行启动

7、测试

![](/Snipaste_2020-10-10_09-40-09.png)



参考文档 https://www.cnblogs.com/heqiuyong/p/10463334.html



# 第 17 章 大数据定制篇 Shell编程

### 17.1 为什么要学 Shell 编程

1、Linux运维工程师在进行服务器集群管理时，需要编写Shell程序来进行服务器管理。

2、对于JavaEE和Python程序员来说，工作的需要，你的老大会要求你编写- -些Shell脚本进行程序或者是服务器的维护，比如编写--个定时备份数据库的脚本。

3、对于大数据程序员来说，需要编写Shell程序来管理集群。.

### 17.2 Shell 是什么

![](/Snipaste_2020-10-09_19-59-43.png)

Shell是一个命令行解释器,它为用户提供了一个向Linux内核发送请求以便运行程序的界面系统
级程序，用户可以用Shell来启动、挂起、停止甚至是编写- -些程序.

#### 17.3 Shell 编程快速入门-Shell脚本执行方式

#### 17.3.1 脚本格式要求

1、脚本以#! /bin/bash 开头

2、脚本需要有可执行权限

#### 17.3.2 编写一个 Shell脚本

需求说明

​	创建一个 Shell脚本 输出helloworld

![](/Snipaste_2020-10-09_20-01-46.png)

#### 17.3.3 脚本常用执行方式

方式1(输入脚本的绝对路径或相对路径)
	1)首先要赋予helloworld.sh脚本的+x权限
	2)执行脚本

![](/Snipaste_2020-10-09_20-02-21.png)

方式2(sh+脚本) 不推荐

说明 不用赋予脚本+x权限 直接执行即可

![](/Snipaste_2020-10-09_20-03-02.png)

### 17.4 shell的变量

17.4.1 Shell的变量介绍

1) Linux Shell中的变量分为，系统变和用户自定义变量。
2)系统变量: SHOME、 $PWD、$SHELL、$USER等等
比如:echo SHOME等等..

![](/Snipaste_2020-10-09_20-03-50.png)

3)显示当前shell所有变量： set

#### 17.4.2 shell变量的定义

●基本语法
1)定义变量:变量=值
2)撤销变量: unset 变量
3)声明静态变量: readonly 变量，注意:不能
unset
●快速入门
案例1:定义变量A
案例2:撤销变量A

![](/Snipaste_2020-10-09_20-04-42.png)

#### 17.4.3 定义变量的规则

1、变量名称可以由字母、数字和下划线组成，但是不能以数字开头。
2、等号两侧不能有空格
3、变量名称一般习惯为大写

#### 17.4.4 将 命令的返回值赋给变量(重点)

1、A='ls-la' 反引号，运行里面的命令，并把结果返回给变量A
2、A=S(ls-la) 等价于反引号

![](/Snipaste_2020-10-09_20-06-57.png)

### 17.5设置环境变量

#### 17.5.1基本语法

1、export变量名=变量值（功能描述：将shell变量输出为环境变量）

2、source配置文件（功能描述：让修改后的配置信息立即生效）

3、echo$变量名（功能描述：查询环境变量的值）

![](/Snipaste_2020-10-09_20-07-46.png)

#### 17.5.2 快速入门

1)在/etc/profile文件中定义TOMCAT_HOME环境变量

![](/Snipaste_2020-10-09_20-08-12.png)

2)查看环境变量TOMCAT_HOME的值

echo$TOMCAT_HOME

3)在另外一个shell程序中使用TOMCAT_HOME

![](/Snipaste_2020-10-09_20-08-40.png)

注意：在输出TOMCAT_HOME环境变量前，需要让其生效

source/etc/profile



### 17.6位置参数变量

#### 17.6.1介绍

当我们执行一个shell脚本时，如果希望获取到命令行的参数信息，就可以使用到位置参数变量，比如：./myshell.sh100200,这个就是一个执行shell的命令行，可以在myshell脚本中获取到参数信息

#### 17.6.2基本语法

$n（功能描述：n为数字，$0代表命令本身，$1-$9代表第一到第九个参数，十以上的参数，十以上的参数需要用大括号包含，如${10}）

$*（功能描述：这个变量代表命令行中所有的参数，$*把所有的参数看成一个整体）

$@（功能描述：这个变量也代表命令行中所有的参数，不过$@把每个参数区分对待）

$#（功能描述：这个变量代表命令行中所有参数的个数）

#### 17.6.3位置参数变量应用实例

案例：编写一个shell脚本positionPara.sh，在脚本中获取到命令行的各个参数信息

![](/Snipaste_2020-10-09_20-10-10.png)

![](/Snipaste_2020-10-09_20-10-20.png)

### 17.7预定义变量

#### 17.7.1基本介绍

就是shell设计者事先已经定义好的变量，可以直接在shell脚本中使用

#### 17.7.2基本语法

$$（功能描述：当前进程的进程号（PID））

$!（功能描述：后台运行的最后一个进程的进程号（PID））

$？（功能描述：最后一次执行的命令的返回状态。如果这个变量的值为0，证明上一个命令正确执行；如果这个变量的值为非0（具体是哪个数，由命令自己来决定），则证明上一个命令执行不正确了。）

#### 17.7.3应用实例在一个shell脚本中简单使用一下预定义变量

![](/Snipaste_2020-10-09_20-11-08.png)

### 17.8运算符

#### 17.8.1基本介绍

学习如何在shell中进行各种运算操作。

#### 17.8.2基本语法

1)“$((运算式))”或“$[运算式]”

2)exprm+n注意expr运算符间要有空格

3)exprm-n

4)expr\*,/,%乘，除，取余•

应用实例案例1：计算（2+3）X4的值1)

$((运算式))

![](/Snipaste_2020-10-09_20-13-21.png)

案例2：请求出命令行的两个参数[整数]的和

![](/Snipaste_2020-10-09_20-13-38.png)



### 17.9条件判断

判断语句

#### 17.9.1•基本语法

（注意condition前后要有空格）

#非空返回true，可使用$?验证（0为true，>1为false）

#### 17.9.2•应用实例

[atguigu]返回true

[]返回false

[condition]&&echoOK||echonotok条件满足，执行后面的语句

#### 17.9.3•常用判断条件

1)两个整数的比较

=字符串比较

-lt小于

-le小于等于

-eq等于

-gt大于

-ge大于等于

17.9.4应用实例

案例1："ok"是否等于"ok"

判断语句：

![](/Snipaste_2020-10-09_20-15-52.png)

案例2：23是否大于等于22

判断语句:

![](/Snipaste_2020-10-09_20-16-12.png)

案例3：/root/install.log目录中的文件是否存在

判断语句

![](/Snipaste_2020-10-09_20-16-35.png)

### 17.10 流程控制

#### 17.10.1if判断

基本语法

if[ 条件判断式 ];then

​	程序

fi

或者

if[ 条件判断式 ]

​	then

程序

elif[ 条件判断式 ]

​	then

​		程序

fi

注意事项：（1）[条件判断式]，中括号和条件判断式之间必须有空格	(2)推荐使用第二种方式

应用实例案例：请编写一个shell程序，如果输入的参数，大于等于60，则输出"及格了"，如果小于60,则输出"不及格"

![](/Snipaste_2020-10-09_20-18-34.png)

#### 17.10.2 case 语句

![](/Snipaste_2020-10-09_20-19-06.png)

;; 

esac

•应用实例案例1：当命令行参数是1时，输出"周一",是2时，就输出"周二"，其它情况输出"other"

![](/Snipaste_2020-10-09_20-19-33.png)

### 17.10.3 for循环 

基本语法1

for 变量 in 值1 值2 值3... 

do

​	程序

done

应用实例

案例1：打印命令行输入的参数【会使用到$*$@】

![](/Snipaste_2020-10-09_20-20-35.png)

•基本语法2

for((初始值;循环控制条件;变量变化))

do

程序

done

应用实例

案例1：从1加到100的值输出显示

![](/Snipaste_2020-10-09_20-21-11.png)

#### 17.10.4while循环

基本语法1

while[条件判断式]

​	do

​		程序

​	done

应用实例

案例1：从命令行输入一个数n，统计从1+..+n的值是多少？

![](/Snipaste_2020-10-09_20-21-59.png)

### 17.11 read 读取控制台输入

#### 17.11.1 基本语法

read(选项)(参数)

选项：

-p：指定读取值时的提示符；

-t：指定读取值时等待的时间（秒），如果没有在指定的时间内输入，就不再等待了。。

参数

变量：指定读取值的变量名

#### 17.11.2应用实例案例

1：读取控制台输入一个num值案例

2：读取控制台输入一个num值，在10秒内输入。

![](/Snipaste_2020-10-09_20-23-11.png)

### 17.12 函数

#### 17.12.1函数介绍

shell编程和其它编程语言一样，有系统函数，也可以自定义函数。系统函数中，我们这里就介绍两个。

#### 17.12.2系统函数

basename基本语法

功能：返回完整路径最后/的部分，常用于获取文件名

basename [pathname] [suffix]

basename [string] [suffix]（功能描述：basename命令会删掉所有的前缀包括最后一个（‘/’）字符，然后将字符串显示出来。

选项：

suffix为后缀，如果suffix被指定了，basename会将pathname或string中的suffix去掉。

dirname基本语法

功能：返回完整路径最后/的前面的部分，常用于返回路径部分

dirname文件绝对路径（功能描述：从给定的包含绝对路径的文件名中去除文件名（非目录的部分），然后返回剩下的路径（目录的部分））

#### 17.12.3 应用实例

案例1：请返回/home/aaa/test.txt的"test.txt"部分

![](/Snipaste_2020-10-09_20-26-07.png)

#### 17.12.4 自定义函数

基本语法

[function]funname[()]

{

​	Action;

​	[returnint;]

}

调用直接写函数名：

funname[值]

应用实例案例

1：计算输入两个参数的和（read），getSum

![](/Snipaste_2020-10-09_20-27-18.png)

17.13Shell编程综合案例

需求分析

1)每天凌晨2:10备份数据库atguiguDB到/data/backup/db

2)备份开始和备份结束能够给出相应的提示信息

3)备份后的文件要求以备份时间为文件名，并打包成.tar.gz的形式，比如：

2018-03-12_230201.tar.gz

4)在备份的同时，检查是否有10天前备份的数据库文件，如果有就将其删除。

编写一个shell脚本。思路分析

![](/Snipaste_2020-10-09_20-27-59.png)

代码实现

```sh
#!/bin/bash

#完成数据库的定时备份。
#备份的路径
BACKUP=/data/backup/db
#当前的时间作为文件名
DATETIME=$(date +%Y_%m_%d_%H%M%S)
#可以输出变量调试
#echo ${DATETIME}

echo "=======开始备份========"
echo "=======备份的路径是 $BACKUP/$DATETIME.tar.gz"

#主机
HOST=localhost
#用户名
DB_USER=root
#密码
DB_PWD=root
#备份数据库名
DATABASE=atguiguDB
#创建备份的路径
#如果备份的路径文件夹存在，就使用，否则就创建
[ ! -d "$BACKUP/$DATETIME" ] && mkdir -p "$BACKUP/$DATETIME"
#执行mysql的备份数据库的指令
mysqldump -u${DB_USER} -p${DB_PWD} --host=$HOST  $DATABASE | gzip > $BACKUP/$DATETIME/$DATETIME.sql.gz
#打包备份文件
cd $BACKUP
tar -zcvf $DATETIME.tar.gz $DATETIME
#删除临时目录
rm -rf $BACKUP/$DATETIME

#删除10天前的备份文件
find $BACKUP -mtime +10 -name "*.tar.gz" -exec rm -rf {} \;
echo "=====备份文件成功==========="

```

![](/Snipaste_2020-10-09_20-28-42.png)



# 第 18 章 Python定制篇 开发平台 Ubuntu

18.1Ubuntu的介绍

Ubuntu（友帮拓、优般图、乌班图）是一个以桌面应用为主的开源GNU/Linux操作系统，Ubuntu是GNU/Linux，支持x86、amd64（即x64）和ppc架构，由全球化的专业开发团队（CanonicalLtd）打造的。

专业的Python开发者一般会选择Ubuntu这款Linux系统作为生产平台

.温馨提示：Ubuntu和Centos都是基于GNU/Linux内核的，因此基本使用和Centos是几乎一样的，它们的各种指令可以通用，同学们在学习和使用Ubuntu的过程中，会发现各种操作指令在前面学习CentOS都使用过。只是界面和预安装的软件有所差别。

Ubuntu下载地址：http://cn.ubuntu.com/download

![](/Snipaste_2020-10-09_21-26-16.png)

### 18.2 Ubuntu的安装

![](/Snipaste_2020-10-09_21-27-12.png)

#### 18.2.2 设置U步辇图支持中文

默认安装的ubuntu中只有英文语言，因此是不能显示汉字的。要正确显示汉字，需要安装中文语言包。

安装中文支持步骤

1.单击左侧图标栏打开SystemSettings（系统设置）菜单，点击打开LanguageSupport（语言支持）选项卡。

2.点击Install/RemoveLanguages，在弹出的选项卡中下拉找到Chinese(Simplified)，即中文简体，在后面的选项框中打勾。然后点击ApplyChanges提交，系统会自动联网下载中文语言包。（保证ubuntu是联网的）。

3.这时“汉语（中国）”在最后一位因为当前第一位是”English”，所以默认显示都是英文。我们如果希望默认显示用中文，则应该将“汉语（中国）”设置为第一位。设置方法是拖动，鼠标单击“汉语（中国）”，当底色变化（表示选中了）后，按住鼠标左键不松手，向上拖动放置到第一位。

4.设置后不会即刻生效，需要下一次登录时才会生效

![](/Snipaste_2020-10-09_21-28-02.png)

### 18.3 Ubuntu 的root用户

#### 18.3.1介绍

安装ubuntu成功后，都是普通用户权限，并没有最高root权限，如果需要使用root权限的时候，通常都会在命令前面加上sudo。有的时候感觉很麻烦。

我们一般使用su命令来直接切换到root用户的，但是如果没有给root设置初始密码，就会抛出su:Authenticationfailure这样的问题。所以，我们只要给root用户设置一个初始密码就好了。

#### 18.3.2给root用户设置密码并使用

1)输入sudopasswd命令，输入一般用户密码并设定root用户密码。

2)设定root密码成功后，输入su命令，并输入刚才设定的root密码，就可以切换成root了。提示符$代表一般用户，提示符#代表root用户。

3)输入exit命令，退出root并返回一般用户4)以后就可以使用root用户了

![](/Snipaste_2020-10-09_21-28-55.png)

### 18.4Ubuntu下开发Python

#### 18.4.1说明

安装好Ubuntu后，默认就已经安装好Python的开发环境[Python2.7和Python3.5]。

![](/Snipaste_2020-10-09_21-29-28.png)

#### 18.4.2在Ubuntu下开发一个Python程序

1)	vimhello.py[编写hello.py]

提示：如果Ubuntu没有vim我们可以根据提示信息安装一个vim

apt install vim

![](/Snipaste_2020-10-09_21-30-32.png)

# 第1 9 章 Python定制篇apt软件管理和远程登录

### 19.1apt介绍

apt是AdvancedPackagingTool的简称，是一款安装包管理工具。在Ubuntu下，我们可以使用apt命令可用于软件包的安装、删除、清理等，类似于Windows中的软件管理工具。

unbuntu软件管理的原理示意图

![](/Snipaste_2020-10-09_21-31-56.png)

### 19.2 Ubuntu 软件操作的相关命令

sudoapt-getupdate更新源

sudoapt-getinstallpackage安装包

sudoapt-getremovepackage删除包

sudoapt-cachesearchpackage搜索软件包

sudoapt-cacheshowpackage获取包的相关信息，如说明、大小、版本等

sudoapt-getinstallpackage--reinstall重新安装包

sudoapt-get-finstall修复安装

sudoapt-getremovepackage--purge删除包，包括配置文件等

sudoapt-getbuild-deppackage安装相关的编译环境

sudoapt-getupgrade更新已安装的包

sudoapt-getdist-upgrade升级系统

sudoapt-cachedependspackage了解使用该包依赖那些包

sudoapt-cacherdependspackage查看该包被哪些包依赖

sudoapt-getsourcepackage下载该包的源代码

### 19.3更新Ubuntu软件下载地址

#### 19.3.1原理示意图

![](/Snipaste_2020-10-09_21-33-33.png)

### 19.3.2寻找国内镜像源

https://mirrors.tuna.tsinghua.edu.cn/

所谓的镜像源：可以理解为提供下载

软件的地方，比如Android手机上可以

下载软件的安卓市场；iOS手机上可

以下载软件的AppStor

![](/Snipaste_2020-10-09_21-34-21.png)

![](/Snipaste_2020-10-09_21-34-31.png)

### 19.3.3 备份Ubuntu默认的源地址

sudo cp/etc/apt/sources.list/etc/apt/sources.list.backup

![](/Snipaste_2020-10-09_21-35-01.png)

![](/Snipaste_2020-10-09_21-35-12.png)

#### 19.3.4 更新源服务器列表

![](/Snipaste_2020-10-09_21-35-29.png)

### 19.4 Ubuntu软件安装，卸载的最佳实践

#### 19.4.1案例说明：使用apt完成安装和卸载vim软件，并查询vim软件的信息：

sudo apt-getremovevim

![](/Snipaste_2020-10-09_21-36-04.png)

sudo apt-get installvim

![](/Snipaste_2020-10-09_21-36-31.png)

sudo apt-cache show vim

![](/Snipaste_2020-10-09_21-36-52.png)

### 19.5使用ssh远程登录Ubuntu

#### 19.5.1ssh介绍SSH

为SecureShell的缩写，由IETF的网络工作小组（NetworkWorkingGroup）所制定；SSH为建立在应用层和传输层基础上的安全协议。

SSH是目前较可靠，专为远程登录会话和其他网络服务提供安全性的协议。常用于远程登录，以及用户之间进行资料拷贝。几乎所有UNIX平台—包括HP-UX、Linux、AIX、Solaris、DigitalUNIX、Irix，以及其他平台，都可运行SSH。

使用SSH服务，需要安装相应的服务器和客户端。客户端和服务器的关系：如果，A机器想被B机器远程控制，那么，A机器需要安装SSH服务器，B机器需要安装SSH客户端。

和CentOS不一样，Ubuntu默认没有安装SSHD服务，因此，我们不能进行远程登录。

#### 19.5.2原理示意图：

![](/Snipaste_2020-10-09_21-37-39.png)

### 19.6使用ssh远程登录Ubuntu

#### 19.6.1安装SSH和启用

sudo apt-get install openssh-server执行上面指令后，在当前这台Linux上就安装了SSH服务端和客户端。

service sshd restart

执行上面的指令，就启动了sshd服务。会监听端口22

![](/Snipaste_2020-10-09_21-38-37.png)

### 19.6.2 在Windows使用XShell5/XFTP5登录Ubuntu

前面我们已经安装了XShell5，直接使用即可。

注意：使用atguigu用户登录，需要的时候再su-切换成root用户

![](/Snipaste_2020-10-09_21-39-05.png)

#### 19.6.3 从linux系统客户机远程登陆linux系统服务机

首先，我们需要在linux的系统客户机也要安装openssh-server

•基本语法：

ssh用户名@IP

例如：sshatguigu@192.168.188.131

使用ssh访问，如访问出现错误。可查看是否有该文件～/.ssh/known_ssh尝试删除该文件解决。

•登出登出命令：exit或者logout



![](/Snipaste_2020-10-09_21-40-16.png)

我亦无他，惟手熟尔

2020年10月9日