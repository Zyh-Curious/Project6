# 6：Linux的使用

## Task1

安装成功

![image-20261002125533083](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261002125533083.png)

Linux发行版：

大致了解了一下，所谓Linux发行版其实是由内核、软件包管理器以及桌面环境或工具三部分组成。其中，内核由Linus来写，其上由各家厂商和社区打包不同软件，形成不同发行版。

主流分类如下：

1、Debain系（刚才我装的Ubuntu就属于这个）

Debain:非常稳定，但软件版本偏旧。由社区驱动，完全开源，很适合用于服务器，但缺点是没法直接装新工具。

Ubuntu:热门，桌面友好，适合新手来开发虚拟机、搞服务器。

Linux Mint:基于Ubuntu，有着轻量的桌面。

2、RedHat 系

RHEL:企业商用还收费

CentOS Stream:免费的社区版

Fedora:前沿版本，软件新

3、Arch系

ArchLinux:软件永远最新，但需要自己配置

Manjaro:一种简化版本，自带桌面，上手简单

（还有一些轻量版本就不赘述了）

![Linux_Distribution_Timeline](C:\Users\LENOVO\Downloads\Linux_Distribution_Timeline.svg)

三种网络连接模式的区别：

1、桥接模式：虚拟机直接接入物理网络，相当于一台主机，适用于与外界进行完全交互的场景

2、NAT模式：虚拟机能通过主机的IP访问外部网络，限制了外部网络访问虚拟机，使用于需要访问互联网但不需要被外部设备访问的场景

3、仅主机模式：该模式下，虚拟机与主机之间建立起一个与外界隔离的网络，虚拟机能访问其他同一模式的虚拟机，但无法直接访问互联网，适用于需要隔离测试环境或模拟内部网络的情况

（所以我选择了NAT模式）

## Task2(以下命令是直接在final shell上执行的)

目录结构：

bin：提供一些基础可执行命令

sbin：提供一些管理命令

boot：系统的启动文件

dev：设备文件，有鼠标、键盘等信息

etc：配置文件，有用户账号、系统配置

home：用户家目录，用来放用户自己的文件

lib及lib64：系统依赖的共享库，就像windows的dll文件

media：系统连接的u盘及其他外部设备

mnt：自己加硬盘可能会用

opt：一些可选大型软件，比如某些版本的jdk

proc：就是内存中的信息

root：管理员的家目录，和用户、Home实现隔离

run：运行时的临时数据（就是结束后的垃圾文件，不过会自动清空）

srv：服务器数据，还有网站、ftp服务数据

tmp：顾名思义，临时文件目录

usr：系统资源，非常重要的文件夹

var：动态变化的数据，就是常说的数据库、缓存

这是命令：

![image-20261003130932751](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261003130932751.png)

这是结果：

![屏幕截图 2026-10-03 130856](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 130856.png)

txt文件相关任务：

![image-20261003140829898](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261003140829898.png)

（让豆包帮我整理了一份速查表:））

![](D:\git\project6\258bee5019b0af10800f38e7646fe120_720.png)

![bef89d011e61344789fe92fb37c8b540_720](D:\git\project6\bef89d011e61344789fe92fb37c8b540_720.png)

## Task3

关键步骤：

![屏幕截图 2026-10-03 142127](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 142127.png)

![屏幕截图 2026-10-03 142132](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 142132.png)

![屏幕截图 2026-10-03 142225](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 142225.png)

vim相关命令：

![bf09299cc63dedb97a1fb3e68427c24a](D:\git\project6\bf09299cc63dedb97a1fb3e68427c24a.png)

## Task4

IP地址：

每一台联网的电脑都有一个IP地址，用于和其他计算机的通信

它分为v4,v6两种

它的格式为：a.b.c.d(其中a,b,c,d为0~255之间的整数)

还有两个特殊IP：

127.0.0.1专用来表示本机

0.0.0.0可以表示本机，可以在端口中表示绑定关系，也可以在IP限制中表示任意IP

端口：

IP地址能让本机锁定其他计算机，端口则能让本机进一步锁定某个程序。或者说，程序通过暴露端口来在计算机之间传递信息

![image-20261003143538985](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20261003143538985.png)

远程连接可以脱离虚拟机进行操作，能大幅提高工作效率

## Task5

root用户拥有最大的权限，不像普通用户一样处处受限

用户组即用户的分组，一个系统可以配置很多用户，每个用户又可以加入很多组

相关命令如下：

创建用户：groupadd [-p -d] 用户名

删除用户：groupdel [-r] 用户名

切换组：usermod -aG 用户名 用户组

注：这三个命令只有root才能执行

-p表示组，-r表示home路径，默认在Home下

-r表示删除home路径

关于root，由于其权限最大，它对整个系统都有影响，所以它的危害也最大，它的错误会对整个系统造成破坏，故在现在的很多管理模式中，用户的权限会受到限制，并以此来对系统更好地进行管理

权限修改截图：

![屏幕截图 2026-10-03 154448](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 154448.png)

![屏幕截图 2026-10-03 154532](C:\Users\LENOVO\Desktop\Screenshots\屏幕截图 2026-10-03 154532.png)