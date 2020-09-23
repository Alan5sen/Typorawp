##帮助命令

#### ·man
man命令为“menu”的缩写，主要可以查看各种命令的使用方法
```
eg: man ls
```
效果：出现`ls`命令的使用方法

##文件及目录管理命令
####·touch
1.创建一个文件
```
eg:touch file.txt
```
效果：在对应的目录创建一个名为`file.txt`的文件

2.修改时间戳为当前时间
文件在创建的时候，系统会自动记录时间，具体查看方式，由命令`ll`查看![红色框线部分为文件创建时间](https://upload-images.jianshu.io/upload_images/18749995-af3769feb611890c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
现在需要将1.txt的时间改为当前时间，即在此执行命令：
```
touch 1.txt
```
![时间变为了21:07](https://upload-images.jianshu.io/upload_images/18749995-ac9620942e301284.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####·mkdir
1.创建一个空目录
```
mkdir testdir
```
效果：创建了一个名为`testdir`的空目录（空文件夹）

2.递归创建多个文件夹（文件夹套文件夹）
```
mkdir -p testdir1/testdir2
```
效果：创建了两个文件夹，testdir2在testdir1中

####·rm
1.删除一个或多个文件

```
rm testfile1    #删除文件testfile1
rm testfile1 testfile2   #删除testfile1和testfile2
```

2.删除一个或多个目录
```
rm -r testdir1  #删除一个目录
rm -r testdir1 testdir2  #删除两个目录
```

3.强制删除某个文件/目录
```
rm -rf testfile1   #强制删除testfile1文件
rm -rf testdir1   #强制删除testdir1文件
```

######切记不能使用命令`rm -rf /*`（后果就是整个系统全部删光，不信的可以试试）

####·mv
1.移动文件/目录
```
mv testfile1 testdir    #将testfile1移动至testdir目录下
```

2.更改文件名
```
mv testfile1.txt  testfile2.txt     #将testfile1.txt改名为testfile2.txt
```

####·cp
复制文件/目录
```
cp file1.txt file2.txt   #将file1复制并命名为file2
cp -r dir1 dir2   #将目录dir1复制成dir2，若dir2已存在，即将dir1里面的东西复制进dir2
```
##目录切换
####·cd
在linux系统中，`.`代表当前目录,`..`代表上一个目录

```
cd dir1    #进入dir1目录中
cd ..      #返回上个目录
cd ~       #进入用户主目录（home）
cd -       #返回之前的目录
```

####·pwd
知道自己所在位置![图片.png](https://upload-images.jianshu.io/upload_images/18749995-0d71319e55e39c99.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##列出目录项
####·ls
1.列出当前目录所有文件
`ls`

2.列出当前目录所有文件（包括隐藏文件）
`ls -a`

3.以列表形式列出所有文件
`ls -al`
`ls -l`
`ll`
`ll -a`

4.直观的看出文件大小
`ls -lh`

####·tree
以树形的方式查看文件
```
tree    #在某目录内，直接使用tree查看本目录
tree  dir1    #查看dir1目录
````

##权限及所有者相关


在`ll`命令下，最前面可以查看文件的权限![图片.png](https://upload-images.jianshu.io/upload_images/18749995-f1ebd083f27dfc61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

那，这玩意怎么看懂呢
![图片.png](https://upload-images.jianshu.io/upload_images/18749995-f71f944ad96efb7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如上图，这里一共10个字母，将其分为4部分，第1部分为第1个字母，表示文件类型，剩下字母的每3个字母为一部分，分别为文件所有者权限（文件的创建者），文件所属用户组权限，其他人对这个文件的权限。好比为一个公司的BOSS，公司的其余员工，以及公司外的人。

文件类型如下表：
符号|文件类型
----|----
- |  普通文件
d|目录文件
p|管道文件
l|链接文件
b|块设备文件
c|字符设备文件
s|套接字文件

初学者只需要知道普通文件以及目录文件即可

剩下的三部分，结构组成都一样，由`r w x`组成
`r`可读权限
`w`可写权限
`x`可执行权限
以`drwxrwxr-x`为例，将其分为4部分，分别为：`d` `rwx` `rwx` `r-x`
`d`表示该文件为目录文件
`rwx`表示文件所有者有可读可写可执行权限
`rwx`表示文件所属用户组有可读可写可执行权限
`r-x`表示其他人只有可读可执行文件，但是不可写

而后3个部分中，若将三个字母表示为二进制数字，那权重分别为`4` `2` `1`。
若某用户权限为`rwx`，即可用7表示（4+2+1=7）
若某用户权限为`-wx`，即可用3表示（0+2+1=7）
以此类推即可。

####·chmod
1.使用数字修改文件权限

```
chmod  777  file1.txt     #给file1.txt最高权限
chmod  555  file2.txt    #给file2.txt可读可执行权限，但是不可写（4+0+1=5）
```

2.  使用字母修改文字权限
主要用`u g o a`四个字母,`+ - =`三个符号以及`r w x`实现
`u->user`
`g->group`
`o->others`
`a->all`
`+`加入权限
`-`删除权限
`=`设定权限
```
chmod  u+w  file1.txt       #给file1.txt的创建者增加可写权限
chmod  a-rwx  file2.txt       #给file2.txt的权限全部抹去
chmod  u=rx,g=rw,0=wx     #u g o的权限不同，分别···权限
```

####·chown
改变文件（目录）创建者的身份
![图片.png](https://upload-images.jianshu.io/upload_images/18749995-c6f13498b1135dc7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
在`ll`下，出现了两个名字，第一个为文件创建者，第二个为文件所属者
利用chown命令改变文件创建者的身份如下：

```
chown  harry  file1.txt    #将文件file1.txt的创建者改为harry
chown  harry  dir    #将目录dir的创建者改为harry
chown  -R  harry  dir    #将目录dir以及目录里面所有文件的创建者改为harry
```

####·chgrp
改变所属组的权限

```
chgrp  harry  file1.txt    #将文件file1.txt的所属者改为harry
chgrp  harry  dir    #将目录dir的所属者改为harry
chgrp  -R  harry  dir    #将目录dir以及目录里面所有文件的所属者改为harry
```

但是，也能用chown命令同时改变创建者以及所属者的身份：
```
chown  harry:alice  file1.txt        #创建者的身份改为harry，所属者的身份改为alice
```

##文本处理命令
####·cat
1.查看文件内容

```
cat file1.txt
```

2.创建一个文件，并且编写内容
```
cat  file2.txt    #创建file2.txt
hello world!    #编辑内容
#按Ctrl+C退出编辑
```

3.将几个文件合并为一个文件
```
cat  file1.txt  file2.txt  >  file3.txt    #file1 file2的内容全在file3内，而且file1在上面，file2在下面
```

####·more
基本操作：
`q`退出more
`空格键`下一页
`b`返回上一页

1.分页显示文本文件内容
```
more file1.txt
```

2.通过管道分页显示结果
```
ll /etc | more
```

####·less
基本操作：
上下建：滚动一行
Enter：向下滚动一行
Page Down：向下翻页
Page Up：向上翻页
b：向上翻页
d：向下翻页
q：退出
/字符串：向下查找对应字符串
?字符串：向上查找对应字符串
n：查找下一个
N：查找上一个

####·head
显示文本前n行内容（默认10行）
```
head file1.txt      #显示file1.txt的前10行
head  -n  5  file1.txt      #显示file1.txt的前5行
```

####·tail
1.显示后n行内容

```
tail -n 5 file1.txt
```

2.循环查看文件内容
```
tail -u file1.txt
```

3.从第n行开始显示信息
```
tail -n +5 file1.txt    #从第5行开始显示信息
```

####·sort
1.按照ASCII码进行排序
```
sort file1.txt
```

2.排序并去除重复行
```
sort  -u file1.txt
```

3.逆序排
```
sort -r file1.txt
```

##文本处理三剑客
####·grep
格式：`grep  [option]  pattern  file`
即  `grep  +  选项  +  查找的内容  +  查找的文件`
`option `主要包含四个
`-i`忽略大小写
`-r`递归搜索文件
`-n`标识结果所在的行数
`-s`不显示错误信息
当然，四个可以一起使用：

```
grep -rins word file.txt     #在file.txt里面查找word这个单词，不区分大小写并标识行数
```


####·sed
1.文本的搜索并替换
`sed 's/text/replace_text/g' file.txt`
即`sed  +  's/不要的内容/想要替代的内容/g'  +  对应文件`
如果直接将原文件也一起修改，加上`-i`即可
`sed -i 's/text/replace_text/g' file.txt`

2.变量替换
已匹配的字符串通过标记`&`来引用
```
echo this is an example | sed 's/\w\+/[&]/g' 
```
可以得到：
`[this] [is] [an] [example]`
![图片.png](https://upload-images.jianshu.io/upload_images/18749995-14c9f710463d9b4e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


####·awk
命令格式：
`awk  'BEGIN{命令表达式1}  命令表达式2  END{命令表达式3}'`
例：
```
echo -e "line1\nline2" | awk 'BEGIN{print "start"}  {print}  END{print  "End"}'
```
![图片.png](https://upload-images.jianshu.io/upload_images/18749995-26302c07b218e3ae.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

##磁盘管理命令
####·df
磁盘文件的可用空间
`df`显示磁盘状况（以字节方式显示）
`df -h`更方便看懂磁盘剩余量
`df ~`查看根目录的磁盘剩余量

####·du
1.显示目录或文件所占空间
`du` 查看当前目录所占空间
`du -h`

2.查看指定文件所占空间
`du -h file.txt`  查看file.txt所占空间大小
`du -h dir/file.txt`   查看dir目录下,file.txt所占空间大小

####·tar
1.压缩文件
`tar -zcvf file.tar.gz file1.txt file2.txt`将file1.txt和file2.txt压缩成file.tar.gz
语句也可写成`tar zcvf file.tar.gz file1.txt file2.txt`（短横可要可不要）

2.解压文件
`tar zxvf file.tar.gz`将file.tar.gz解压

`-z`支持gzip属性的文件
`-v`显示操作过程
`-f`是一个必须的参数，效果是使用档案名字，后面只能接文件名
`-c`建立压缩档案（create的意思）
`-x`解压

##进程管理命令
####·ps
列出当前系统正在运行的程序
`ps aux`列出当前`内存中`所有正在运行的程序
`ps aus | grep +关键字`找出包含关键字的进程
ps时列出的信息：

符号|意义
----|----
USER|该进程属于哪个账号
PID|该进程的编号
%CPU|该进程占用的CPU百分比
%MEM|该进程占用的物理内存百分比
VSZ|该进程消耗的虚拟内存量
RSS|该进程消耗的固定内存量
TTY|是否在本终端机运行
SATA|该程序主要运行的状态，具体状态如下表
START|该进程触发的时间
TIME|该进程实际使用CPU的时间
COMMAND|该程序的实际指令

符号|意义
----|----------
R|该程序正在运行，或者可被执行
S|该程序正在休眠，但是可被唤醒
T|该程序目前正在侦测，或者已停止
Z|僵尸程序

####·top
linux下常用的性能分析工具，类似于windows的任务管理器。

####·kill
linux下向进程发送命令的常用工具
`kill -l`查看kill命令支持发送哪些命令
`kill -9  进程编号`杀死进程

####·killall
杀死指定名字的进程
`killall  进程名称`杀死某个进程

##网络工具命令
####·ssh
1.连接到远程主机
格式：`ssh  +  主机名@主机ip`
2.远程运行shell命令
格式：`ssh  +  主机名@主机ip +  shell命令 `

####·wget
1.在命令行下的迅雷工具，用于下载。
格式：`wget + 资源地址`
2.断点续传
 `wget -c +资源地址`

####·scp
用于文件传输的命令。
1.上传
格式：`scp + 文件绝对路径 + 对应主机名@主机ip + 文件存放的绝对路径`
2.下载
格式：`scp  + 对应主机名@主机ip + 文件绝对路径+ 文件存放的绝对路径`

####·ping
1.测试网络连通性
`ping   www.baidu.com`
2.ping指定次数
`ping -c 5 www.baidu.com`    ping5次

##用户管理命令
####·sudo
以超级管理员的身份执行命令

####·useradd
需要使用特定参数来生成主目录，系统shell版本等。若不使用参数，则生成的账户无密码，我shell版本。
`sudo useradd -d "home/zero" -m -s "bin/bash" zero`这里zero是主机名
`-d "home/zero"`是指定这个为根目录
`-m`如果目录不存在就强制创建
`-s`指定shell版本

####·adduser
自动为创建的用户生成主目录，系统shell版本等，会在创建时输入用户密码。
`adduser user`即可

####·userdelete
删除用户
`userdelete -r user`

####·passwd
更改密码
`passwd zero`更改zero账户的密码

####·groupadd
1.`groupadd leader`增加一个新组

2.`cat /etc/group | grep leader`查询组

####·groupmod
1.`groupmod -n leaders leader`更改组名，从leader改为leaders

2.`groupmod -g 3000 leaders`更改组GID，改为3000

####·groupdel
`groupdel leaders`删除用户组

