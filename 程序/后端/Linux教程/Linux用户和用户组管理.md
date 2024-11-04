# 三、与用户账号有关的系统文件

完成用户管理的工作有许多种方法，但是每一种方法实际上都是对有关系统文件进行修改。与用户和用户组相关的信息都存放在一些系统文件中，这些文件包括 /etc/passwd, /etc/shadow, /etc/group 等。
## 1. /etc/passwd 文件是用户管理工作涉及的最重要的一个文件

Linux系统中每个用户都在 /etc/passwd 文件中有一个对应的记录行，它记录了这个用户的一些基本属性。这个文件对所有用户都是可读的。
```
＃ cat /etc/passwd

root:x:0:0:Superuser:/:
daemon:x:1:1:System daemons:/etc:
bin:x:2:2:Owner of system commands:/bin:
sys:x:3:3:Owner of system files:/usr/sys:
adm:x:4:4:System accounting:/usr/adm:
uucp:x:5:5:UUCP administrator:/usr/lib/uucp:
auth:x:7:21:Authentication administrator:/tcb/files/auth:
cron:x:9:16:Cron daemon:/usr/spool/cron:
listen:x:37:4:Network daemon:/usr/net/nls:
lp:x:71:18:Printer administrator:/usr/spool/lp:
sam:x:200:50:Sam san:/home/sam:/bin/sh
```
从上面例子可以看到，/etc/passwd 中一行记录对应着一个用户，每行记录又被（:）分隔为7个字段，其具体含义如下：
```
用户名：口令：用户标识号：组标识号：注释性描述：主目录：登录shell
```
1. **用户名：** 代表用户账号的字符串
2. **口令：** 一些系统中，存放着加密后的用户口令字
3. **用户标识号：** 一个整数，系统内部用它来标识用户
4. **组标识号：** 字段记录的是用户所属的用户组
5. **注释性描述：** 记录着用户的一些个人情况
6. **主目录：** 用户的起始工作目录
7. **登录shell：** 用户登录后，要启动一个进程，负责将用户的操作传给内核，这个进程是用户登录到系统后运行的命令解释器后某个特定的程序，即Shell
8. **伪用户：** 这些用户在 /etc/passwd 中也占有一条记录，但不能登录。他们的存在主要是方便系统管理，满足相应的系统进程对文件属主的要求
```
常见的伪用户
bin 拥有可执行的用户命令文件
sys 拥有系统文件
adm 拥有账户文件
uucp UUCP使用
lp lp或lpd子系统使用
nobody NFS使用
```