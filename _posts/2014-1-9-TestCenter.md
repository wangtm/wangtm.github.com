---

layout : post

category : manage

tags : [TestCenter   BUG缺陷管理工具 ]

title : BUG缺陷管理工具

---

    前段时间写了很多的自动化测试方面的东西，总感觉对测试出来的BUG缺少个集中管理的工具，要是有一个工具就好了，而是在网上搜了很多，
各有各的好处，各有各的缺点，有的是太笨重有的就是需要收费，反正我试了几款，没用几天就卸载了，最后找了一款"TestCenter"我试了一下
，感觉里面有的功能能满足我的需求，不是很笨重，有免费的，下面我就来介绍一下该工具的安装及配置。

	首先安装就不用多介绍了，在Win下的都是傻瓜试的，一路”next“，最后点击”finsh“就OK了。在安装这个之前需要安装一个JDK，并配置一下将JDK环境。JDK配置的方法如下：

右键点击我的电脑“属性”，选择“高级”。

‚点击环境变量。

在（admin用户名）的用户变量中新建变量。

变量名：JAVA_HOME

变量值：C：\Program Files\Java\jdk1.6.0_12 即JDK所安装的路径

变量名:  PATH

变量值：C：\Program Files\Java\jdk1.6.0_12\bin即JDK所安装下bin的路径

变量名：CLASSPATH

变量值：C：\Program Files\Java\jdk1.6.0_12\lib即JDK所安装下lib包的路径

如图：


安装完成后，双击桌面“运行TestCenter”图标进入TestCenter。进入该系统，然后你就可以该干嘛就干吗了 

软件的卸载TestCenter时,程序会根据用户选择来卸载。

       a.卸载TestCenter MYSQL

              1>程序会完全删除TestCenter数据库及服务,包括里面的数据。

              2>程序不会删除用户原有的MYSQL数据库及服务,不会影响用户数据库中的数据。

       b.不卸载TestCenter MYSQL

              1>程序会删除TestCenter程序体,不会删除TestCenter MYSQL数据库及服务，不会影响数据库中的数据。  

这个将的比较简单，接下来我会介绍里面的一些常用的功能点做一下介绍，如怎么建立测试计划，建立测试需求等等


