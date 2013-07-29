---

layout : post

category : manage

tags : [selenium]

title : selenium操作手册之一

---


Selenium_前期知识准备 

 
在开始selenium之前，总得知道selenium是做啥的，环境大致需要些什么软件，如何进行的测试。



关于selenium的相关背景知识，推荐文档：Selenium私房菜（新手入门教程）.pdf

下载：http://download.csdn.net/detail/testingba/3811306


XPath教程.pdf 是讲解对象引用的常见方法xpath的，差不多翻翻看得懂就行，反正firefox有插件firebug，可以即时看看对象的xpath。自己编写xpath基本上不会遇到。

下载：http://download.csdn.net/detail/testingba/3811337


Selenium 中文API.doc 这个是参考手册，留在手边用作参考吧，还是中文版的，比较难得。

下载：http://download.csdn.net/detail/testingba/3811354

手把手教你selenium_搭建环境_软件下载 
1.	打开firefox
打开seleniumIDE进行脚本录制和回放，调试的时候可能需要firebug插件查看页面中的对象；
2． 生成junit4的java代码后，导入eclipse的java工程中，启动seleniumRC，然后直接运行回放脚本。
假设读者和我一样是全面空白状态，那就需要下载的文件清单：
1． firefox
2． seleniumIDE
3． firebug
4． SeleniumRC
5． Selenium Client Drivers
6． JDK1.6
7． Eclipse
8． JUNIT4

Selenium相关介质下载：
1. 下载firefox：
http://www.firefox.com.cn/download/
下载得到文件：Firefox-latest.exe
2. 下载seleniumIDE
http://seleniumhq.org/projects/ide/
选择download的TAB页
下载 seleniumIDE1.4.1，下载文件为：selenium-ide-1.4.1.xpi
3. 下载安装firebug
下一篇文章讲解环境的搭建
4. 下载SeleniumRC
http://seleniumhq.org/projects/ide/
选择download的TAB页
下载<Selenium Server (formerly the Selenium RC Server)>的2.12.0，下载文件为：selenium-server-standalone-2[1].12.0.jar
5. 下载Selenium Client Drivers
http://seleniumhq.org/projects/ide/
选择download的TAB页
获取selenium-java-client-driver.jar，用于java 语言的Selenium 开发
<Java 2.12.0 2011-11-10 Download>
下载文件为：selenium-java-2[1].12.0.zip，解压为：selenium-2.12.0，里面包含selenium-java-2.12.0.jar。
selenium帮助文档：http://selenium.googlecode.com/svn/trunk/docs/api/java/index.html
6. 下载JDK1.6
Jdk下载可以到官网：
http://www.java.net/download/jdk6/6u10/promoted/b32/binaries/jdk-6u10-rc2-bin-b32-windows-i586-p-12_sep_2008.exe
我自己是用的：jdk1.6.0_18
7. 下载eclipse
下载eclipse：
http://www.eclipse.org/downloads/
Eclipse Classic 3.7.1, 174 MB，我本机是xp系统的，所以下载的是32bit的版本
8. 下载JUNIT4
通常下载安装eclipse的时候会带上junit，没必要单独去下载junit，
下载：http://sourceforge.net/projects/junit/files/junit/4.10/junit-4.10.jar/download
下载文件名为：junit-4.10.jar
