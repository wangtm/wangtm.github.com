---

layout : post

category : 项目管理

tags : [SVN入门及配置使用  ]

title : SVN入门及配置使用

---

(转)SVN入门及配置使用

SVN，即Subversion，是一个自由开源的版本控制系统，可以将数据恢复到早期版本，或者检查数据修改的历史，这些数据可以是源代码，也可以是其他类型的文件。
在SVN出现之前，CVS是开源世界版本控制工具的事实标准，然而CVS存在一些固有的缺陷，并且修复这些缺陷需要耗费很大的精力，因此，SVN的发起者Brian Behlendorf和CollabNet决定重新编写一个版本控制系统，保留CVS的基本思想，但要修正其中错误和不合理的特性。于是，SVN作为CVS的继任者出现了。SVN的设计者们力图通过两方面的努力赢得CVS用户的青睐：保持开源系统的设计以及界面风格与CVS尽可能类似，同时尽力弥补CVS许多显著的缺陷。这些努力的结果使得从CVS迁移到SVN不需要作出重大的变革，因此越来越多的人选择了SVN。 
http://svnbook.red-bean.com
http://www.subversion.org.cn 

目录

一、客户端的使用
　1.1 Linux系统下一般使用（Ubuntu）
　1.2 Windows系统下一般使用
　1.3 Linux下使用SVN+ssh认证（未找到相关资料@_@）
　1.4 Windows下使用SVN+ssh认证
二、服务器端的配置
　2.1 Linux下的svnserve配置
　2.2 Windows下的svnserve配置
　2.3 Linux下的svnserve+ssh配置
　2.4 Windows下的svnserve+ssh配置（需使用Cygwin，略）
　2.5 Linux下基于APache的SVN服务器配置
　2.6 Windows下基于APache的SVN服务器配置
三、建立版本库
　3.1 Linux下创建版本库
　3.2 Windows下创建版本库
大多数人都是从客户端开始使用SVN，以下先介绍客户端的使用。假设已经假设好了SVN服务器，其文件夹地址为http://domain/svn/trunk/myproject，用户名为test，密码为test。（如果服务器端配置的是SVN，则使用svn://开头的URL访问；如果服务器端配置的是SVN+SSH，则使用svn+ssh开头的URL访问）
一、客户端的使用
1.1 Linux（Ubuntu）系统下一般使用
1）首先需要安装svn客户端，ubuntu下使用$sudo apt-get install subversion（其他请baigoogledu，余同）
2）checkeout命令：第一次使用时使用checkout命令，把服务器的目录拷贝到本地的当前目录下，同时会建立一个隐藏文件夹记录版本信息：
　　[工作目录]$svn checkout "http://domain/svn/trunk/myproject" --username test
然后输入密码
3）svn update命令：获取服务器上的最新版本
　　[工作目录]$svn update（除了第一次要加url和用户名和密码，之后系统会记住）
4）svn add命令：要把非版本控制的本地文件添加到版本控制：
　　[工作目录]$svn add hello.c
5）svn commit命令：把本地文件上传到服务器
[工作目录]$svn commit（如果有新的文件，要首先svn add）
1.2 Windows系统下一般使用
1）安装客户端：http://tortoisesvn.net/downloads
2）新建一个文件夹（工作目录），右击选择checkout，填写URL和用户名密码
3）工作目录右键update
4）工作目录右键add
5）工作目录右键commit
1.3 Linux下使用SVN+ssh认证（未找到相关资料@_@）
1.4 Windows下使用SVN+ssh认证
（参考ubuntu下架设svn服务器及在windows建立svn+ssh客户）
1.4.0 安装TortoiseSVN、Puttygen、Pageant
　　http://sourceforge.net/projects/tortoisesvn
　　http://www.chiark.greenend.org.uk/~sgtatham/putty/
1.4.1 转换私钥格式
　1）将Linux下的文件<username>key拷贝到windows下，运行Puttygen；
    2）选择菜单conversions->Import Key；选择文件<username>key，提示"Enter passphrase for key"，输入创建公私钥对示使用的passphrase关键字;
    3）选择Parameters为“SSH-2 DSA”或“SSH-2 RSA”->Save private key->保存文件名为username>key.ppk。
1.4.2 建立TortoiseSVN与Pageant的关联，并将私钥加入Pageant：
    1）鼠标右键选择TortoiseSVN->Settings->Network->SSH client，输入：
    　C:\Program Files\TortoiseSVN\bin\TortoisePlink.exe
    2）鼠标右键选择TortoiseSVN->RepoBrowser 输入URL：
　　svn+ssh://<username>@<SvnServiceIP>/usr/local/svn/trunk
    3）运行Pageant，右键点击屏幕右下角的图标-〉Add Key，将私钥文件<username>key.ppk加入。
——如果不想缓存ssh密码，则第8、9步不需要，只保留第二步，但每次check out、check in中每进入一个文件夹都要输入两次密码，烦死你:)
二、服务器端的配置
Web服务器部署可以有三种选择，配置由简单到复杂排列为
·svnserve
·svnserve over SSH
·Apache+mod_dav_svn模块
下面从最简单的入手，介绍svnserve。
[更新]Windows下服务器端的配置可以使用VisualSVN Server进行傻瓜化安装。
官方网站：http://www.visualsvn.com/
参考链接：VisualSVN系列介绍（有详细的安装过程介绍，这里就不转述了）
2.1&2.2 配置svnserve
svnserve是一个轻型的服务器，可以同客户端通过在TCP/IP基础上的自定义有状态协议通讯，客户端通过使用开头为svn://或者svn+ssh://svnserve的URL来访问一个svnserve服务器。
2.1 Linux下的svnserve配置
2.1.0 同样地，使用命令$sudo apt-get install subversion
2.1.1 svnserve作为独立守护进程，监听请求
　　$svnserve -d
　　$ #svnserve is now running, listening on port 3690
　　——可以使用--listen-port=[端口号]来指定端口，或者--listen-host=[主机名]来指定主机名
　　假定已经建立一个版本库位于/usr/local/repositories/project路径（版本库的建立稍后提及）， 此时客户端可以使用svn://[主机]/usr/local/repositories/project来进行访问
　　——可以使用-r选项来限制只输出指定路径下的版本库，从而使客户端访问更为简洁：
　　$svnserve -d -r /usr/local/repositories
　　则客户端只要使用svn://[主机]/project就可以访问
2.1.2 通过inetd使用svnserve
　　$svnserve -i
　　——此时svnserve会尝试使用自定义协议通过stdin和stdout来与subversion客户端通话，默认端口为3690。可以在/etc/services添加如下几行：
　　svn 3690/tcp #subversion
　　svn 3690/udp #subversion
　　——如果是使用经典的类Unix的inetd守护进程，可以在/etc/inetd.conf添加如下行，则如果有客户连接来到端口3690，inetd会产生一个svnserve进程来做服务
　　svn stream tcp nowait svnowner /usr/bin/svnserve svnserve -i
2.1.3 设置svnserve的内置认证