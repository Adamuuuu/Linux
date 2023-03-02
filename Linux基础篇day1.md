### Linux的历史

linux 是芬兰人 Torvalds 开发的。

Torvalds 在大学期间，感觉Unix 满足不了它使用计算机的需求，于是想要开发出一套新的操作系统，通过学习Unix的相关知识外加参考minix的设计理念和程序代码，最终开发出了Linux的内核。随后放在了 ftp 网站上，供更多的人使用， 因为他想更多的人提供建议与一起来开发这个内核。

#### TIP

为了能够让 linux 能兼容 unix 的软件，对 linux 进行了修改，开始参考 POSIX

TIP

POSIX 是可携式操作系统接口（Portable Operating System Interface）的缩写， 重点在于规范内核与应用程序之间的接口，这是由美国电气与电子工程师学会（IEEE）所发布的一项标准

POSIX 标准主要是针对 UNIX 与一些软件运行时的标准规范，所以按照这个规范来支持， 就能让 unix 上的软件在 linux 上运行，所以导致 linux 使用率大增

#### 特色

- 自由开发的学习和使用环境
- 配置需求低廉
- 内核功能强大，由于他是开源的，所有有很多团体或个人投入开发
- 独立作业，很多软件套件都可以在Linux中运行

#### 优点

- 稳定的系统

  基于 UNIX 的概念开发出来的操作系统，继承了 UNIX 稳定并且有效率的特点， 安装 Linux 的主机连续运行一年以上不曾宕机、不必关机是很平常的事情

- 免费或少许费用

- 安全性、漏洞的快速修补：开源的力量

- 多任务、多用户

  与 windows 不同，Linux 主机开源同时允许多人上线来工作，并且资源分配较为公平， 比起 windows 的单人多任务系统要稳定的多！这种多用户、多任务可是 UNIX Like 上面相当好的一个功能， 怎么说呢？你可以在一部 Linux 主机上面规划处不同等级的用户，而且每个用户登录系统时的工作环境都可以不相同， 此外，还可以允许不同的用户在同一时间登录主机，以同时使用主机的资源

- 用户与用户组的规划

  在 Linux 的机器中，文件的属性可以分为

  - 可读
  - 可写
  - 可执行

  等参数来定义一个文件的适用性，此外，这些属性还可以分为三个种类

  - 文件拥有者
  - 文件所属用户组
  - 其他非拥有者与用户组者

  这对于项目或其他项目开发者具有相当良好的系统保密性

- 相对比较不耗资源的系统：总之就是硬件需求低，可以服务多人使用

#### 缺点

- 需要使用命令行的终端模式进行系统管理
- 没有特定的支持厂商
- 游戏支持度不足
- 专业软件支持度不足（大部分专业绘图软件不支持）

### 安装Linux

#### 安装前需要知道的概念

- **目录树**

Linux与Windows不同，在Windows上通常是c盘、d盘、e盘这种分区

但Linux是一种目录树的结构

![目录树](D:\Linux\我的博客\目录树.png)

所有文件都是由根目录「/」衍生而来的，上图长方形为目录，波浪形为文件，比如想要取得 mydata 那个文件时， 系统就得由根目录开始找，查找就形成了一条路径 `/home/dmtsai/mydata`

linux 系统使用的是目录树架构，但是我们文件数据其实是放置在磁盘分区槽当中的， 现在的问题是「如何结合目录树的架构与磁盘内的数据呢」？这个时候就需要用到「挂载（mount）」了

- **挂载**

**挂载** 就是利用一个目录当成进入点，将磁盘分区槽的数据放置在该目录下。 也就是说，进入该目录就可以读取该分区槽的意思，这个动作我们成为挂载。

由于整个 Linux 系统最重要的就是根目录，因此根目录一定需要挂载到某个分区槽的， 至于其他的目录则可依据用户自己的需求来挂载到不同的分区槽

![挂载](D:\Linux\我的博客\挂载.png)

- partition 1 挂载到根目录下
- partition 2 挂载到 /home 下

也就是说，当把数据放置在 /home 下时，是放在了 partition 2 上的，否则就是放在 partition 1 上的

#### 软件准备

- vmware:虚拟机

- xshell：在Windows里远程连接linux系统的工具

- xftp：在Windows和Linux系统之间传输文件

- CentOS映射文件:http://www.centos.org/download/

#### 安装使用

**进入VMware界面，新建虚拟机，使用默认选项安装**

- CPU 等级类别：本机的 CPU 类型

- 内存：提供大约 1~2G 的内存

- 硬盘：

  分配大约20G的空间

- 网络卡：使用 bridge（桥接）方式，同样使用 VirtI/O 的芯片。CentOS 本身有提供驱动程序

**在终端界面登录Linux**

![登陆界面](D:\Linux\我的博客\登陆界面.png)

**通过Xshell7连接虚拟机**

首先通过`ip add`的命令获取Linux的ip

![ip地址](D:\Linux\我的博客\ip地址.png)

然后进入Xshell7界面，选择新建用户，按照要求输入ip地址以及用户名和密码即可连接成功。

### 简单使用

#### 两大原则

- 一切皆文件
  - Linux中任何命令、操作都有对应的文件
- 沉默是金
  - 在Linux命令执行的过程中，没有消息就是好消息

首先明确几个重要概念

```bash
$ command [-options] parameter1 parameter2
  指令      选项        参数1       参数2
 
        Copied!
    
```

- command：指令（command）或 可执行文件（如批次脚本 script）
- command：是指令名称，例如变换工作目录的指令是 cd 等
- 中括号是可选配置参数
  - `-` 一个短横线，如 -h，这是选项的简写
  - `--` 两个短横线，是选项的完整名称，如 --help
- 指令、选项、参数等中间以空格来区分，不论空几格 shell 都视为一格，所以空格是很重要的特殊字符
- 按下 enter 按键后，就代表一行指令的开始启动
- 严格区分英文大小写

#### 基础指令的使用

##### ls  [-l]
查看文件夹列表（查看更多信息）

ll  是ls -l的别名

-r ：将目录的内容清单以英文字母顺序的逆序显示

-t ：按文件的修改时间进行排序

```sh
[root@localhost lianxi]# ls -l
总用量 24
-rw-r--r--. 1 root root 181 2月  23 16:27 buckup.sh
-rw-r--r--. 1 root root 147 2月  19 15:12 create_file.sh
-rw-r--r--. 1 root root 207 2月  20 20:45 create_user.sh
drwxr-xr-x. 2 root root  21 2月  21 16:30 function
-rw-r--r--. 1 root root 180 2月  23 20:55 monitor_crond.sh
drwxr-xr-x. 3 root root  18 2月  18 19:15 sanchuang
-rw-r--r--. 1 root root   4 2月  20 19:52 test.txt
-rw-r--r--. 1 root root 590 2月  20 20:45 user_pwd.txt
```

```sh
-rw-r--r--. 1 root root 181 2月  23 16:27 buckup.sh
```

对于输出的文件信息，具体解释如下

- r代表读权限   w代表写权限  x代表执行权限

- `-rw-r--r--`  开头的`-`代表文件类型为普通文件，往后每三个为一组，第一组代表文件拥有者对该文件的权限，第二组代表文件所属用户组对该文件的权限，第三组代表其他非拥有者与用户组者对该文件的权限。

##### mkdir 

  新建文件夹，可以同时建立多个文件

  ```sh
  [root@localhost demo]# mkdir test
  [root@localhost demo]# ls
  test
  [root@localhost demo]# mkdir test1 test2
  [root@localhost demo]# ls
  test  test1  test2
  ```

  ##### cd

  切换目录 cd .. 返回上一级

  ```sh
  [root@localhost demo]# cd ..
  [root@localhost lianxi]# cd demo
  [root@localhost demo]# 
  
  ```

  ##### pwd

  查看当前目录

  ```sh
  [root@localhost demo]# pwd
  /lianxi/demo
  ```

  ##### touch

  新建一个文件或多个文件

  ```sh
  [root@localhost demo]# touch test.txt
  [root@localhost demo]# ls
  test.txt
  [root@localhost demo]# touch test{1..10}.txt
  [root@localhost demo]# ls
  test10.txt  test2.txt  test4.txt  test6.txt  test8.txt  test.txt
  test1.txt   test3.txt  test5.txt  test7.txt  test9.txt
  [root@localhost demo]# 
  
  ```

#####  rm 

  删除命令

  - rm -r 递归删除   文件夹中的子文件夹也会删除
  
  - rm -f 强制删除  不给予提醒
  
  - rm -rf *  删除文件夹中所有文件   但不包括隐藏文件
  
  - rm -rf  .*删除文件夹中的隐藏文件

  ```sh
  [root@localhost demo]# rm -rf *
  [root@localhost demo]# ls
  [root@localhost demo]# 
  ```

##### env

  查看环境变量

  ```sh
  MAIL=/var/spool/mail/root
  PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
  PWD=/lianxi/demo
  LANG=zh_CN.UTF-8
  SELINUX_LEVEL_REQUESTED=
  HISTCONTROL=ignoredups
  SHLVL=1
  HOME=/root
  LOGNAME=root
  SSH_CONNECTION=192.168.220.1 6180 192.168.220.129 22
  LESSOPEN=||/usr/bin/lesspipe.sh %s
  XDG_RUNTIME_DIR=/run/user/0
  _=/usr/bin/env
  
  ```

  

##### ps aux

  查看进程信息

  ```sh
  [root@localhost demo]# ps aux
  USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
  root          1  0.0  0.3 128020  6648 ?        Ss   21:40   0:00 /usr/lib/
  root          2  0.0  0.0      0     0 ?        S    21:40   0:00 [kthreadd
  root          4  0.0  0.0      0     0 ?        S<   21:40   0:00 [kworker/
  ```

  #### 常用快捷键

table：自动补全文件名，补齐命令

ctrl+c：终止当前进程

ctrl+l：清屏

top：显示进程

#### 获取帮助

这么多的指令，死记硬背肯定是不行的，由于 Linux 上大多数都是自由软件，因此开发者一般都会提供 文档等方式让你了解这些指令的用法

##### 指令的 --help 求助说明

  命令  --help

```sh

[root@localhost /]# mkdir --help
用法：mkdir [选项]... 目录...
Create the DIRECTORY(ies), if they do not already exist.

Mandatory arguments to long options are mandatory for short options too.
  -m, --mode=MODE   set file mode (as in chmod), not a=rwx - umask
  -p, --parents     no error if existing, make parent directories as needed
  -v, --verbose     print a message for each created directory
  -Z                   set SELinux security context of each created directory
                         to the default type
      --context[=CTX]  like -Z, or if CTX is specified then set the SELinux
                         or SMACK security context to CTX
      --help		显示此帮助信息并退出
      --version		显示版本信息并退出

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
请向<http://translationproject.org/team/zh_CN.html> 报告mkdir 的翻译错误
要获取完整文档，请运行：info coreutils 'mkdir invocation'

```



  ##### man命令

如果是从来没有用过的指令， 或则要查询的根本就不是指令，而是文件的「格式」时，就需要通过 man page 了。

比如

```sh
DATE(1)                       User Commands                       DATE(1)

NAME
       date - print or set the system date and time

SYNOPSIS
       date [OPTION]... [+FORMAT]
       date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

DESCRIPTION
       Display  the  current  time in the given FORMAT, or set the system
       date.

       Mandatory arguments  to  long  options  are  mandatory  for  short
       options too.

       -d, --date=STRING
              display time described by STRING, not 'now'

       -f, --file=DATEFILE
              like --date once for each line of DATEFILE

       -I[TIMESPEC], --iso-8601[=TIMESPEC]
              output  date/time  in ISO 8601 format.  TIMESPEC='date' for
              date only (the default), 'hours', 'minutes', 'seconds',  or
              'ns' for date and time to the indicated precision.

       -r, --reference=FILE
              display the last modification time of FILE

       -R, --rfc-2822
              output  date and time in RFC 2822 format.  Example: Mon, 07
              Aug 2006 12:34:56 -0600

       --rfc-3339=TIMESPEC
              output date and time in RFC 3339 format.   TIMESPEC='date',
              'seconds',  or 'ns' for date and time to the indicated pre‐
              cision.  Date and time components are separated by a single
              space: 2006-08-07 12:34:56-06:00

       -s, --set=STRING
              set time described by STRING

       -u, --utc, --universal
              print or set Coordinated Universal Time (UTC)

       --help display this help and exit

```



  **下表总结一些常用按键**

| 按键      | 进行工作                                                     |
| --------- | ------------------------------------------------------------ |
| 空格键    | 向下翻页                                                     |
| Page Down | 向下翻页                                                     |
| Page Up   | 向上翻页                                                     |
| home      | 去第一页                                                     |
| end       | 去到最后一页                                                 |
| /string   | 向下搜寻 string 这个字符串，如果要搜索 vbird 就输入 /vbird   |
| ?string   | 向上搜寻 string                                              |
| n,N       | 利用 / 或 ？来搜寻字符串时，可以用 n 来继续下一个搜寻，N 上一个 |
| q         | 结束这次的 man page                                          |

  

man page 搜索的不是在线的（前面书上说是在线求助），提供 man page 的数据通常放在 `/usr/share/man` 目录的。

### 目录与文件

#### 绝对路径与相对路径

- 绝对路径：由根目录开头，如 /home/mrcode
- 相对路径：不是由根目录开头的，如 ./mrcode
- 以下的特殊目录需要着重了掌握
  - `.`：代表此层目录
  - `..`：上一层目录
  - `-`：前一个工作目录
  - `~`：目前用户身份坐在的家目录
  - `~account`：表示 account 这个用户的家目录（account 是个账户名称）

#### 目录相关指令

##### mkdir 

  新建文件夹，可以同时建立多个文件

  ```sh
[root@localhost demo]# mkdir test
[root@localhost demo]# ls
test
[root@localhost demo]# mkdir test1 test2
[root@localhost demo]# ls
test  test1  test2
  ```

  ##### cd

  切换目录 cd .. 返回上一级

  ```sh
[root@localhost demo]# cd ..
[root@localhost lianxi]# cd demo
[root@localhost demo]# 

  ```

  ##### pwd

  查看当前目录

  ```sh
[root@localhost demo]# pwd

/lianxi/demo
  ```

  ##### ls

  查看当前目录选项与参数：

- **a**：全部的文件，连同隐藏文件（开头为 .）一起列出来（常用）
- A：全部的文件，连同隐藏文件（不包括 . 和 .. 这两个目录)
- **d**：仅列出目录本身，而不是列出目录内的文件数据（常用）
- f：直接列出结果，而不进行排序（ls 默认以文档名排序）
- F：根据文件、目录等信息，给予附加数据结构
- h：将文件容量以人类较易读的方式（例如 GB、KB）列出来
- i：列出 inode 号码，inode 的意义后续讲解
- **l**：长数据串输出，包含文件的属性与权限等数据（常用）
- n：列出 UID 与 GID 而非使用者与群组的名称（UID 与 GID 会在账户管理中讲解）
- r：将排序结果反向输出，例如原本文件名由小到大，反向则由大到小



  ```sh
#查看全部文件 连同隐藏文件
[root@localhost lianxi]# ls -a
.          create_file.sh  function          test.txt
..         create_user.sh  monitor_crond.sh  user_pwd.txt
buckup.sh  demo            sanchuang
#查看全部文件  不包括 . 和 .. 这两个目录
[root@localhost lianxi]# ls -A
buckup.sh       create_user.sh  function          sanchuang  user_pwd.txt
create_file.sh  demo            monitor_crond.sh  test.txt
#仅列出目录本身，而不是列出目录内的文件数据
[root@localhost lianxi]# ls -d
.
#直接列出结果，而不进行排序
[root@localhost lianxi]# ls -f
.               buckup.sh         sanchuang       user_pwd.txt
..              monitor_crond.sh  create_file.sh  function
create_user.sh  demo              test.txt
将文件容量以人类较易读的方式（例如 GB、KB）列出来
[root@localhost lianxi]# ls -h
buckup.sh       create_user.sh  function          sanchuang  user_pwd.txt
create_file.sh  demo            monitor_crond.sh  test.txt
#长数据串输出，包含文件的属性与权限等数据（常用）
[root@localhost lianxi]# ls -l
总用量 24
-rw-r--r--. 1 root root 181 2月  23 16:27 buckup.sh
-rw-r--r--. 1 root root 147 2月  19 15:12 create_file.sh
-rw-r--r--. 1 root root 207 2月  20 20:45 create_user.sh
drwxr-xr-x. 3 root root  50 2月  24 23:47 demo
drwxr-xr-x. 2 root root  21 2月  21 16:30 function
-rw-r--r--. 1 root root 180 2月  23 20:55 monitor_crond.sh
drwxr-xr-x. 3 root root  18 2月  18 19:15 sanchuang
-rw-r--r--. 1 root root   4 2月  20 19:52 test.txt
-rw-r--r--. 1 root root 590 2月  20 20:45 user_pwd.txt
#列出 UID 与 GID 而非使用者与群组的名称
[root@localhost lianxi]# ls -n
总用量 24
-rw-r--r--. 1 0 0 181 2月  23 16:27 buckup.sh
-rw-r--r--. 1 0 0 147 2月  19 15:12 create_file.sh
-rw-r--r--. 1 0 0 207 2月  20 20:45 create_user.sh
drwxr-xr-x. 3 0 0  50 2月  24 23:47 demo
drwxr-xr-x. 2 0 0  21 2月  21 16:30 function
-rw-r--r--. 1 0 0 180 2月  23 20:55 monitor_crond.sh
drwxr-xr-x. 3 0 0  18 2月  18 19:15 sanchuang
-rw-r--r--. 1 0 0   4 2月  20 19:52 test.txt
-rw-r--r--. 1 0 0 590 2月  20 20:45 user_pwd.txt
[root@localhost lianxi]# 

  ```

##### cp

复制文件或者目录

```bash
cp [-adfilprsu] 来源文件（source）目标文件（destination）
```

- **a**：相当于 -dr --preserve=all 的一是一，至于 dr 请参考下列说明；（常用）
- d：若来源文件为链接文件的属性（link file），则复制链接文件属性而非文件本身
- f：强制（force）的意思，若目标文件已经存在且无法开启，则移除后再尝试一次
- **i**：若目标文件已经存在时，在覆盖时会先询问动作的进行。（常用）
- l：进行硬式链接（hard link）的链接档的建立，而非复制文件本身
- **p**：连同文件的属性（权限、用户、时间）一起复制过去，而非使用默认属性；（备份文件常用）
- **r**：递归持续复制，用于目录的复制行为。（常用）

```sh
#复制文件
[root@localhost china3]# cp lili.txt hunan
[root@localhost china3]# ls hunan
lili.txt
[root@localhost china3]# ls
boot  hunan  lili.txt  passwd

[root@localhost china3]# cp  /etc/passwd hunan
[root@localhost china3]# ls hunan
lili.txt  passwd

#复制文件并重命名
[root@localhost china3]# cp lili.txt hunan/ll.txt
[root@localhost china3]# ls hunan
lili.txt  ll.txt  passwd

#复制多个文件
[root@localhost china4]# cp dengchao*.txt deng

#复制文件夹
[root@localhost china4]# cp deng yueyang -r

#复制多个文件夹  中间用空格隔开
[root@localhost china4]# cp deng yueyang hunan -r

```

##### mv

移动或者重命名，当后面接的文件存在就是移动

可移动一个文件，也可以移动多个文件

- f：强制，如果目标文件已经存在，不会询问，直接覆盖
- i：若目标文件已经存在时，就会询问是否覆盖
- u：若目标已经存在，且 source 比较新，才会功更新该文件

```sh
[root@study tmp]# cd /tmp/   
[root@study tmp]# cp ~/.bashrc bashrc
# 创建目录
[root@study tmp]# mkdir test
# 将刚刚拷贝的 bashrc 复制到目录中
[root@study tmp]# mv bashrc test/
# 目录更名
# 其实还有一个指令 rename，该指令专职进行多个文档名同时更名，并非针对单一文件更名
# 与 mv 不同，详细请 man rename
[root@study tmp]# mv test/ test2


```

#####  rm 

  删除命令

  - rm -r 递归删除   文件夹中的子文件夹也会删除

  - rm -f 强制删除  不给予提醒

  - rm -rf *  删除文件夹中所有文件   但不包括隐藏文件

  - rm -rf  .*删除文件夹中的隐藏文件

  ```sh
[root@localhost demo]# rm -rf *
[root@localhost demo]# ls
[root@localhost demo]# 
  ```

##### 回收站实例

编写一个程序（脚本）   实现回收站功能

1. 临时存放数据
2. 记录了当时文件的路径  方便恢复  记录当时的路径到一个文件中 ，在恢复的时候查询使用

具体步骤

1. 首先编写一个脚本mv_back.sh   在脚本新建一个回收站文件夹

/backup   让后通过mv与位置变量将输入的文件或者文件夹移动到/backup文件夹中

```shell
#!/bin/bash
#新建回收站目录
mkdir -p /backup

mv  $1 /backup
[root@localhost china3]# 

```

2. 为脚本文件添加可执行权限

   ```
   [root@localhost china3]# chmod +x mv_back.sh
   ```

3. 复制脚本文件到环境变量中

   ```
   [root@localhost china3]# cp mv_back.sh /usr/bin
   ```

4. 修改rm的别名

   ```
   [root@localhost china3]# alias rm='mv_back.sh'
   ```

   

#### 文件相关指令

##### cat

直接查阅一个文件的内容可以使用 cat

- A：相当于 -vET 的整合选项，可列出一些特殊字符而不是空白
- b：列出行号，仅针对非空白行做行号显示，空白行不标行号
- E：将结尾的断行字符 $ 显示出来
- n：打印出行号（包含空白行）
- T：将 tab 按键以 ^I 显示出来
- v：列出一些看不出来的特殊字符

```sh
#比较常用的就是如下两个
[root@localhost china3]# cat post_var.sh 
#!/bin/bash

echo "第一个位置变量是$1"
echo "第二个位置变量是$2"
echo "第三个位置变量是$3"
[root@localhost china3]# cat -n post_var.sh 
     1	#!/bin/bash
     2	
     3	echo "第一个位置变量是$1"
     4	echo "第二个位置变量是$2"
     5	echo "第三个位置变量是$3"

```

##### more与less

虽然more与less同cat一样可以显示文件内容，但是这两种命令都是可以翻页使用的

more

```sh
[root@localhost china3]# more /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
games:x:12:100:games:/usr/games:/sbin/nologin
ftp:x:14:50:FTP User:/var/ftp:/sbin/nologin
nobody:x:99:99:Nobody:/:/sbin/nologin
systemd-network:x:192:192:systemd Network Management:/:/sbin/nologin
dbus:x:81:81:System message bus:/:/sbin/nologin
polkitd:x:999:998:User for polkitd:/:/sbin/nologin
sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin
postfix:x:89:89::/var/spool/postfix:/sbin/nologin
chrony:x:998:996::/var/lib/chrony:/sbin/nologin
huangjiu:x:1000:1000::/home/huangjiu:/bin/bash
liqiang:x:1001:1001::/home/liqiang:/bin/bash
chenlin:x:7788:1002:sanchuang student:/home/yueyang:/sbin/nologin
liyili:x:7789:7789::/home/liyili:/bin/bash
user20:x:7790:7790::/home/user20:/bin/bash
user00:x:7791:7791::/home/user00:/bin/bash
user01:x:7792:7792::/home/user01:/bin/bash
user02:x:7793:7793::/home/user02:/bin/bash
user03:x:7794:7794::/home/user03:/bin/bash
--More--(52%)    #重点是这里   展示了当前显示了文件的多少内容
```

**在 more 程序中，有几个按键可以按：**

- 空格键（space）：向下翻一页
- Enter：向下翻一行
- `/字符串`：在显示的内容中，向下搜索「字符串」这个关键词
- q：立即离开 more
- b 或 ctrl+b：向前翻页，只针对文件有用，对管线（管道 |）无用



**less同more大致相同，但是more在输出完之后会直接退出文件，但less不会**

可以使用的按键和指令有

- 空格键：向下翻一页
- pagedown：向下翻一页
- pageup：向上翻一页
- `/字符串`：向下搜索字符串；注意这个斜杠也是需要输入的，不是在 「:」输入，：也和这个是一个功能
- `?字符串`：向上搜索字符串
- n：重复前一个搜索（与 / 或 ？有关）
- N：反向的重复前一个搜索
- g：前进到这个资料的第一行
- G：前进到这个资料的最后一行去（注意是大写）
- q：离开 less 这个程序

##### head 取出文件前几行内容

```sh
head [-n number] 文件

-n：后面接数字，表示摘取几行

```



```sh
#默认取出的是十行内容
[root@localhost china3]# head /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
sync:x:5:0:sync:/sbin:/bin/sync
shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
halt:x:7:0:halt:/sbin:/sbin/halt
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
#可以通过添加选项修改取出的行数
[root@localhost china3]# head -5 /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
```

#####  tail 取出后面几行

```sh
tail [-nf number] 文件

-n ：后面接数字，表示显示几行
-f ：表示持续侦测后面所接的档名，要等到按下 ctrl+c 才会结束 tail 的侦测
```

**两者可以组合使用**

例如想要取文件的第5到10行

```sh
[root@localhost china3]# head /china3/test.txt |tail -5
这是第6行
这是第7行
这是第8行
这是第9行
这是第10行
```

想要取到第8行

```sh
[root@localhost china3]# head -8 /china3/test.txt |tail -1
这是第8行
```

`|`：管线/管道符，前面的指令所输出的信息，请透过管线交由后续的指令继续使用。后续会详细讲解

##### cat 和more、less的对比

当读取大文件，我们通常会使用more与less，这是因为cat读取文件的时候是一次性全部读取，会消耗比较多的内存与CPU，但是more与less是慢慢读取，不消耗很多的内存和cpu

##### touch

修改文件时间或新建文件

 新建一个文件或多个文件

  ```sh
[root@localhost demo]# touch test.txt
[root@localhost demo]# ls
test.txt
[root@localhost demo]# touch test{1..10}.txt
[root@localhost demo]# ls
test10.txt  test2.txt  test4.txt  test6.txt  test8.txt  test.txt
test1.txt   test3.txt  test5.txt  test7.txt  test9.txt
[root@localhost demo]# 

  ```

##### du

统计目录及文件的空间占有情况

du 选项  目录和或文件名

- a  统计时包括所有的文件

- h 以更易读的字节单位（K，M）等显示信息

- s 只统计每个参数所占用空间的总大小



```sh
[root@localhost demo1]# du -a
4	./test1.sh
4	./test.sh.gz
8	.
[root@localhost demo1]# du -h
8.0K	.
[root@localhost demo1]# du -h test1.sh 
4.0K	test1.sh
[root@localhost demo1]# du -s test1.sh 
4	test1.sh
```

##### local

locate 可以查找文件，并同时查看他们的文件权限

```bash
[mrcode@study kernel]$ locate crontab
/etc/anacrontab
/etc/crontab
/usr/bin/crontab
/usr/share/doc/man-pages-overrides-7.7.3/crontabs
/usr/share/doc/man-pages-overrides-7.7.3/crontabs/COPYING
/usr/share/man/man1/crontab.1.gz
/usr/share/man/man1p/crontab.1p.gz
/usr/share/man/man4/crontabs.4.gz
/usr/share/man/man5/anacrontab.5.gz
/usr/share/man/man5/crontab.5.gz
/usr/share/vim/vim74/syntax/crontab.vim
```

#### 指令与文件的搜集

`which`  查看命令的位置

```sh
which [-a] command

-a：将所有 PATH 目录中可以找到的指令均累出，而不止第一个被找到的指令名称

```

`whereis`  查看命令位置以及man手册的位置

```sh
whereis [-bmsu] 文件或目录名
```

```sh
[root@localhost china3]# which ls
alias ls='ls --color=auto'
	/usr/bin/ls
[root@localhost china3]# whereis ls
ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz
[root@localhost china3]# 
```

**他们本质上是从PATH环境变量中的目录来查找的，并且只能找出执行文件**

另一个比较重要的命令就是`find`了

##### find

```sh
find [path] [option] [action]

```

与时间有关的参数有 -atime、-ctime、-mtime，以 -mtime 说明：

- mtime n：在 n 天前的「一天之内」被修改过内容的文件
- mtime +n：列出在 n 天之前（不含 n 本身）被修改过内容的文件
- mtime -n：列出在 n 天之内（含 n 天本身）被修改过内容的文件
- newer file：file 为一个存在的文件，列出比 file 还要新的文件

实践练习

```sh
# 将过去系统上 24 小时内有更动过内容（mtime）的文件列出
find / -mtime 0
# 0 表示当前时间，也就是当前时间开始往前 24 小时，也就是 24 小时内被修改过的文件

# 3 天前，24 小时内，如下
find / -mtime 3

# 寻找 /etc 下的文件，如果文件日期比 /etc/passwd 新旧列出
find /etc -newer /etc/passwd

# 列出 4 天内被更动多的文件
find / -mtime -4

```

- name filename：查找文件名为 filename 的文件

- size [-+]SIZE：查找比 SIZE 还要大（+）或则小（-）的文件

  SIZE 支持的单位有：

  - c：byte
  - k：1024 byte

  所以要查找 比 50 KB 还要大的文件，指令为 `find /home/ -size +50ks`

- type TYPE：查找文件类型为 TYPE 的。主要有

  - f：一般正规文件
  - b,c：装置文件
  - d：目录
  - l：连接
  - s：socket
  - p：FIFO

- exec command：command 为其他指令，-exec 后面可再接额外的指令来处理搜索到的结果

- perm mode：查找文件权限「刚好等于」mode 的文件，mode 为类似 chmod 的属性。

  例如：-rwsr-xr-x 的属性为 4755

- perm -mode：查找文件权限「必须要全部包括 mode 的权限」的文件

  例如：查找 -rwxr--r-- ，即 0744 的文件，使用 -perm -0744

- perm /mode：查找文件权限「包含任意 mode 的权限」的文件

  例如：-rwxr-xr-x，即 -perm /755 时，但一个属性属性为 -rw------ 也会被列出来， 因为他有 -rw 的属性存在

实践练习

```sh
# 找出文件名为 passwd 的文件
find / -name passwd

# 找出包含了 passwd 关键词的文件
find / -name "*passwd*"
#查找文件权限为7000的
find / -perm /7000
# 7000 就是 ---s--s--t
#将最近3小时内/lianxi 目录下文件大小大于10K的文件移动到/back目录下

find /lianxi -mmin +180 -type f -exec cp{} /find \;
```



### 关于执行文件路径的变量：`$PATH`

我们在前面说过，**Linux有两大原则：一切皆文件和沉默是金。**

**那么这些命令是否也有对应的文件呢？**

事实上确实是这样，我们可以通过`which` 命令来验证，这个命令是用来查找某个命令的绝对路径。

```sh
[root@localhost /]# which cd
/usr/bin/cd
[root@localhost /]# which pwd
/usr/bin/pwd
[root@localhost /]# which mkdir
/usr/bin/mkdir

```



通过以上结果我们可以看到像`cd` `pwd` `mkdir`这些命令都有与之相对应的文件。那我们在执行`cd` `pwd`  这些指令的时候 ，有没有考虑过一个问题：**为什么我们可以在任何地方执行这些命令？而不需要打出他的绝对路径呢？**

**这都是环境变量PATH在起作用**



**PATH是什么？：他决定了shell将到哪些目录中寻找命令或程序，PATH的值是一系列目录，当您运行一个程序时，Linux在这些目录下进行搜寻编译链接。**

可以输入`echo $PATH`查看当前环境变量,其中以分号隔开。

```sh
[root@localhost /]# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin
```



具体是如何运行的，我们可以通过自己添加一个环境变量来学习

#### 添加环境变量

- 1.直接在终端修改当前生效

`export PATH=$PATH:.`（其中export可不要，.是当前目录的意思，也可以自定义绝对路径）
配置完后可以通过`echo $PATH`查看配置结果。
生效方法：立即生效
有效期限：临时改变，只能在当前的终端窗口中有效，当前窗口关闭后就会恢复原有的path配置
用户局限：仅对当前用户

![PATH](D:\Linux\我的博客\PATH.png)

- 2.对用户生效
  因为写入到 .bash_profile 中的，而.bash_profile中是调用/.profile，所以可以直接在/.profile中定义变量



在home/用户/.profile中修改调用文件：vi ~/.bashrc
\#在最后一行添上
`export PATH=路径:$PATH`
生效方法：（有以下两种）
1、关闭当前终端窗口，重新打开一个新终端窗口就能生效
2、输入“source ~/.bashrc”命令，立即生效
使用 echo $PATH 看不到定义变量
有效期限：永久有效
用户局限：仅对当前用户



- 3.修改系统级

vi /etc/profile/profile

```
export PATH=$PATH:路径
```

保存文件，重启即可（有的系统执行./profile即可，不需重启；有的系统必须重启）
重启后可查看PATH环境变量看是否更改：
`echo $PATH`

### 文件的压缩与备份

首先提出一个问题：我们为什么需要打包压缩文件？

答：为了备份还原  有利于网络传输

但打包与压缩是两个过程，打包是将许多文件放到一起形成一个文件，也就是`归档文件`，而压缩则是减少占用磁盘的空间。

Windows文件中的哪些压缩文件是Linux也是可以打开的？

zip是两者都支持的

.rar 文件在Linux里默认是不能打开的  

#### 常见的压缩指令

- zip  压缩命令
  - zip passwd.zip passwd   压缩
  - unzip passwd.zip     解压缩

- gzip  

  - gzip passwd  压缩   
  - gunzip  passwd.gz    解压缩

- xzip xzip passwd  与gzip类似  但是压缩效果比gzip好   （压缩后占比更少）  但是压缩时间长

- bzip2 同gzip类似

linux 上常见的压缩指令是 gzip、bzip2 以及最新的 xz，还有支持 windows 的 zip，至于其他的压缩指令基本上都淘汰了。

##### gzip

```sh
gzip [-cdtv#] 文档名
zcat 文档名.gz
```

```sh
[root@localhost test]# gzip passwd
[root@localhost test]# ls
passwd.gz
[root@localhost test]# gunzip passwd.gz 
[root@localhost test]# ls
passwd
```

其余几条指令的使用方法与gzip大致相同，此处便不做赘述

##### tar

这种将多个文件或目录包成一个大文件的指令功能，就可以称呼为 **打包指令**，tar 就是这样一个功能的打包指令，同时还可以通过压缩指令将该文件进行压缩。

tar 的选项与参数非常多，这里只接受几个常用的选项

选项与参数

- c：建立打包文件，可搭配 `-v`来观察过程中被打包的文件名
- t：查看打包文件的内容含有哪些文件，重点在查看文件名
- x：接打包或解压缩的功能，可搭配 -C 在特定目录解开，特别注意 **c、t、x 不能同时出现在一起**
- z：通过 gzip 的支持进行压缩、解压缩；此时文件名最好为 `*.tar.gz`
- j：通过 bzip2 的支持进行压缩、解压缩；此时文件名最好为 `*.tar.bz2`
- J：通过 xz 的支持进行压缩、解压缩；此时文件名最好为 `*.tar.xz`
- v：在压缩、解压缩的过程中，将正在处理的文件名显示出来
- f：后面要立刻接要被处理的文件名，建议 -f 单独写一个选项（不容易忘记）
- C：在指定目录解压缩
- p：保留备份数据的原本权限与属性，常用语备份（-c）重要的配置文件
- P：保留绝对路径，保留 root 跟路径
- `--exclude=FILE`：在压缩过程中，排除指定的文件，不打包

最常用的是以下命令：

- 压 缩：`tar -cjf -v filename.tar.bz2 要被压缩的文件或目录`,后打包的压缩文件会覆盖原来的文件
  - tar -czf  -->.tar.gz
  - tar -cjf  -->.tar.bz2
  - tar -cJf  -->.tar.xz
- 查 询：`tar -tjf -v filename.tar.bz2`
- 解压缩：`tar -xjf -v filename.tar.bz2 -C 指定目录解开`

```sh
#压缩
[root@localhost demo]# tar -czf test.sh.gz test.sh
[root@localhost demo]# ls
demo1  test1.sh  test.sh  test.sh.bz2  test.sh.gz
#查看
[root@study ~]# tar -jtv -f /root/etc.tar.bz2
drwxr-xr-x root/root         0 2019-10-04 18:38 etc/
-rw-r--r-- root/root       808 2019-10-27 22:43 etc/fstab
-rw------- root/root         0 2019-10-04 18:20 etc/crypttab
lrwxrwxrwx root/root         0 2019-10-04 18:20 etc/mtab -> /proc/self/mounts
-rw-r--r-- root/root        51 2019-10-04 18:20 etc/resolv.conf
#解压
[root@localhost demo1]# tar -zx -f test.sh.gz -C /wh
[root@localhost demo1]# cd /wh
[root@localhost wh]# ls
test

```

格式化输出日期

- +%Y  year 年
- %m    月
- %d    天
- %H    小时
- %M    分
- %S    秒

```sh
ctime=$(date+%Y%m%d)

tar czf  bool-$ctime.tar.gz /bool

tar czf  bool-$(date+%Y%m%d).tar.gz /bool
```

##### 系统备份

在工作中经常需要备份的东西：日志文件

编写一个脚本  实现备份/var/log目录下的所有文件   要求文件名包含当天日期  精确到秒  同时删除七天前的备份文件   只保留最近七天的文件

```sh
#!/bin/bash
ctime=$(date +%Y%m%d%H%M%S)

mkdir -p /scbackup
tar czf /scbackup/${ctime}-log.tar.gz /var/log 2>/dev/null

find /scbackup -mtime +7 -name "*tar.gz" -exec rm -rf {} \;
```

#### 大文件处理

##### split 

可以分割文件，按文件大小或行数来分割

选项和参数：

- b  指定每个分割文件的大小

- d  指定分割文件的后缀为数字

- a  指定分割文件数字后缀的长度  如果是1  后缀为 0，1，2   如果是2 ，则是00，01，02.。。

- C   指定每行最大的字节数

- l   指定每个文件的最大行数

```sh
[root@localhost changsha]# ll -h
总用量 512M
-rw-r--r--. 1 root root  104 2月  27 15:55 bigfile.sh
-rw-r--r--. 1 root root 411M 2月  27 15:56 test.txt
[root@localhost changsha]# split -b 200M test.txt
[root@localhost changsha]# ll -h
总用量 923M
-rw-r--r--. 1 root root  104 2月  27 15:55 bigfile.sh
-rw-r--r--. 1 root root 411M 2月  27 15:56 test.txt
-rw-r--r--. 1 root root 200M 2月  27 16:00 xaa
-rw-r--r--. 1 root root 200M 2月  27 16:00 xab
-rw-r--r--. 1 root root  11M 2月  27 16:00 xac

```





### vim编辑器

在 LInux 的世界中，绝大部分的配置文件都是以 ASCII 的纯文本形态存在的，因此利用简单的文字编辑软件就可以修改配置了

基本上 vi 共分为三种模式：一般指令模式、编辑模式、指令列命令模式

- 一般指令模式（command mode）

  以 vi 打开一个文件就直接进入一般指令模式了（默认模式，也简称一般模式）。

  在该模式中，可以使用「上下左右」按键移动光标，可以使用「删除字符」或「删除整列」来处理文件内容，也可以使用「复制、粘贴」

- 编辑模式（insert mode）

  在一般模式中可以进行删除、复制、粘贴等动作，但是无法编辑文件内容。

  需要按下「i、I、o、O、a、A、r、R」等任意按键后才会进入编辑模式，通常会在左下方出现 INSERT 或 REPLACE 的字样，可以通过 esc 按键退出编辑模式，回到一般指令模式

- 指令列命令模式（commadn-line mode）

  在一般模式中，输入「:、/、?」任意字符，则光标会移动到最底下的一列。

  在这个模式中，可以提供你搜索、读取、存盘、大量取代字符、离开 vi、显示行号等功能、

### bash解释器

管理整个计算机硬件的其实是操作系统的核心（kernel），一般使用者只能通过 shell 来与核心沟通。bash具体都有哪些功能？那么有系统有多少 shell 可用呢？以及为什么要使用 bash？

#### bash 的功能主要有

- 命令编修能力
- 命令与文件补全功能
- 命令别名设置功能
- 工作控制、前景背景控制
- 程序化脚本
- 通配符

#### 什么是shell

操作系统其实是一组软件，控制整个硬件与管理系统的活动检测，如果这组软件能被用户随意的操作，若使用者应用不当，将会使得整个系统崩溃！所以不能随便被一些没有管理能力的终端用户随意使用

但是可以考虑使用程序来指挥核心，可以发现应用程序其实是在最外层，就如同鸡蛋的外壳一样，因此也就被称呼为壳程序（Shell）

其实壳程序的功能只是提供用户操作系统的一个接口，因此整个壳程序需要可以呼叫其他软件的功能，如前面提到过的很多指令，包括 man、chmod、chown、vi、fdisk、mkfs 等指令，这些指令都是独立的应用程序，但是可以通过壳程序（指令行模式）来操作这些应用程序



#### 为什么要学习shell呢

- 文字接口的 shell 在各大 distribution 都一样
- 远程管理时，文字接口速度较快
- shell 是管理 linux 系统非常重要的一环，因为 linux 内很多控制都是以 shell 撰写的

#### 设置别名

`alis`命令可以帮助我们给命令设置别名，方便我们更好的使用命令

可以通过`alis`来查看目前机器设置的别名

```sh
[root@localhost demo1]# alias
alias c='clear'
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'

```

也可以自己设置别名 和取消别名

```sh
# 这里使用 lm 取代了 ls -al
alias lm='ls -al'
#或者可以使用c代替clear
alias c=clear

#取消别名
[root@localhost demo1]# unalias c
[root@localhost demo1]# alias
alias cp='cp -i'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias mv='mv -i'
alias rm='rm -i'
alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'
```

#### 通配符

可以进行模糊匹配，比如可以想要知道 /usr/bin 下有多少以 X 开头的文件，使用`ls -l /usr/bin/X*` 就可以知道

*匹配任意字符

？匹配1个字符

举例

```sh
[root@localhost demo1]# ll /usr/bin/mkdir*
-rwxr-xr-x. 1 root root 79768 8月  20 2019 /usr/bin/mkdir

[root@localhost demo1]# ll /usr/bin/mkdi?
-rwxr-xr-x. 1 root root 79768 8月  20 2019 /usr/bin/mkdir
```

#### shell变量

**什么是变量？**

简单说，某一个特定字符串代表不固定的内容；比如：`y = ax+b` 等号左边的是变量，右边的是变量的内容，使用简单的变量来取代另一个比较复杂或则是容易变动的数据，这样做的好处就是方便！

##### 特殊符号

学习变量知识，我们首先要认识Linux中的特殊符号，特殊符号经常与变量等结合使用

**$符号**

- $?上一个命令的退出状态(若为0：表示成功；不是0，表示失败)，或者上一个函数的返回值，但是有两个注意点：函数一结束就取返回值；退出状态码必须是-0~255，否则就使用命令替换获取返回值或者定义一个变量（shell的文件级和函数中定义的变量默认都是全局变量）
- $#表示脚本中参数的个数
- $*表示获取所有对应参数的值
- $n表示为（n>=1）的参数
- $0表示脚本名
- $@表示获取所有对应参数的值
- $$ 表示Shell本身的PID（ProcessID）

**分号**

在脚本中，`分号`是多个语句之间的`分隔符号`，当只有一个语句的时候，`末尾无需分号`，最后一个语句后面也`无需分号`，否则报错
在交互式命令中，用分号隔开每个命令, 每个命令按照从左到右的顺序,顺序执行， 彼此之间不关心是否失败， 所有命令都会执行，例如：`command1 ; command2`

实际应用

```sh
#这是脚本

#/bin/bash

echo 这是脚本名字：$0
echo 总共有$#个人，分别是$*
echo 第一个人是$1,第二个人是$2
#脚本运行结果
[root@localhost demo1]# bash test1.sh 张三 李四
这是脚本名字：test1.sh
总共有2个人，分别是张三 李四
第一个人是张三,第二个人是李四

```



**引号**

单引号 是原始字符串，属于强引用，它会忽略所有被引起来的字符的特殊处理，被引用起来的字符会被原封不动的使用，唯一需要注意的点是不允许引用自身

双引号 可以对特殊字符进行扩展， 属于弱引用，它会对一些被引起来的字符进行特殊处理。双引号与单引号的区别在于其可以包含特殊字符（单引号直接输出内部字符串，不解析特殊字符；双引号内则会解析特殊字符），包括', ", $, \,如果要忽略特殊字符，就可以利用\来转义，忽略特殊字符，作为普通字符输出

具体效果可以看下面变量的取用章节





##### 变量的应用



- echo可以取出变量的值，通常有以下两种方式，推荐使用第2种方式

```sh
echo $PATH
echo ${PATH}			# 推荐使用这种方式取用

```

或者配合符号取用,比如使用单引号和双引号与echo配合就会有不同的结果

```sh

[root@localhost demo1]# a=10
#单引号
[root@localhost demo1]# echo '这是一个变量$a'
这是一个变量$a
#双引号
[root@localhost demo1]# echo "这是一个变量$a"
这是一个变量10
#不加引号
[root@localhost demo1]# echo 这是一个变量$a
这是一个变量10
#加大括号
[root@localhost demo1]# echo 这是一个变量${a}
这是一个变量10

```

通过以上结果我们可以发现，当echo配合单引号使用的时候，就是是什么就输出什么，不会取出其中变量的值，而使用双引号的时候则会取出变量的值

**命令替换**

另外还可以通过以下两种方式从命令中提取信息将其赋值给变量。

- 反引号字符（`）
- $()格式

`$( )` 和反引号``` (`tab`按键上面) 作用相同:命令替换

```sh
[root@localhost demo1]# echo $(date)
2023年 02月 25日 星期六 22:06:43 CST
[root@localhost demo1]# echo `date`
2023年 02月 25日 星期六 22:06:49 CST

```

**数值运算**

- `$(( )) `是整数数值运算，也可用`(( ))` 代替
- 另`$[ ]`也是进行数学运算的，在将一个数学运算结果赋给某个变量时，可以用美元符和方括号（`$[ operation ]`）将数学表达式围起来

```sh
[root@localhost demo1]# echo $((1+2))
3
[root@localhost demo1]# echo $[1+2]
3
```

**重定向**

| > 或 1>   | 把正确的进行输出(标准输出),覆盖 |
| --------- | ------------------------------- |
| >> 或 1>> | 把正确的进行输出(标准输出),追加 |
| 2>        | 把错误的进行输出,覆盖           |
| 2>>       | 把错误的进行输出,追加           |
| &>        | 合并正确和错误输出，覆盖重定向  |
| &>>       | 合并正确和错误输出，追加重定向  |

实际应用

```sh
#把正确的进行输出
[root@localhost demo1]# echo 12345 >test.txt
[root@localhost demo1]# cat test.txt
12345
[root@localhost demo1]# echo changsha >test.txt
[root@localhost demo1]# cat test.txt
changsha
[root@localhost demo1]# echo 12345 >>test.txt
[root@localhost demo1]# cat test.txt
changsha
12345
#把错误的进行输出

[root@localhost lianxi]# echo 123 2>test.txt
123
[root@localhost lianxi]# cat test.txt 
[root@localhost lianxi]# awdad 2>test.txt 
[root@localhost lianxi]# cat test.txt 
-bash: awdad: 未找到命令
[root@localhost lianxi]#  sdawaf >test.txt 
-bash: sdawaf: 未找到命令
#不论对错都进行输出
[root@localhost demo1]# echo 1234 &>>test.txt
[root@localhost demo1]# dasd &>>test.txt
[root@localhost demo1]# cat test.txt
0
1234
-bash: dasd: 未找到命令

```

**/dev/null 垃圾桶黑洞装置的特殊写法**

就是可以将任何信息吃掉的黑洞装置

```bash
[root@localhost demo1]# sadas 2>>/dev/null
[root@localhost demo1]# echo 12324 >/dev/null

#不论对错 都不会输出信息  常用来去除不必要的输出
 
```

**逻辑操作符**

- `&&`：前一个执行正确，后面才会执行
- `||`：前一个执行正确，后面的不会执行

此处就不做赘述了

####  历史命令：history

history 用来查询曾经下达过的指令

```sh
history [n]
history [-c]
history [-raw] histfiles
```

正常情况下历史命令的读取记录是这样的：

- 当以 bash 登录 Linux 主机后，系统会主动的由家目录的 `~/.bash_history` 读取
- 假设这次登录后，共下达过 100 次命令，等你注销时，系统就会将 101~1100 总共 1000 条记录**更新**到 `~/.bash_history` 中，因为和能存储最大条数 HISTSIZE 有关系，前面的序号会增加，但是总存储条数只有 HISTSIZE 条
- 也可以使用 history -w 强制写入

选项与参数：

- n：数字，列出最近 n 条命令
- c：将目前的 shell 中的所有 history 内容全部消除
- !:
  - !number  执行第几条历史命令
  - !command  执行最近一条的命令

```sh
[mrcode@study ~]$ history 4
  681  man rm
  682  alias
  683  man history
  684  history 4
[mrcode@study ~]$  !681		  # 执行第 681 条指令
 man rm			# 这里会显示具体执行的指令是什么
[mrcode@study ~]$ !!				# 执行上一个指令
 man rm
[mrcode@study ~]$ !al				# 从最新的历史指令开始搜索 al 开头的指令并执行他
alias
```

#### 命令执行过程



前面讲到过使用 alias 可以建立别名，比如创建了一个 ls 的别名，其实 ls 有少的指令，那么到底是哪一个会被选中执行呢？基本上，指令运行顺序可以这样看：

1. 以相对、绝对路径执行命令，例如 `/bin/ls` 或 `./ls`
2. 由 alias 找到该指令来执行
3. 由 bash 内置的指令来执行
4. 通过 $PATH 这个变量的顺序搜索到第一个指令执行

举例来说：

- `/bin/ls`：该指令运行后，没有颜色
- `ls`：该指令运行后输出的内容有颜色，因为是使用别名 `alias ls=‘ls --color=auto’`

##### bash环境配置文件

们一进入 bash 就取得了一堆有用的变量，这是因为系统有一些环境配置文件的存在，让 bash 在启动时直接读取这些配置文件，以规划好 bash 的操作环境。而这些配置文件分为全局系统配置和用户个人偏好配置



###  login 与 non-login shell

在介绍 bash 的配置文件前，一定要先知道 login shell 与 non-login shell ，重点就在于有没有登录（login）

- login shell：取得 bash 时需要完整的登录流程，就称为 login shell

  举例来说，你要由 tty1~tty6 登录，需要输入用户的账户与密码，此时取得的 bash 就称为「login shell」

- non-login shell：取得 bash 接口的方法不需要重复登录的举动

  比如：你以 x window 登录 linux 后，再以 X 的图形化接口启动终端机，此时该终端机并没有再次输入账户与密码，那么该 bash 的环境就称为 non-login shell

  再比如：你再原本的 bash 环境下再次下达 bash 这个指令，同样也没有输入账户密码，那第二个 bash（子程序）也是 non-login shell

上面两种情况取得的 bash 配置文件不一致。由于我们需要登录系统，所以先谈谈 login shell 会读取哪些配置文件？一般来说，login shell 其实只会读取这两个配置文件

1. /etc/profile：系统整体配置，最好不要修改这个文件
2. `~/.bash_profile` 或 `~/.bash_login` 或 `~/.profile`：属于使用者个人设置

![bash配置文件](D:\Linux\我的博客\bash配置文件.jpg)



#### 管线文件

bash 命令执行的时候有输出数据，如果这群数据必须经过几道手续之后才能得到我们想要的格式，这就可以使用管线命令（pipe）来完成了

值得注意的是，管线命令只会每个管线后面第一个必须是指令，而且这个指令必须能接受standard input的数据才可以，比如 less、more、head、tail 等都是可以接受 standard input 的管线命令。而 ls、cp、mv 等就不是管线命令了，因为他们不会接受来自 stdin 的数据。

管线命令主要有两个比较需要注意的地方：

- 管线命令仅会处理 standard output ，对于 standard error output 会忽略
- 管线命令必须要能接受来自前一个指令的数据成为 standard input 继续处理才行

```sh
[root@localhost demo1]# ll /etc |less
```

执行以上命令的时候，`ll`输出的内容就会被less读取，然后利用less可以实现翻页阅读的功能

````sh
#这是前面我们学习head和tail时候指令，head输出的内容被作为tail读入的内容  然后截取后五条信息
例如想要取文件的第5到10行
[root@localhost china3]# head /china3/test.txt |tail -5
这是第6行
这是第7行
这是第8行
这是第9行
这是第10行
```
````

##### grep

grep 则是分析一堆信息，若一行当中有匹配的数据，则将这一行数据拿出来,通常和管道命令结合起来

选项与参数：

- a：将 binary 文件以 text 文件的方式搜索数据
- c：计算找到「搜索字符」的次数
- i：忽略大小写
- n：输出行号
- v：反向选择，显示出没有搜索字符串的那一行数据
- `--color`：可以将找到的关键词部分加上颜色显示

```sh

[root@localhost demo1]# head /etc/passwd | grep 'mail*'
mail:x:8:12:mail:/var/spool/mail:/sbin/nologin

```

 ##### wc

wc 可以计算输出的信息。比如：/etc/man_db.conf 这个文件里面有多少字？多少行？

```bash
wc [-lwm]

-l：仅列出行
-w：仅列出多少字（英文单字）
-m：多少字符
    
```

```bash
# 范例 1：/etc/man_db.conf 这个文件里面有多少字
[mrcode@study ~]$ cat  /etc/man_db.conf | wc
	   行     字数	   字符数
    131     723    5171

# 范例 2：last 可以输出登陆者，但是 last 最后两行并非账户内容，那么该如何以一行指令取得登录系统的总人次？
last | grep [a-zA-Z] | grep -v 'wtmp' | grep -v 'reboot' | grep -v 'unknown' | wc -l
138
# grep 正则匹配，排除了非英文字符的账户
# grep -v 反向选择，相当于排除了指定的账户
# 最后使用 wc 统计行数
 
```



##### cut

```bash
cut -d '分割字符' -f fields  # 用于有特定分割字符
cut -c 字符区间							 # 用于排列整齐的信息
 
    
```

选项与参数：

- d：后面接分割字符。与 `-f` 一起使用
- f：依据 -d 的分割字符将一段信息分区成数段，用 -f 取出第几段的意思
- c：以字符（characters）的单位取出固定字符区间

```bash
# 范例 1：将 PATH 变量取出，我要找出第 5 个路径
[mrcode@study ~]$ echo ${PATH}
/usr/lib64/qt-3.3/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/mrcode/.local/bin:/home/mrcode/bin
# 数量是从 1 开始，不是从 0 哟
[mrcode@study ~]$ echo ${PATH} | cut -d ':' -f 5
/usr/sbin

# 取出第 5 个和第 6 个
[mrcode@study ~]$ echo ${PATH} | cut -d ':' -f 5,6
/usr/sbin:/home/mrcode/.local/bin
```

```bash
# 范例 3 ：用 last 将显示的登陆者信息，仅留下用户名
[mrcode@study ~]$ last
# 账户 		终端机					登录 IP					日期时间						
mrcode   pts/1        192.168.0.105    Mon Dec  2 01:25   still logged in   
mrcode   pts/0        192.168.0.105    Mon Dec  2 01:25   still logged in   
mrcode   pts/1        192.168.0.105    Mon Dec  2 00:21 - 01:12  (00:51)  
# 用空格分隔的数据，那么可以这样做
[mrcode@study ~]$ last | cut -d ' ' -f 1
mrcode
mrcode
mrcode
# 其实 账户和终端机之间的空格有好几个，并不是一个所以使用下面的命令并不能把 终端机一列也提取出来
last | cut -d ' ' -f 1,2
```



##### 排序命令

**sort**



```bash
sort [-fbMnrtuk] [file or stdin]
```

选项与参数：

- f：忽略大小写的差异
- b：忽略最前面的空格符
- M：以月份的名字来排序，例如 JAN、DEC 等排序方法
- n：使用纯数字进行排序，默认是以文字形态来排序
- r：反向排序
- u：uniq，相同的数据中，仅出现一行代表，也就是去重
- t：分隔符，预设使用 「tab」来分割
- k：以那个区间（field）来进行排序

```bash
# 范例 1：个人账户都记录在 /etc/passwd 下，将账户进行排序
[mrcode@study ~]$ cat /etc/passwd | sort
abrt:x:173:173::/etc/abrt:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
avahi:x:70:70:Avahi mDNS/DNS-SD Stack:/var/run/avahi-daemon:/sbin/nologin
bin:x:1:1:bin:/bin:/sbin/nologin
chrony:x:993:990::/var/lib/chrony:/sbin/nologin
# 可以看到按字符排序了

# 范例 2：/etc/passwd 内容是以 : 来分割的，想使用第三栏进行排序
[mrcode@study ~]$ cat /etc/passwd | sort -t ':' -k 3
root:x:0:0:root:/root:/bin/bash
mrcode:x:1000:1000:mrcode:/home/mrcode:/bin/bash
qemu:x:107:107:qemu user:/:/sbin/nologin
operator:x:11:0:operator:/root:/sbin/nologin
# 第三栏是数字，但是这里并没有按数字大小来排序，因为默认使用文字排序
# 与数值大小进行排序
[mrcode@study ~]$ cat /etc/passwd | sort -t ':' -k 3 -n
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin

# 范例 3：利用 last ，将输出的数据仅取账户，并排序
[mrcode@study ~]$ last | cut -d ' ' -f 1 | sort

mrcode
mrcode
 
```

##### join：合并两个文件中相同行的数据

```bash
join [-ti12] file1 file2
 
      
```

选项与参数：

- t：join 默认以空格符分割数据，并且比对「第一个字段」的数据，如果两个文件相同，则将两笔数据连城一行，且第一个字段放在第一个
- i：忽略大小写
- 1：数值 1，代表「第一个文件要用哪个字段来分析」
- 2：数值 2，代表「第二个文件要用哪个字段来分析」

```bash
# 范例 1：用 root 身份，将 /etc/passwd 与 /etc/shadow 相关数据整合成一栏
[root@study ~]# head -n 3 /etc/passwd /etc/shadow
==> /etc/passwd <==
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin

==> /etc/shadow <==
root:$6$oTg/fYGfv9/GIl6h$UEcmYlRZacV757rHtXlvmu5xH5TWGfqd3eDOEotB3CAc5mcW5UEoMTSg0pDICd/sYGrEScsHQY9tYZY0FGkKS1::0:99999:7:::
bin:*:17834:0:99999:7:::
daemon:*:17834:0:99999:7:::
# 输出的信息来看，最左边的的账户有相同的账户，且以 : 分割

[root@study ~]# join -t ':' /etc/passwd /etc/shadow | head -n 3
# 看到了吗，作用就是将某个字段的数据合并成一段
root:x:0:0:root:/root:/bin/bash:$6$oTg/fYGfv9/GIl6h$UEcmYlRZacV757rHtXlvmu5xH5TWGfqd3eDOEotB3CAc5mcW5UEoMTSg0pDICd/sYGrEScsHQY9tYZY0FGkKS1::0:99999:7:::
bin:x:1:1:bin:/bin:/sbin/nologin:*:17834:0:99999:7:::
daemon:x:2:2:daemon:/sbin:/sbin/nologin:*:17834:0:99999:7:::
```

##### paste：将两行贴在一起

将两行贴在一起，且中间以 tab 隔开

```bash
paste [-d] file1 file2

-d：后面可以接分割符。默认以 tab 来分割
- ：如果 file 部分写成 -，表示来自 standard input    
```



```bash
# 范例 1：用 root 身份，将 /etc/passwd 与 /etc/shadow 同一行贴在一起
[root@study ~]# paste /etc/passwd /etc/shadow | head -n 3
root:x:0:0:root:/root:/bin/bash root:$6$oTg/fYGfv9/GIl6h$UEcmYlRZacV757rHtXlvmu5xH5TWGfqd3eDOEotB3CAc5mcW5UEoMTSg0pDICd/sYGrEScsHQY9tYZY0FGkKS1::0:99999:7:::
bin:x:1:1:bin:/bin:/sbin/nologin        bin:*:17834:0:99999:7:::
daemon:x:2:2:daemon:/sbin:/sbin/nologin daemon:*:17834:0:99999:7:::
```



### 权限

#### 初步认识

当我们使用`ls -l`命令的时候，终端的输出如下

```sh
-rw-r--r--. 1 root root 30 2月  28 20:58 accountadd.txt
```

其中`-rw-r--r--`就代表了文件的权限信息

`-rw-r--r--`  开头的`-`代表文件类型为普通文件

往后每三个为一组：

- 第一组代表文件拥有者对该文件的权限，
- 第二组代表文件所属用户组对该文件的权限，
- 第三组代表其他非拥有者与用户组者对该文件的权限。

所以说文件权限是主要面向以上三类人的

#### 重要性

- 系统保护的功能

  保证一些关键文件只有root用户有修改权限，防止普通用户胡乱修改

- 团队开发软件或数据共享的功能

  就是多人协作的时候，希望每个人都可以使用某一些目录下的文件，而其他人不开放。 比如 testgroup 团队有三个人 t1、t2、t3 ，那么就可以将团队所需的文件权限设置为 `-rwxrws---` 该组内的都可读写与执行

- 未将权限设置妥当的危害

  很简单，比如只有 root 才能做的开关机，新增、或删除用户等等的指令，那么随意人都可以用的话， 就乱套了

#### 如何改变文件属性与权限

主要有三个命令

- chgrp：改变文件所属群组
- chown：改变文件拥有者
- chmod：改变文件的权限、SUID、SGID、SBIT 等等的特性

##### chgrp改变所属群组

```sh
[root@localhost demo3]# ll
总用量 8
-rw-r--r--. 1 root root 30 2月  28 20:58 accountadd.txt
-rw-r--r--. 1 root root 89 2月  28 21:03 creat_user.sh
[root@localhost demo3]# chgrp test accountadd.txt 

[root@localhost demo3]# ll
总用量 8
#这里已经修改完成

-rw-r--r--. 1 root test 30 2月  28 20:58 accountadd.txt
-rw-r--r--. 1 root root 89 2月  28 21:03 creat_user.sh
```

##### chown改变文件拥有者

```sh
chown [-R] 账户名称 文件或目录
chown [-R] 账户名称:组名 文件或目录

```

```sh
[root@localhost demo3]# chown wh accountadd.txt 
[root@localhost demo3]# ll
总用量 8
-rw-r--r--. 1 wh   test 30 2月  28 20:58 accountadd.txt
-rw-r--r--. 1 root root 89 2月  28 21:03 creat_user.sh
#同时修改用户和组
[root@localhost demo3]# chown wh:root accountadd.txt 
[root@localhost demo3]# ll
总用量 8
-rw-r--r--. 1 wh   root 30 2月  28 20:58 accountadd.txt
-rw-r--r--. 1 root root 89 2月  28 21:03 creat_user.sh

```

##### 改变权限chmod

chmod指令改变权限有两种形式，一种是用数字，一种使用符号

```sh
chmod [-R] xyz 文件或目录

xyz：就是刚刚的数值类型的权限范围，为 rwz 属性数值的相加
-R：递归

```

数字和权限的对应关系为

- r = 4
- w = 2
- x = 1

常用的权限数值为

- `-rw-rw-r--` 664 ：一般文件，可读可写无执行
- `-rwxr-x-r-x` 755：shell 脚本文件，拥有者可读写执行，其他的都只能可读可执行，不可编辑
- `-rwxr------` 740：不希望该文件被其他人看到（能看到文件，但是不能读取里面的内容）

修改示例就是 `chmod 740 text.txt`

##### Linux文件种类

- 正规文件（regular file）

  为 `-` 的文件，另外依照文件的内容又大致分为：

  - 纯文本文档（ASCII）：比如使用 cat ~/.bashrc，就能把该文件内容读取出来

  - 二进制文件（binary)：可执行文件 scripts （文字型批处理文件不算）

  - 数据格式文件（data）：有些程序运行中会读取某些特定文件格式的文件

    比如 linux 在登录时，会将登录的数据记录在 /var/log/wtmp 文件内， 但是使用 cat 时，会读出来乱码，因为是一种特殊格式的文件

  笔者唯一没有明白的就是 二进制文件，怎么是 scripts 文件呢？

- 目录（directory）：d

- 连接文档（link）：类似 windows 中的快捷方式，用小写（L）的 l 表示

- 设备与装置文件（device)

  与系统周边及存储等相关文件，通常都集中在 /dev 这个目录下，通常又分为两种：

  - 区块（block）设备文档：使用 b 表示

    就是一些存储数据，供系统随机存取的接口设备，比如硬盘、软盘等。 可以随机在硬盘的不同区块读写。可以看看 /dev/sda 会发现第一个属性就是 b

  - 字符（character）设备文件：用 c 表示

    一些串行端口的接口设备，例如键盘鼠标等。这些设备的特性就是一次性读取的，不能够截断输出。 举例来说，你不可能让鼠标跳跃到另一个画面，而是连续性滑动到另一个地方

- 数据接口文件（sockets）：用 s 表示

  这种类型的文件通常被用在网络上的数据承接。启动程序监听客户端的请求，客户端透过这个 socket 来进行数据的沟通 最常在 /run 或 /tmp 这个目录中

- 数据传送文件（FIFO,pipe）：使用 p 表示

  FIFO 也是一种特殊的文件类型，主要目的在解决多个程序同时存取一个文件所造成的并发错误问题， 是 first-in-first-out 的缩写

#### Linux目录配置的依据FHS

FHS（Filesystem Hierarchy Standard）标准：让使用者可以了解到已安装软件通常放置于哪个目录下

|          -          |    可分享的（shareable）     | 不可分享的（unshareable） |
| :-----------------: | :--------------------------: | :-----------------------: |
|   不变得（static)   |     `/usr`（软件放置处）     |    `/etc` （配置文件）    |
|          -          |     `/opt`（第三方软件）     |  `/boot` （开机与核心）   |
| 可变动的（variable) |  `/var/mail` （使用者邮箱)   |  `/var/run` （程序相关）  |
|          -          | `/var/spool/news` （新闻组） | `/var/lock` （程序相关）  |



- 可分享的：

  可以分享给其他系统挂载使用的目录；所以包括执行文件与用户的邮件等数据，是能够分享给网络上其他主机挂载用的目录

- 不可分享的：

  自己机器上面运行的装置文件或则是与程序有关的 socket 文件等，由于仅与自身机器有关，就不适合分享了

- 不变得：

  有些数据是不会经常变动的，跟随 distribution 而不变动的。例如函数库、文件说明文件、系统管理员所管理的主机服务配置文件等

- 可变动的：

  经常改变的数据，例如登录文件、一般用户可自行收受的新闻组等

**下面是Linux的文件树图**

![image-20230228214739040](C:\Users\Admin\AppData\Roaming\Typora\typora-user-images\image-20230228214739040.png)

##### 根目录

根目录是整个系统最重要的一个目录，里面所有的目录都是由根目录衍生出来的，FHS 定义出根目录下应该要有以下目录存在

根目录下的主要文件有

- `/bin`

  系统有很多放置执行文件的目录，单 /bin 比较特殊。 因为放置的是在单人维护模式下还能够被操作的指令。

  /bin 下的指令可以被 root 与一般账户所使用，主要有 cat、chmod、chown、date、mv、mkdir、cp、bash 等常用命令

- `/boot`

  主要放置开机会使用到的文件，包括 linux 核心文件以及开机选单与开机锁需配置文件等。

  **Linux kernel 常用额文件名为 vmlinuz** ，如果使用 grub2 开机管理程序，则还会存在 /boot/grub2 这个目录

- `/dev`

  任何装置与接口设备都是以文件形态存在这个目录当中。只要透过存取这个目录下的某个文件， 就等于存取某个装置，比较重要的文件有 /dev/null、/dev/zero、/dev/tty、/dev/loop*、/dev/sd* 等

- `/etc`

  系统主要的配置文件几乎都放在这个目录中，例如人员的账户密码文件、各种服务的启动文件等， 一般来说，这个目录下的各文件属性是可以让一般使用者查阅的，但是只有 root 有权利修改。

- /lib

  lib 下放的是在 **开机时会用到的函数库**，以及在 /bin 和 /sbin 下的指令会呼叫的函数库。

- /media

  放的是可移除的设备，例如 软盘、光盘、 DVD 等都暂时挂载于此。

- `/mnt`

  如果暂时挂载某些额外的设备，一般建议可以放到这个目录中，在很早的时候该目录用途与 /mnt 相同， 只是有了 /media 后，这个目录就用来暂时挂载用了

- `/root`：
  该目录为系统管理员，也称作超级权限者的用户主目录。

- `/tmp`

  一般用户或则是正在执行的程序暂时放文件的地方。该目录是任何人都可以存取的，所以需要定期清理一下。 因此 FHS 甚至建议在开机时，应该删除该目录下的文件

- `/home`

  系统默认的用户目录。在你新增一个一般使用者账户时，默认的用户家目录都会规范到这里来。 比较重要的是，家的木有两种代号：

  - ~：代表目前这个用户的家目录
  - ~mrcode：则代表 mrcode 的家目录

- `/sbin`

  Linux 有非常多的指令是用来设置系统环境的，这些指令只有 root才能够利用来设置系统， 其他用户只能用来「查询」。放在 /sbin 下的为开机过程中所需要的，包括了开机、修复、还原系统所需要的指令。

##### /usr

  /usr 里面放置的数据属于可以分享的与不可变动的.

  /usr 不是 user 的缩写，而是 Unix Software Resource 的缩写（Unix 操作系统软件资源）

  一般来说 /usr 的此目录建议有以下：

  第一部分：FHS 要求必须要存在的目录

  - `/usr/bin/`

    所有一般用户能够使用的指令都放在这里。 CentOS7 新版已经将全部的用户指令放在这里， 而使用连接文件的方式将 /bin 连接到这里。也就是说 /usr/bin 与 /bin 是一样的了。 而且 FHS 要求在此目录下不应该有子目录

  - `/usr/lib/`

    基本上 与 /lib 功能相同，使用 /lib 就是连接到此目录的

  - `/usr/local/`

    系统管理员在本机自行安装自己下载的软件（非 distribution 默认提供），建议安装到此目录。 比如，distribution 提供的软件较旧，想安装新的但是又不想移除旧版本的，就可以将新版安装到这里。

    该目录下也是具有 bin、etc、include、lib 的次目录

  - `/usr/sbin`

    非系统正常运作所需要的系统指令。最长久的就是某些网络服务器软件的指令（daemon）。 不过功能基本与 /sbin 差不多，因此 /sbin 也是连接到此目录的

  - `/usr/share/`

    主要放置只读架构的数据文件和共享文件。在该目录下的数据几乎是不分硬件架构均可读取的数据， 因为几乎上都是文本文件。常见的还有以下次目录

    - `/usr/share/man`：联机帮助文件
    - `/usr/share/doc`：软件杂项的文件说明
    - `/usr/share/zoneinfo` 与时区有关的时区文件

  第二部分：FHS 建议可以存在的目录

  - `/usr/games/`：与游戏比较相关的数据

  - `/usr/include`：

    c/c++ 等程序语言的档头（header）与包含档（include）放置处，当我们以 tarball 方式 （tar.gz 的方式安装软件）安装某些数据时，会使用到里头的许多包含档

  - `/usr/libexe`

    某些不被一般使用者惯用的执行档或脚本，例如大部分的 x 窗口下的操作指令

  - `/usr/lib<qual>`

    与 `/lib<qual>` 功能相同，连接过来的

  - `/usr/src`

    一般源码建议放这里，src 有 source 的意思。 至于核心源码则建议放到 /usr/src/linux 目录下

##### /var

  主要放置的是针对常态性变动的文件，包括 cache、登录文件（log file）以及某些软件所产生的文件， 包括程序文件（lock file，run file），或则例如 mysql 数据库的文件等， 常见的目录有

- `/var/cache`：应用程序运行中使用的缓存文件

- `/var/lib`：

  程序本身执行过程中，需要用到的数据文件存放处。在此目录下各自的软件应该要有各自的目录， 比如：mysql 数据库放到 /var/lib/mysql 而 rpm 的数据库则放到 /var/lib/rpm

- `/var/lock`

  某些装置或是文件资源一次只能被一个程序使用，所以这里存放的是加锁的标识， 目前此目录已经挪到 /run/lock 中了

- `/var/mail`：个人电子邮件信箱目录，不过也被放置到了 /var/spool/mail 中了，通常两个目录互为连接文件

- `/var/run`

  某些程序或则是服务启动后，会将他们的 PID 放置在这个目录下，与 /run 相同，也连接到 /run 下了。 至于 PID 后续讲解

- `/var/spool`

  通常放置一些对了数据，这些数据被使用后通常都会被删除。 比如：系统受到新信会放到 /var/spool/mail 中，但使用者手下该信件后该封信原则上就会被删除。 信件如果展示寄不出去，则会放到 /var/spool/mqueue 中。等待被送出后会被删除。

  如果是工作排程数据（crontab）就会被放到 /var/spool/cron 目录中

  

### 用户和组



账户管理是管理员工作中相当重要的一环，并且所有一般用户的账户申请，都必须需要管理员的协助才可以，所以必须了解下如何管理好一个服务器主机账户。



#### 使用者标识符

 当我们输入`id`命令时，我们会看到关于用户的相关信息

```sh
[root@localhost home]# id user01
uid=7792(user01) gid=7792(user01) 组=7792(user01)
```

那么输入的这一行都代表了什么意思呢

- uid:user id
- gid：group id

这两个信息可以帮助我们知道此用户对应的账户和属组，第三个组可以帮我们设置`附加组`



那么当我们登录Linux时候，系统是如何确认我们身份的呢？

1. 首先当需要我们输入账号密码
2. 用户得到账户密码信息后会先去/etc/passwd文件下查找是否有对应的账户，然后在/etc/shado对照密码是否正确
3. 如果一切正确，就进入shell的管控阶段

这里面有两个非常重要的文件:/etc/passwd和/etc/shadow

那么让我们来查看一下这两个文件

##### /etc/passwd

```sh
[root@localhost home]# cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
bin:x:1:1:bin:/bin:/sbin/nologin
daemon:x:2:2:daemon:/sbin:/sbin/nologin
adm:x:3:4:adm:/var/adm:/sbin/nologin
...
huangjiu:x:1000:1000::/home/huangjiu:/bin/bash
liqiang:x:1001:1001::/home/liqiang:/bin/bash

```

其中各代表的意思是

**huangjiu**:x:**1000**:**1000**:           :**/home/huangjiu:/bin/bash**

1                 2   3       4          5             6                                  7        

字段1   用户账号名称

字段2   用户密码字串或者密码占位符

字段3   用户账号的UID号

字段4  所属基本组账号的GID号

字段5  用户描述信息

字段6  家目录     默认用户的家目录都在home目录下   与用户同名

字段7  登录shell信息

##### /etc/shadow

```sh
[root@localhost home]# cat /etc/shadow
root:$6$pJFBnoJ/4CPj9o36$XgDKAYgD0ukVAZaoRBmD1BgWNG2r.wAx/o3SFQlmbzu4U2WkybhcUgsE6aifnc7SoXfKuzsq23UkLjj0TglBS1::0:99999:7:::
bin:*:18353:0:99999:7:::
daemon:*:18353:0:99999:7:::
adm:*:18353:0:99999:7:::
...
huangjiu:$6$n3SWSLZq$U1JoWAeL5Ab9iL5Us/fM8DEzvrUayrMvLXhEzhI85x1EU9.NEA2X8lHzSW4YxzmHFPglfMoQ3tYwfi2Zn7PcX0:19408:0:99999:7:::
```

以`:`作为分隔符算一个字段

1. 账户名称，用来与 /etc/passwd 中账户名称对应

2. 密码：经过加密的密码

3. 最近修改密码的日期：记录了修改密码的那一天的日期

4. 密码不可被修改的天数：与第 3 个字段相比

5. 密码需要重新修改的天数：与第 3 个字段相比

   也就是该密码在最近修改之后，生效的天数，99999=273 年，也大概标识不限制了

6. 密码需要变更期限前的警告天数：与第 5 个字段相比

   在到期前 n 天，系统发出警告给该账户，告诉你该账户还有 n 天密码过期了，请尽快修改该密码。如上面的例子为 7 天，则到期之前 7 天内，系统会警告该用户

7. 密码过期后的账户宽限时间：与第 5 个字段相比

   当密码过期几天后，那么再登录系统则完全无法登录了

8. 账户失效日期

   与第 3 个字段一样，使用的是 1970 年以来的总数日设置的。表示该账户在此规定的日期之后，将无法再使用。这就是账户失效，而无论密码是否有过期，该账户都无法使用

   该字段一般会用在收费服务的系统中，规定一个日期让该账户无法使用

9. 保留：保留字段，防止以后有新功能的加入

shadow中的密文是经过加密的，获取shadow的加密机制，可以通过以下指令

```sh
[root@study ~]# authconfig --test | grep hashing
 password hashing algorithm is sha512		# 密码加密算法为 sha512

```

##### 忘记密码怎么办

- 一般用户密码忘记：找系统管理员帮忙，可以以 root 身份使用 passwd 指令来处理，而不需要旧密码
- root 密码忘记：这个就麻烦了，只有通过各种手段进入 Linux 再去修改 /etc/shadow 文件，比如
  - 第 19 章中讲解的重启进入单人维护模式，系统会主动的给予 root 权限的 bash 接口，此时再用 passwd 修改密码即可
  - 使用 Live CD 开机后挂载根目录去修改 /etc/shadow 文件，将 root 的密码字段清空，再登录时就相当于不要密码了



**上面介绍了关于用户的两个文件，那么接下来介绍群组的有关文件**

##### /etc/group

```sh
[root@localhost home]# cat /etc/group
root:x:0:
bin:x:1:
daemon:x:2:
sys:x:3:
```

共 4 个字段

1. 组名：与第三字段 GID 对应

2. 群组密码

   通常不需要设置，如果非要设置，该配置也移动到 /etc/gshadow 文件中了。目前很少有机会设置群组管理员

3. GID：与 /etc/passwd 中第 4 个字段对应

4. 此群组支持的账户名称

   一个账户可以加入多个群组，某个账户加入此群组时，将该账户填入该字段即可，比如 mrcode 与 changsha 加入 root 群组，该字段内容为 `mrcode,changsha`，整行数据为 `root:x:0:mrcode,changsha`

前面我们使用`id`命令查看用户信息的时候，一个用户不仅有一个属组，他还会有一个附加属组，那么在工作过程中到底应该以哪一个为准呢？这就涉及到了一个有效群组的概念了

##### 有效群组

每个使用者在 `/etc/passwd` 中的第 4 个字段是 GID，该 GID 则是初始群组，当用户登录系统，立刻就拥有该群组的相关权限。

```sh
[root@localhost home]# id user01
uid=7792(user01) gid=7792(user01) 组=7792(user01)

#在这个例子中，user01属组就是随着user01用户一起建立的，而目前还没有给他添加附加组
[root@localhost home]# groupadd test
[root@localhost home]# usermod -G test user01
[root@localhost home]# id user01
uid=7792(user01) gid=7792(user01) 组=7792(user01),7821(test)
#此时我们user01用户就会有两个属组了

#此时我们登录user01用户查看
[root@localhost home]# su - user01
[user01@localhost ~]$ groups
user01 test
#此时输出的第一个属组就是有效属组
```

此时user01就可以拥有属组 user01和test两个数组的全部权限

**一个用户可以所属多个附加组，但只能有一个初始组**



#### 新建用户和组

##### useradd

```bash
useradd [-u UID] [-g 初始群组] [-G 次要群组] [-mM] [-c 说明栏] [-d 家目录绝对路径] [-s shell] 使用者账户

选项与参数：

	-u：UID 是一组数字。直接指定一个特定的 UID 给该账户
	-g：字符串的初始组名，该字符串的 GID 在 /etc/passwd 的第 3 个字段内
	-G：字符串的次要群组，该选项会修改 /etc/group 内的相关字段
	-M：强制！不要建立用户家目录（系统账户默认值）
	-m：强制！要建立用户家目录（一般账户默认）
	-c：/etc/passwd 中第 5 字段的说明内容，可以随便设置
	-d：指定某个目录成为家目录，请务必使用决定路径
	-r：建立一个系统账户，该账户的 UID 有限制（参考 /etc/login.defs）
	-s：后面接一个 shell，若没有指定则预设是 /bin/bash
	-e：后面接一个日期，格式为 YYYY-MM-DD ，此项可写入 shadow 第 8 字段，即是账户失效日期
	-f：后面接 shadow 的第 7 字段，该密码是否会失效。0 为立刻失效，-1 为永远不失效（密码只会过期而强制域登录时重新设置）

注意这里是没有密码配置的，密码的设置需要用到 passwd 指令

```



选项与参数：

	-u：UID 是一组数字。直接指定一个特定的 UID 给该账户
	-g：字符串的初始组名，该字符串的 GID 在 /etc/passwd 的第 3 个字段内
	-G：字符串的次要群组，该选项会修改 /etc/group 内的相关字段
	-M：强制！不要建立用户家目录（系统账户默认值）
	-m：强制！要建立用户家目录（一般账户默认）
	-c：/etc/passwd 中第 5 字段的说明内容，可以随便设置
	-d：指定某个目录成为家目录，请务必使用绝对路径
	-r：建立一个系统账户，该账户的 UID 有限制（参考 /etc/login.defs）
	-s：后面接一个 shell，若没有指定则预设是 /bin/bash
	-e：后面接一个日期，格式为 YYYY-MM-DD ，此项可写入 shadow 第 8 字段，即是账户失效日期
	-f：后面接 shadow 的第 7 字段，该密码是否会失效。0 为立刻失效，-1 为永远不失效（密码只会过期而强制域登录时重新设置）

注意这里是没有密码配置的，密码的设置需要用到 passwd 指令



当我们使用useradd新建用户之后，CentOS会帮我们规定很多默认值

- 在 `/etc/passwd` 中创建一行与账户相关的数据，包括建立 UID、GID、家目录等
- 在 `/etc/shadow` 中创建该账户的密码相关参数，但是无密码
- 在 `/etc/group` 中创建一个与账户名同名的组名
- 在 `/home` 下创建一个与账户同名的目录作为家的目录，且权限为 700

可通过`useradd -D`命令查看

```
[root@localhost home]# useradd -D
GROUP=100
HOME=/home
INACTIVE=-1
EXPIRE=
SHELL=/bin/bash
SKEL=/etc/skel
CREATE_MAIL_SPOOL=yes
```

##### passwd

设置密码

```sh
[root@localhost home]# passwd user01
更改用户 user01 的密码 。
新的 密码：
无效的密码： 密码少于 8 个字符 
#这里我输入了一个12345 系统弹出一个警告，可以忽略，回车进入下一步
重新输入新的 密码：
passwd：所有的身份验证令牌已经成功更新。
```

另外还有一种设置密码的方式比较常用

```sh
[root@localhost home]# echo 1234566 |passwd  user01 --stdin
更改用户 user01 的密码 。
passwd：所有的身份验证令牌已经成功更新。

#这种方式可以帮我们查看密码输入是否正确
```



##### chage

此命令可帮助我们了解更多关于密码的信息

```bash
chage [-ldEImMW] 账户名

选项与参数：
	-l: 列出该账户的详细密码参数
	-d：后面接日期，修改 shadow 第 3 字段，最近一次修改密码的日期，格式为 YYYY-MM-DD
	-E：后面接日期，修改 shadow 第 8 字段，账户失效日，格式 YYYY-MM-DD
	-I：后面接天数，修改 shadow 第 7 字段，密码失效日期
	-m：后面接天数，修改 shadow 第 4 字段，密码最短保留天数
	-M：后面接天数，修改 shadow 第 5 字段，密码多久需要修改
	-W：后面接天数，修改 shadow 第 6 字段，密码过期前警告天数
 
```

##### userdel

删除用户的相关数据，使用起来很简单了，用户数据有：

- 用户账户、密码相关参数：`/etc/passwd 、/etc/shadow`
- 使用者群组相关参数：`/etc/group、/etc/gshadow`
- 用户个人文件数据：`/home/username、/var/spool/mail/username ...`

```bash
userdel [-r] username  

-r：连同用户的家目录也一起删除
```

```sh
[root@localhost home]# userdel -r user01
[root@localhost home]# id user01
id: user01: no such user

find: ‘user01’: 没有那个文件或目录
```

但是需要注意的是：如果想要删除该用户相关的所有文件等数据，在该指令下达之前，使用 `find / -user username` 找出整个系统内属于 username 的文件，再加以删除。

##### groupadd

新建属组

```sh
group add [-g gid] [-r] 组名

选项与参数：
	-g：后面接某个特定的GID，用来指定 GID
	-r：建立系统群组。与 /etc/login.defs 内的 GID_MIN 有关

```

##### groupmod

```sh
groupmod [-g gid] [-n group_name] 群组名

选项与参数：
	-g：修改现有的 GID 数字
	-n：修改现有的组名

```

##### groupdel

删除群组

```sh
groupdel [groupname]
```

有时候我们删除属组的时候可能会遇到无法删除的情况，这是因为该属组正在被使用

如果非要删除，有两种方式

- 修改 mrcode1 的 GID
- 删除 mrcode1 的使用者

#### 账户管理

在我们具体工作过程中，更多会遇到的情况是一个主机多个账户共同工作的情况，这个时候就会遇到一些问题

比如，当前有一个文件夹test，他是账户a和账户b共同使用的，a账户在test文件夹里面新建了一个a_001.txt的文件，然后b账户同样进入了test文件夹，那么对a_001.txt的文件进行了修改甚至删除操作，这就很不合适了

所以有什么办法可以解决这个问题呢？

可以通过给文件夹加上一个t权限来解决问题

**那么什么是t权限呢？**

```sh
[root@localhost lianxi]# chmod +t /lianxi/user_test/
[root@localhost lianxi]# su - a
上一次登录：一 2月 27 17:36:38 CST 2023pts/0 上
[a@localhost ~]$ cd /lianxi/user_t
-bash: cd: /lianxi/user_t: 没有那个文件或目录
[a@localhost ~]$ cd /lianxi/user_test/
[a@localhost user_test]$ touch a_001.txt
[a@localhost user_test]$ ls
a_001.txt
[a@localhost user_test]$ exit
登出
[root@localhost lianxi]# su - b
上一次登录：一 2月 27 17:37:07 CST 2023pts/0 上
[b@localhost ~]$ cd /lianxi/user_test/
[b@localhost user_test]$ ls
a_001.txt
[b@localhost user_test]$ rm -rf a_001.txt 
rm: 无法删除"a_001.txt": 不允许的操作

```



#### 身份切换

通常在工作中为了安全起见，我们更多是以一般用户的身份登录主机或者是服务器的，但如果只使用普通用户的身份，会有很多指令等无法执行，这个时候我们就可以通过用户切换+指令串的方式来解决

##### su

```sh
首先我们需要明白一个概念

su  后面不加用户是默认切到 root
su  是不改变当前变量
su - 是改变为切换到用户的变量
也就是说su只能获得root的执行权限，不能获得环境变量

而su -是切换到root并获得root的环境变量及执行权限
```

##### sudo

这个命令可以很好的帮助我们解决开始的问题

sudo 的执行仅需要自己的密码，还可以设置不需要密码就可以执行 sudo；由于 sudo 可以让你以其他用户的身份执行指令，（通常是利用 root 身份执行命令），所以并非所有人都能够执行 sudo，而是需要规范到 `/etc/sudoers`内的用户才能够执行 sudo 指令



这也就意味着我们可以通过sudo的命令来以普通的用户来执行root用户才能进行的操作，但是在此之前需要先在`/etc/sudoers`配置文件中设置一下，具体操作方法如下

```sh

[root@localhost lianxi]# vim /etc/sudoers

root    ALL=(ALL)       ALL
Cmnd_Alias NETWORKING = /sbin/route, /sbin/ifconfig, /bin/ping, /sbin/dhclient, /usr/bin/net, /sbin/iptables, /usr/bin/rfcomm, /usr/bin/wvdial, /sbin/iwconfig, /sbin/mii-tool

Cmnd_Alias LUTOOLS = /bin/nice, /bin/kill, /usr/bin/kill, /usr/bin/killall, /usr/sbin/useradd, /usr/sbin/userdel, /usr/sbin/ip

wh  ALL = LUTOOLS , NETWORKING


[root@localhost lianxi]# su - wh
上一次登录：一 2月 27 18:01:59 CST 2023pts/0 上
[wh@localhost ~]$ sudo useradd lqj

我们信任您已经从系统管理员那里了解了日常注意事项。
总结起来无外乎这三点：

    #1) 尊重别人的隐私。
    #2) 输入前要先考虑(后果和风险)。
    #3) 权力越大，责任越大。

[sudo] wh 的密码：
[wh@localhost ~]$ id lqj
uid=7825(lqj) gid=7827(lqj) 组=7827(lqj)

```

#### 查询使用者

##### w、who、last

可以使用w或者who来查询当前已登录系统的用户

```sh

[root@localhost /]# who
root     tty1         2023-02-28 19:38
root     pts/0        2023-02-28 19:38 (192.168.220.1)
root     pts/1        2023-02-28 19:38 (192.168.220.1)
root     pts/2        2023-02-28 19:39 (192.168.220.1)
[root@localhost /]# w
 19:41:38 up 3 min,  4 users,  load average: 0.03, 0.12, 0.06
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     tty1                      19:38    3:30   0.01s  0.01s -bash
root     pts/0    192.168.220.1    19:38    2.00s  0.01s  0.00s w
root     pts/1    192.168.220.1    19:38    2:50   0.01s  0.00s -bash
root     pts/2    192.168.220.1    19:39    1:38   0.01s  0.00s -bash
[root@localhost /]# 

```

##### 账户之间对话

**write**

```sh
#首先复制两个对话，然后就有了pts/0和pts/1两个用户  
# 在 root1 窗口上，对 root pts/0 的终端接口写信息
# hello 是root 传递的文字信息
#输入一行按下回车键，信息就会显示到对方那边去。所以他们两个就可以谈话了
# 要结束传递的话，需要通过组合键 ctrl + d 结束


[root@localhost /]# write root pts/1
hello

[root@localhost /]# 
Message from root@localhost.localdomain on pts/0 at 19:46 ...
hello
EOF

```

**mesg  启用或关闭对话功能**

这种方式是及时聊天，假如对方正在工作，就是打断他的工作，所以如果不想打开这个功能，可以使用命令`mesg n`

```sh
[wh@study ~]$ mesg n	# 关闭信息
[wh@study ~]$ mesg
is n
#不过这条命令对root是无效的
```

**wall 广播信息**

所有用户都能收到

```sh
[wh@study ~]$ wall "I will shutdown my linux server..."
[wh@study ~]$
Broadcast message from mrcode@study.centos.mrcode (pts/0) (Tue Feb 25 22:45:41 2020):

I will shutdown my linux server...

# 所有在线用户都能收到，包括 root，当然前提是对方 mesg y 打开时

```

**mail  使用者信箱**

wall、write需要用户在线才能传递信息，如过想要给离线用户发送信息，可以使用寄信命令`mail`

```sh
# root 用户给 wh 寄信
# 指令下达之后会进入写做模式，不过该模式下无法使用退格键，只能想好再写
[root@study ~]# mail -s "nice to meet you" mrcode
Hello,D.m tsai
Nice to meet you in the network.
You are so nice. bybye!
.					# 最后一行输入小数点，再次回车会完成寄信操作
EOT		
[root@study ~]#

#或者使用流来完成内容的导入
# 范例 ：将你的家目录下的环境变量文件 ~/.bashrc 寄给自己
mail -s "bashrc file content" wh < ~/.bashrc
# 范例 ：通过管线命令将 `ls -al ~` 内容传给 root 自己
ls -al ~ | mail -s "myfile" root

```

**收信**

收信也需要用到mail命令

```sh
[wh@study ~]$ mail
Heirloom Mail version 12.5 7/5/10.  Type ? for help.
"/var/spool/mail/mrcode": 1 message 1 new
>N  1 root                  Tue Feb 25 22:52  19/700   "nice to meet you"
& 		# 这里可以输入很多指令，可以通过输入 ？ 查询

# > ：是表示目前处理的信件是哪一封
# N ：表示该信件还未读过

# 尝试输入 ? 会出现以下的提示
& ?
               mail commands
type <message list>             type messages
next                            goto and type next message
from <message list>             give head lines of messages
headers                         print out active message headers
delete <message list>           delete messages
undelete <message list>         undelete messages
save <message list> folder      append messages to folder and mark as saved
copy <message list> folder      append messages to folder without marking them
write <message list> file       append message texts to file, save attachments
preserve <message list>         keep incoming messages in mailbox even if saved
Reply <message list>            reply to message senders
reply <message list>            reply to message senders and all recipients
mail addresses                  mail to specific recipients
file folder                     change to another folder
quit                            quit and apply changes to folder
xit                             quit and discard changes made to folder
!                               shell escape
cd <directory>                  chdir to directory or home if none given
list                            list names of all available commands

A <message list> consists of integers, ranges of same, or other criteria
separated by spaces.  If omitted, mail uses the last message typed.
&
```

#### 建立大量账户

使用shell脚本建立大量账户

```sh
#!bin/bash


for i in {00..20}
do
useradd std$i
echo 12345 |passwd --stdin username
done
 
```

还有更加完整的进阶版本

```sh
vim accountadd.sh

#!/bin/bash
# This shell script will create amount of linux login accounts for you.
# 1. check the "accountadd.txt" file exist？ you must create that file manually
#	one account name one line in the "accountadd.txt" file
# 2. use openssl to create users password
# 3. User must change his password in his first login
#
# 此命令行命令脚本将为您创建大量 Linux 登录。
# 1.检查 "accountadd.txt" 文件是否存在？您必须手动创建该文件，一个账户一行
# 2.使用 openssl 创建用户密码
# 3.用户必须在首次登录时更改密码
export PATH=/bin:/sbin:/usr/bin:/usr/sbin

# 0. userinput
usergroup=""		# 如果你的账户需要次要组，在这里定义
pwmech="openssl"	# 如果是 openssl(生成随机数) 则使用 openssl 指令生成 base64 的 6 位数随机密码
homeperm="no"		# 如果修改为 yes，则将该账户家目录权限修改为 711

# 1. 检查 accountadd.txt 文件
action="${1}"			# create 使用 useradd 指令、delete 使用 userdel 指令
if [ ! -f accountadd.txt ]; then
	echo "accountadd.txt 文件不存在！"
	exit 1
fi

# 如果有群组，则建立系统群组
[ "${usergroup}" != "" ] && groupadd -r ${usergroup}
rm -f outputpw.txt
usernames=$(cat accountadd.txt)

for username in ${usernames} 
do
	case ${action} in
		"create")
			# 存在组则拼接选项 -G 是为该用户添加次要群组
			[ "${usergroup}" != "" ] && usegrp=" -G ${usergroup} " || usegrp=""
			useradd ${usegrp} ${username}	# 新增账户
			# 如果没有值则使用用户名作为密码
			[ "${pwmech}" == "openssl" ] && usepw=$(openssl rand -base64 6) || usepw=${username}
			echo ${usepw} | passwd --stdin ${username}  # 创建密码
			chage -d 0 ${username}		# 配置首次登陆必须修改密码
			[ "${homeperm}" == "yes" ] && chmod 711 /home/${username}
			echo "username=${username},password=${usepw}" >> outputpw.txt
		;;
		"delete")
			echo "删除用户 ${username}"
			userdel -r ${username}			# -r 将用户家目录也删除
		;;
		*)
			echo "请使用：$0 [create|dellete]"
		;;
	esac
done

```

测试结果如下

```sh
vim accountadd.txt

std01
std02
std03
std04
std05

```

```sh
sh accountadd.sh create
[root@study ~]# sh accountadd.sh create
更改用户 std01 的密码 。
passwd：所有的身份验证令牌已经成功更新。
更改用户 std02 的密码 。
passwd：所有的身份验证令牌已经成功更新。
更改用户 std03 的密码 。
passwd：所有的身份验证令牌已经成功更新。
更改用户 std04 的密码 。
passwd：所有的身份验证令牌已经成功更新。
更改用户 std05 的密码 。
passwd：所有的身份验证令牌已经成功更新。

[root@study ~]# cat outputpw.txt 
username=std01,password=s4j4jdwr
username=std02,password=G4iW/O6M
username=std03,password=HGO0rvI8
username=std04,password=17NAhvgS
username=std05,password=Q2CftODm

# 可以看到输出的账户和密码信息，你可以打印出来，一行一条裁剪，然后发给使用者

```

#### 账户管理

将本服务的账户分开管理

- 分为单纯邮件使用者：将该账户加入名为 mail 的初始群组，且此账户不可使用 bash 等 shell 登陆系统。
- 可登陆系统账户：将该账户加入 youcan 的次要群组

```sh

# 1. 检查两个群组是否存在，不存在则建立
grep mail /etc/group
grep youcan /etc/group
groupadd youcan

# 2. 创建邮件账户，可以准备脚本来处理
vim popuser.sh
#!/bin/bash
for username in pop1 pop2 pop3
do
	# -g 初始群组； -s 指定 bash； -M 不要创建家目录
	useradd -g mail -s /sbin/nologin -M $username
	echo $username | passwd --stdin $username		# 将密码设置为账户相同
done

sh popuser.sh

# 3. 建立一般账户，同样适用脚本创建
vim loginuser.sh
#!/bin/bash
for username in pop1 pop2 pop3
do
	# -g 初始群组； -s 指定 bash； -M 不要创建家目录
	useradd -G youcan -s /bin/login $username
	echo $username | passwd --stdin $username		# 将密码设置为账户相同
done

sh loginuser.sh

```



### shell编程

### 进程管理和SELinux

#### 什么是进程

**触发任何一个事件，系统都会将它定义成一个进程，并且给予这个进程一个 ID，称为 PID，同时依据启发这个进程的用户与相关属性关系，给予这个 PID 一组有效的权限设置**。

可通过`ps aux`查看系统当前正在运行的进程

```sh
[root@localhost /]# ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root          1  2.2  0.3 128016  6640 ?        Ss   09:38   0:00 /usr/lib/
root          2  0.0  0.0      0     0 ?        S    09:38   0:00 [kthreadd
root          3  0.0  0.0      0     0 ?        S    09:38   0:00 [kworker/
root          4  0.0  0.0      0     0 ?        S<   09:38   0:00 [kworker/
root          5  0.0  0.0      0     0 ?        S    09:38   0:00 [kworker/
root          6  0.0  0.0      0     0 ?        S    09:38   0:00 [ksoftirq
root          7  0.0  0.0      0     0 ?        S    09:38   0:00 [migratio
root          8  0.0  0.0      0     0 ?        S    09:38   0:00 [rcu_bh]
root          9  0.2  0.0      0     0 ?        S    09:38   0:00 [rcu_sche
root         10  0.0  0.0      0     0 ?        S<   09:38   0:00 [lru-add-
root         11  0.0  0.0      0     0 ?        S    09:38   0:00 [watchdog
```

#### 进程与程序

当我们执行程序的时候，就可以触发事件获得一个PID，系统会通过这个PID来判断该给这个程序怎么样的权限，且通常情况下，由这个进程衍生出来的其他进程一般情况下也会沿用这个权限

#### 子进程与父进程

上面提到 **衍生出来的进程**，我们登陆到 bash，该 bash 是一个程序，并有一个 PID，在这个 bash 上执行指令，触发了相关指令的程序运行，从而得到该程序的 PID，这个 PID 就是一个子进程，原本的 bash 就是一个父进程



#### fork and exec

进程与父进程的关系最为复杂的在于进程相互间的呼叫。

在 Linux 的进程呼叫通常称为 fork-and-exec 的流程，进程都会借由父进程以复制（fork）的方式产生一个一模一样的子进程，然后被复制出来的子进程再以 exec 的方式来执行时机要进行的程序，最终就成为一个子进程的存在。整个流程类似下图：

![fork and exec](D:\Linux\我的博客\fork and exec.png)

#### 进程管理

为什么进程管理这么重要？

- 我们在操作系统时的各项工作都是经过某个 PID 来达成的（包括你的 bash 环境），因此，能不能进行某项工作，与该进程的权限有关
- 当整个系统资源要被使用光的时候，可以能够找出最耗资源的哪个进程，然后删除该进程，让系统恢复正常。
- 由于某个程序写的不好，导致产生一个有问题的进程在内存中，如何找出它，将它移除呢？
- 如果有 5、6 项工作在系统中运行，但其中有一项工作才是最重要的，该如何让那一项重要的工作被最优先执行？



##### ps进程观察

```sh
ps aux		# 观察系统所有的进程数据
ps -l 		# 观察与当前终端机相关的进程
ps -lA 		# 观察系统所有的进程数据（显示内容项同 ps -l 的项一样，只不过是系统所有进程）
ps axjf		# 连同部分进程树状态

选项与参数：
	-A：所有的 process 都显示出来，与 -e 具有同样的效果
	-a：不与 terminal 有关的所有 process
	-u：有效使用者（effective user）相关的 process
	x：通常与 a 一起使用，可列出完整信息
输出格式规划：
	l：较长、较详细的将该 PID 的信息列出
	j：工作的格式（jobs format）
	-f：做一个更为完整的输出
```

```sh
[root@localhost /]# ps aux
USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root          1  2.2  0.3 128016  6640 ?        Ss   09:38   0:00 /usr/lib/
root          2  0.0  0.0      0     0 ?        S    09:38   0:00 [kthreadd
root          3  0.0  0.0      0     0 ?        S    09:38   0:00 [kworker/
root          4  0.0  0.0      0     0 ?        S<   09:38   0:00 [kworker/
root          5  0.0  0.0      0     0 ?        S    09:38   0:00 [kworker/
root          6  0.0  0.0      0     0 ?        S    09:38   0:00 [ksoftirq
root          7  0.0  0.0      0     0 ?        S    09:38   0:00 [migratio
root          8  0.0  0.0      0     0 ?        S    09:38   0:00 [rcu_bh]


[root@localhost /]# ps -l
F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0   1589   1585  0  80   0 - 28919 do_wai pts/0    00:00:00 bash
0 R     0   1638   1589  0  80   0 - 38331 -      pts/0    00:00:00 ps

[root@localhost /]# ps -lA
F S   UID    PID   PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0      1      0  0  80   0 - 32004 ep_pol ?        00:00:00 systemd
1 S     0      2      0  0  80   0 -     0 kthrea ?        00:00:00 kthread
1 S     0      4      2  0  60 -20 -     0 worker ?        00:00:00 kworker
1 S     0      5      2  0  80   0 -     0 worker ?        00:00:00 kworker
1 S     0      6      2  0  80   0 -     0 smpboo ?        00:00:00 ksoftir
1 S     0      7      2  0 -40   - -     0 smpboo ?        00:00:00 migrati
1 S     0      8      2  0  80   0 -     0 rcu_gp ?        00:00:00 rcu_bh
1 S     0      9      2  0  80   0 -     0 rcu_gp ?        00:00:00 rcu_sch
```

对于`ps -l`输出内容的解析

- F：进程旗标（process flags），说明这个进程的总结权限，常见的号码有：
  - 4：表示此进程的权限为 root
  - 1：则表示此子进程仅进行 **复制（fork）而没有实际执行（exec）**
- S：进程状态（STAT），主要状态有：
  - R（Running）：正在运行中
  - S（Sleep）：该程序目前正在睡眠状态（idle），但可以被唤醒（signal）
  - D：不可被唤醒的睡眠状态，通常该程序可能在等待 I/O 的情况
  - T：停止状态（stop），可能是在工作控制（背景暂停）或除错（traced）状态
  - Z（Zombie）：僵尸状态，进程已终止但却无法被移除至内存外
- UUID/PID/PPID：代表此进程被该 UID 所拥有、进程的 PID 、此进程的父进程 PID
- C：代表 CPU 使用率，单位为百分比
- PRI/NI：Priority/Nice 的缩写，代表此进程被 CPU 所执行的优先级，数值越小表示该进程越快被 CPU 执行。
- ADDR/SZ/WCHAN：都与内存有关
  - ADDR：kernel function，该进程在内存的哪个部分，如果是 running 的进程，一般会显示 `-`
  - SZ：该进程用掉多少内存
  - WCHAN 该进程是否运行中，若为 `-` 表示正在运行中
- TTY：登陆者的终端机位置，若为远程登录则使用动态终端接口（pts/n）
- TIME：使用掉的 CPU 时间。注意：是此进程实际花费 CPU 运行的时间
- CMD：command 的缩写，此进程的触发程序指令



对于`ps aux`输出的解释

`USER        PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND`

- USER：该 process 属于哪个使用者账户
- PID：进程标识符
- `%CPU`：该进程使用掉的 CPU 资源百分比
- `%MEM`：占用的虚拟内存（KBytes）
- RSS：占用的固定内存（KBytes）
- TTY：在哪个终端机上面运行？
  - `?`：与终端机无关
  - `tty1-tty6`：本机上登录的
  - `pts/0`等：是由网络连接进入的进程
- STAT：目前的状态，与 `ps -l` 中的状态相同含义
- START：该进程被触发启动时间（如果太久不会显示具体时间）
- TIME：该进程实际使用 CPU 运行的时间
- COMMAND：进程执行的指令



##### 僵尸进程zombie

僵尸 zombie：该进程以及执行完毕或则是因故应该要终止了，但是该进程的父进程却无法完整的将该进程结束掉，而造成哪个进程一直在内存中。

在进程中它的标识是在 CMD 后面有 `<defunct>` 标识,例如下面这样

```bash
apache 8683 0.0 0.9 83383 9992 ？Z 14:33 0:00 /usr/sbin/httpd<defunct>
```

当系统不稳定时，容易造成僵尸进程，可能是因为程序有问题，或则是使用者的操作习惯不良等。

发现有僵尸进程时，应该找出来，分析原因，否则有可能一直产生僵尸进程

事实上，通常僵尸进程都已经无法管控，而直接交给 systemd 程序来负责了，偏偏 systemd 是系统第一个执行的程序，它是所有程序的父程序，无法杀掉该程序（杀掉它，系统就死了），所以，经过一段时间后，系统无法通过核心非经常性的特殊处理来将该进程删除时，那只有重启机器了



##### top动态观察系统进程的变化

ps 可以显示一个时间点的进程状态，而 top 则可以持续的侦测进程运行状态

```sh
top [-d 数字] | top [-bnp]

选项与参数：
	-d：后面可以接秒数，整个进程画面更新的秒数，预设是 5 秒更新一次
	-b：以批次的方式执行 top，还有更多的参数可以使用（莫名其妙啊，啥参数？），通常会搭配数据流重导向来将批次的结果输出为文件
	-n：与 -b 搭配，需要进行几次 top 的输出
	-p：指定某些 PID 来进行观察

在 top 执行过程中可以使用的按键指令：
	？：显示在 top 中可以输入的按键指令
	P：以 CPU 的使用资源排序显示
	M：以 Memory 的使用资源排序显示
	N：以 PID 排序
	T：由该进程使用 CPU 时间累积（TIME+）排序
	k：给予某个 PID 一个信号（signal）
	r：给予某个 PID 重新制定一个 nice 值
	q：离开 top 软件的按键
	E：切换单位显示，比如从 KB 切换为 G 显示
	c：切换 COMMAND 的信息，name/完成指令

```

```sh
# 范例 1：每两秒更新一次 top，观察整体信息
[root@localhost /]# top -d 2
top - 10:03:25 up 24 min,  3 users,  load average: 0.00, 0.01, 0.03
Tasks: 110 total,   1 running, 109 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  0.2 sy,  0.0 ni, 99.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0
KiB Mem :  1863028 total,  1481620 free,   230944 used,   150464 buff/cach
KiB Swap:  2097148 total,  2097148 free,        0 used.  1480708 avail Mem

   PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ 
   681 root      20   0  273192   4868   3736 S   0.5  0.3   0:01.82 
     1 root      20   0  128016   6648   4160 S   0.0  0.4   0:00.91 
     2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 
     4 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 
     5 root      20   0       0      0      0 S   0.0  0.0   0:00.09 
     6 root      20   0       0      0      0 S   0.0  0.0   0:00.04 
     7 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 
     8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 
     9 root      20   0       0      0      0 S   0.0  0.0   0:00.66 
    10 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 
    11 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 


```

top 的信息基本上分为两个区域，上面 6 行，和下面的列表

- 第一行信息：top -

  - 目前开机时间：22:20:11 这个

  - 开机到目前为止所经过的时间：up 1:05 这个

  - 已经登录系统的用户人数：4 users

  - 系统在 1、5、15 分钟的平均工作负载

    在第 15 章谈到过 batch 工作方式负载小于 0.8 就是这里显示的值了。

    表示的是，系统平均要负责运行几个进程，这里是三个值，也就是对应平均 1/5/15 分钟

    越小达标系统越空闲，若高于 1 ，那么你的系统进程执行太频繁了

- 第二行：tasks

  显示的是目前进程的总量与各个状态（running、sleeping、stopped、zombie）的进程数量

  如果发现有 zombie 进程的话，就需要找下是哪个进程变成了僵尸进程了

- 第三行：`$Cpus`

  CPU 整体负载，每个项目可使用 ？ 查询。

  需要特别注意的是 wa 项，表示 I/O wait，通常系统变慢，都是 I/O 产生的问题比较大，需要特别注意该项占用的 CPU 资源，如果是多核 CPU，可以按下数字键「1」来切换成不同 CPU

- 第四行和第五行

  目前的物理内存与虚拟内存（Mem/Swap）的使用情况。要注意的是 swap 的使用量要尽量的少，如果 swap 被大量使用，表示系统的物理内存不足

- 第六行：当在 top 程序中输入指令时，显示状态的地方

下面的大部分都见过了，就不在此赘述了

top 预设使用 CPU 使用率 `%CPU`作为排序的重点，如果想要使用内存使用率排序，可以按下 M 键，要离开按下 q 键

如果想要找出最耗 CPU 资源的进程时，大多使用 top 指令，然后以 CPU 使用资源来排序（p）

##### kill

kill 命令用于删除执行中的程序或工作。kill 可将指定的信息送至程序。预设的信息为 SIGTERM(15)，可将指定程序终止。若仍无法终止该程序，可使用 SIGKILL(9) 信息尝试强制删除程序。

最常用的信号是：

- 1 (HUP)：重新加载进程。
- 9 (KILL)：杀死一个进程。
- 15 (TERM)：正常停止一个进程。

**实例**

杀死进程

```
# kill 12345
```

强制杀死进程

```
# kill -KILL 123456
```

发送SIGHUP信号，可以使用一下信号

```
# kill -HUP pid
```

彻底杀死进程

```
# kill -9 123456
```

显示信号

```
# kill -l
1) SIGHUP     2) SIGINT     3) SIGQUIT     4) SIGILL     5) SIGTRAP
6) SIGABRT     7) SIGBUS     8) SIGFPE     9) SIGKILL    10) SIGUSR1
11) SIGSEGV    12) SIGUSR2    13) SIGPIPE    14) SIGALRM    15) SIGTERM
16) SIGSTKFLT    17) SIGCHLD    18) SIGCONT    19) SIGSTOP    20) SIGTSTP
21) SIGTTIN    22) SIGTTOU    23) SIGURG    24) SIGXCPU    25) SIGXFSZ
26) SIGVTALRM    27) SIGPROF    28) SIGWINCH    29) SIGIO    30) SIGPWR
31) SIGSYS    34) SIGRTMIN    35) SIGRTMIN+1    36) SIGRTMIN+2    37) SIGRTMIN+3
38) SIGRTMIN+4    39) SIGRTMIN+5    40) SIGRTMIN+6    41) SIGRTMIN+7    42) SIGRTMIN+8
43) SIGRTMIN+9    44) SIGRTMIN+10    45) SIGRTMIN+11    46) SIGRTMIN+12    47) SIGRTMIN+13
48) SIGRTMIN+14    49) SIGRTMIN+15    50) SIGRTMAX-14    51) SIGRTMAX-13    52) SIGRTMAX-12
53) SIGRTMAX-11    54) SIGRTMAX-10    55) SIGRTMAX-9    56) SIGRTMAX-8    57) SIGRTMAX-7
58) SIGRTMAX-6    59) SIGRTMAX-5    60) SIGRTMAX-4    61) SIGRTMAX-3    62) SIGRTMAX-2
63) SIGRTMAX-1    64) SIGRTMAX
```

杀死指定用户所有进程

```
#kill -9 $(ps -ef | grep hnlinux) //方法一 过滤出hnlinux用户进程 
#kill -u hnlinux //方法二
```

##### nice程序优先级

通常可以通过 Nice 值来达到一定的优先级调整，Nice 就是上述中的 NI 值

此外，必须要注意，nice 值范围

- nice 值范围是 -20~19
- root 可随意调整自己或他人进程的 Nice 值，且范围为 -20~19
- 一般使用者仅可调整自己进程的 Nice 值，且范围仅为 0~19（避免一般用户抢占系统资源）
- 一般使用者仅可将 nice 值越调越高；比如 nice 为 5，则未来仅能调整到大于 5；

那么调整 nice 值有两种方式：

- 一开始执行程序就立即给予一个特定的 nice 值：用 nice 指令
- 调整某个已经存在的 PID 的 nice 值：用 renice 指令

**nice指令设置初始值**

```sh
nice [-n 数字] command

-n：后面接一个数值，数值范围 -20~19

```

```sh
# 范例 1： 用 root 给一个 nice 值为 -5，用于执行 vim，并观察该进程
[root@study ~]# nice -n -5 vim &
[2] 30185
[root@study ~]# ps -l
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0  8985  7780  0  80   0 - 57972 do_wai pts/0    00:00:00 su
4 S     0  9051  8985  0  90  10 - 29118 do_wai pts/0    00:00:00 bash
4 T     0 30185  9051  0  85   5 - 10791 do_sig pts/0    00:00:00 vim
0 R     0 30652  9051  0  90  10 - 12407 -      pts/0    00:00:00 ps
# 原本的 bash PRI 为 90，所以 vim 预设为 90，这里给予 nice -5，所以最终 PRI 变成了 85
# PRI越低越优先
# 要注意：不一定正好变成 85，因为会动态调整的


```

renice对已存在的进程nice重新调整

```sh
renice [number] PID
```

```sh
# 范例 1：找出自己的 bash PID ,并将该 PID 的 nice 调整到 -5
[root@study ~]# ps -l
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0  3426  3372  0  80   0 - 58072 do_wai pts/1    00:00:00 su
4 S     0  3443  3426  0  80   0 - 29059 do_wai pts/1    00:00:00 bash
0 R     0  3487  3443  0  80   0 - 12407 -      pts/1    00:00:00 ps
[root@study ~]# renice -5 3443
3443 (process ID) old priority 0, new priority -5
[root@study ~]# ps -l
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
4 S     0  3426  3372  0  80   0 - 58072 do_wai pts/1    00:00:00 su
4 S     0  3443  3426  0  75  -5 - 29059 do_wai pts/1    00:00:00 bash
0 R     0  3493  3443  0  75  -5 - 12407 -      pts/1    00:00:00 ps

```

#### 系统资源的观察

##### free查看内存使用情况

```sh

free [-b|-k|-m|-g|-h] [-t] [-s N -c N]

选项与参数：
	-b：单位参数；默认是用 k，其他单位对应 bytes、Mbytes、Kbytes、Gbytes
	-t: 输出的最终结果，显示物理内存与 swap 的总量
	-s：可以让系统每几秒输出一次，不间断输出；
	-c：与 -s 同时处理，让 free 列出几次

```

```sh

# 范例 1：显示目前系统的内存容量
[root@study ~]# free -m
#			  总内存		已使用		   剩余							  可用
              total        used        free      shared  buff/cache   available
Mem:           7631         713        6374          15         542        6671
Swap:          4095           0        4095


```

##### uname查看系统核心信息

```sh
uname [-asrmpi]

选项与参数：
	-a：所有系统相关的，都列出来
	-s：系统核心名称
	-r：核心的版本
	-m：本系统的硬件名称，例如 i686 或 x86_64
	-p：CPU 的类型，与 -m 类似
	-i：硬件的平台（ix86）

```

```sh
[root@localhost /]# uname -a
Linux localhost.localdomain 3.10.0-1160.el7.x86_64 #1 SMP Mon Oct 19 16:18:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

##### uptime观察系统启动时间与工作负载

```sh
[root@study ~]# uptime 
 17:31:46 up 43 min,  2 users,  load average: 0.00, 0.01, 0.05
 # 当前时间	 已开机多久  几个用户登录	平均负载：1、5、15 分钟的平均负载

```

##### netstat追踪网络或插槽文件

首先安装以下工具

```sh
 yum install net-tools -y
```



```sh
netstat -[atunlp]

选项与参数：
	-a：将目前系统上所有的联机、监听、Socket 数据都列出来
	-t：列出 tcp 网络封包的数据
	-u：列出 udp 网络封包的数据
	-n：不以进程的服务名称，以端口号来显示
	-l：列出目前正在网络监听的（listen）的服务
	-p：列出该网络服务的进程 PID

```

```sh
# 范例 1：列出目前系统上已经建立的网络连接与 unix socket 状态
[root@study ~]# netstat 
Active Internet connections (w/o servers)		# 与网络相关部分
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0     36 study.centos.mrcode:ssh 192.168.4.170:50821     ESTABLISHED
Active UNIX domain sockets (w/o servers)	# 与本机的进程自己的相关性（非网络）
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    12644    /run/systemd/shutdownd
unix  3      [ ]         DGRAM                    7618     /run/systemd/notify
unix  2      [ ]         DGRAM                    7620     /run/systemd/cgroups-agent
unix  5      [ ]         DGRAM                    7634     /run/systemd/journal/socket


```

网络联机部分：

- Proto：网络封包协议，主要分为 TCP 与 UDP。
- Recv-Q：非由用户程序连接到此 socket 的复制和总 Bytes 数
- Send-Q：非由远程主机传送过来的 acknowledged 总 Bytes 数
- Local Address：本地端的 Ip:port
- Foreign Address：远程主机的 IP:port
- State：联机状态，主要有建立（ESTABLISED）、监听（LISTEN）

##### vmstat侦测系统资源变化

vmstat 可以侦测 CPU、内存、磁盘输入输出状态等信息。

```sh
vmstat [-a] [延迟 [总计侦测次数]]		# CPU/内存等信息
vmstat [-fs]										 # 内存相关
vmstat [-S 单位]									# 设置显示数据的单位
vmstat [-d]											 # 与磁盘有关
vmstat [-p 分区槽]								 # 与磁盘有关

选项与参数：
	-a：使用 inactive/active（是否活跃）取代 buffer/cache 的内存输出信息
	-f：开机到目前为止，系统复制（fork）的进程数
	-s：将一些事件（开机到目前为止）导致的内存变化情况列表说明
	-S：后面可以接单位，例如 k、M 等
	-d：列出磁盘的读写总量统计表
	-p：后面列出分区槽，可显示该分区槽的读写总量统计表

```



```sh
# 范例 1：统计目前主机 CPU 状态，每秒一次，总共 3 次
[root@study ~]# vmstat 1 3
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
 2  0      0 450296   2116 346828    0    0   501    36  181  320  2  3 95  0  0
 0  0      0 450156   2116 346860    0    0     0     0  163  223  2  3 95  0  0
 0  0      0 450156   2116 346860    0    0     0     0  273  388  3  5 91  0  0

# 范例 2：系统上面所有的磁盘读写状态
[root@study ~]# vmstat -d
disk- ------------reads------------ ------------writes----------- -----IO------
       total merged sectors      ms  total merged sectors      ms    cur    sec
sda     7640      1  709893    6377   2486    351   54323    8478      0      5
sdb      116      0    5384      27      0      0       0       0      0      0
sr0        0      0       0       0      0      0       0       0      0      0
dm-0    7072      0  661717    6054   2611      0   45902   10871      0      5
dm-1      88      0    4408      21      0      0       0       0      0      0
dm-2     103      0   10834      58     23      0    4325      56      0      0

```





#### 特殊文件与进程

##### SUID权限

在 Linux 中，所有账号的密码记录在 /etc/shadow 这个文件中，并且只有 root 可以读写入这个文件：

```sh
[root@localhost /]# ll /etc/shadow
-rw-r--r--. 1 root root 3468 2月  28 21:03 /etc/shadow

```

但如果tester用户想要修改自己的密码，就需要修改shadow，那么他并没有对文件的修改权限，他是怎么做到的呢

这就是使用了SUID

```sh
[root@localhost /]# ll /usr/bin/passwd
-rwsr-xr-x. 1 root root 27856 4月   1 2020 /usr/bin/passwd

```

上图红框中的权限信息有些奇怪，owner 的信息为 rws 而不是 rwx。当 s 出现在文件拥有者的 x 权限上时，就被称为 SETUID BITS 或 SETUID ，其特点如下：

- SUID 权限仅对二进制可执行文件有效
- 如果执行者对于该二进制可执行文件具有 x 的权限，执行者将具有该文件的所有者的权限
- 本权限仅在执行该二进制可执行文件的过程中有效

下面我们来看 tester 用户是如何利用 SUID 权限完成密码修改的：

1. tester 用户对于 /usr/bin/passwd 这个程序具有执行权限，因此可以执行 passwd 程序
2. passwd 程序的所有者为 root
3. tester 用户执行 passwd 程序的过程中会暂时获得 root 权限
4. 因此 tester 用户在执行 passwd 程序的过程中可以修改 /etc/shadow 文件

但是如果由 tester 用户执行 cat 命令去读取 /etc/shadow 文件确是不行的：

![img](https://img2018.cnblogs.com/blog/952033/201809/952033-20180915173920406-1945058595.png)

原因很清楚，tester 用户没有读 /etc/shadow 文件的权限，同时 cat 程序也没有被设置 SUID。我们可以通过下图来理解这两种情况：



![SUID](D:\Linux\我的博客\SUID.png)

如果想要用户可以通过`cat`命令执行这个文件，就给他设置一个SUID权限就可以了

```sh
sudo chmod 4755 /bin/cat
```

但这样做很不安全，所以我们还是将权限移除比较好，移除的命令是

```sh
sudo chmod 755 /bin/cat
```



### 计划任务

让系统定时去做某件事情

优势：  解放人力  提升效率  自动化

#### crontab

```sh
crontab [-u username] [-l | -e | -r]

选项与参数：
	-u：只有 root 才能进行该任务，帮其他使用者建立/移除 crontab 工作排程
	-e：编辑 crontab 的工作内容
	-l：查询 crontab 的工作内容
	-r：移除所有的 crontab 的工作内容，若只删除一项，则使用 -e 编辑

```

实例

```sh
# 范例 1：假如你女朋友生日是 5.2，要在 5.1 23:59 发一封信给她，这封信的内容已经写在 /home/mrcode/lover.txt 中了
crontab -e
59 23 1 5 * mail kiki < /home/mrcode/lover.txt

# 范例 2：每 5 分钟执行一次  `/home/mrcode/test.sh`
*/5 * * * * sh /home/mrcode/test.sh

```



系统配置文件/etc/crontab

```sh
[root@localhost lianxi]# cat /etc/crontab
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed

```

存放计划任务的目录：`/var/spool/cron/`

可以通过看日志文件` /var/log/cron`来知道计划任务是否执行

crond服务每隔一分钟去查看有什么事情需要做

`service crond status`  可以查看crond的状态 

`ps aux | grep crond`   查看进程是否存在

`service crond stop`   停止crond服务



任何一个用户是否都可以创建计划任务,普通用户可以创建计划任务  但是普通用户不能进入/var/spool/cron/ 文件中,而且需要注意的是用户即使不登陆系统，计划任务仍然会执行。

那么如果黑客在我们电脑中添加了自动执行木马的程序，我们要如何找出来呢？

- 进入/var/spool/cron/ 文件中查看

- 去以下目录中查看

  -  cron.daily/

  - cron.hourly/

  - cron.monthly/

  - cron.weekly/

    这些目录都是Linux中每天/每月/每小时会执行一次的脚本文件目录

如果crond挂了如何告知管理员

编写一个脚本  每隔1秒钟执行一次  检测crond是否正常运行   如果没有正常运行就在屏幕输出  crond is dowm

```shell
#!/bin/bash

while true
do
if service crond status &>/dev/null ;then

        echo "crond is up"
else
        echo "crond is down"
        service crond start && echo "now crond is up"
fi
sleep 1
done

```

