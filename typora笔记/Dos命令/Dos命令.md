常见Dos命令

`ipconfig`查看ip地址

`ping`测试网络是否流畅
	`ping www.baidu.com`
	`ping 192.168.1.1`

`cd`切换目录
	`cd 123`切换到`123`文件夹下
	`cd ..`切换到当前目录的上一个目录
	`cd + 绝对路径`直接切换到那个目录
		`cd C:\windows\system32` 直接切换到`C:\windows\system32`目录	

`dir`列出目录下所有文件
	`dir /ON` O 是英文单词 order（顺序）的首字母，而 N 则是英文单词 name（名称）的首字母。==> 按文件名的字母顺序显示文件 
	`dir /A`显示所有文件/文件夹，包括隐藏文件
	`dir /OS`按大小排序
	`dir /s`列出当前目录以及子目录下的所有文件 

`tree`按树形展示目录，跟上面的dir差不多

`mkdir/md`创建文件夹
	`mkdir 123`建一个名为123的文件夹
	`mkdir test1\test2`在当前文件夹下建一个test1文件夹，在test1中又建了一个test2文件夹

`rd/rmdir`删除空文件夹
	`rd test`若test文件夹为空，则删除
	`rd /s test`删除test文件夹
	`rd /s /q test`强制删除test文件夹，不询问

`del`删除文件
	`del 1.txt`删除1.txt
	`del test`删除test文件夹下所有的文件（保留文件夹，只删文件）

`copy`复制文件
	`copy 1.txt 2.txt`将1.txt复制一份，命名为2.txt
	`copy 1.txt 123`将1.txt复制到123文件夹去
	`copy 1.txt C:\windows\system32`将1.txt复制到`C:\windows\system32`去，这里使用绝对路径。

`move`移动文件，相当于剪切，可以当重命名用。
	`move 1.txt 123`将1.txt文件移动到123文件夹中
	`move 1.txt 123/2.txt`将1.txt剪切到123文件夹中，命名为2.txt
	`move 1.txt 2.txt`将1.txt重命名为2.txt，过程可以理解为将1.txt剪切到当前文件夹并命名为2.txt

`ren`重命名
	`ren 1.txt 2.txt`将1.txt重命名为2.txt
	`ren *.jpg  *.png`将所有jpg结尾的文件改为png结尾

`tpye`显示文件内容，即打开文件
	`type 1.txt`打开1.txt

`echo`在cmd下打印文件
	`echo Hello World!`输出`Hello World!`
	`echo Hello World! > 1.txt`将内容以覆盖的形式写入1.txt
	`echo Hello World! >> 1.txt`将内容以追加的形式写入1.txt

`copy con +文件名`写文件，以Ctrl+Z结束
	`copy con 1.txt`
		`Hello World!`
		`Crrl +Z`将以上内容输入到1.txt中

`attrib`隐藏文件夹
	`attrib +h test`隐藏test文件夹
	`attrib -h test`去掉隐藏属性
	`attrib +h +s test`  +s:提供系统保护

`cls`清屏

`shutdown`重启/关机/
	`shutdown -s`关机
	`shutdown -l`注销
	`shutdown -r`重启
	`shutdown -t 10`10秒后进行操作，时间可以改
		`shutdown -s -t 10`10秒后关机
		`shutdown -r -t 10`10秒后重启
	`shutdown -c "消息内容"`关机时显示消息内容（一般来说中文会乱码）

`systeminfo`显示系统相关信息

Dos常用命令差不多就辣么多，其他想知道的直接百度。

------

利用Dos命令完成以下练习：
1.查看一下自己的ip
2.ping一下隔壁的ip，ping一下百度、优酷等网站（只要接着同一个WiFi就可以互相ping通）
3.在桌面新建一个test文件夹，在里面创建test1、test2文件夹。
4.在test1文件夹中，创建一个1.txt文件，内容是`Hello World!`
5.创建一个2.txt文件，内容是三行的`Hello World!`
6.将2.txt复制一份成3.txt
7.将3.txt复制到test目录下（即test1的上一个目录）
8.将3.txt剪切到test2目录下，并重命名为4.txt
9.查看4.txt的内容
10.切换到test目录，将test2文件夹隐藏并给与系统保护。
11.切换至test2目录，分别利用`dir`和`dir /a`查看test2目录下的文件和文件夹，比较有啥区别
12.清屏
13.利用`systeminfo`查看系统版本信息
练习不检查，有问题提问即可。

