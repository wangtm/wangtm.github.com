---

layout : post

category : manage

tags : [selenium，自动化，自动化测试配置文件 ]

title : selenium自动化测试配置文件

---

首先建一个名称为“config.properties”的文件

然后在文件里配置录制一个脚本经常要用到的设置。比如：登录名和密码之类的

##登录名和密码
UserName=abc
UserPassword=123

##需要测试的网址
如：
URL=www.baidu.com
或
http://127.0.0.1/xxxx/xxxx.html


##选择需要启动的浏览器
FireFoxBrowser= *FireFox (这里加上你本地FireFox的安装路径)
googlechrome = *chrome (这里加上你本地FireFox的安装路径)

##然后设置启动时间
##default指的是立即执行  也可以设置在某个时间内执行

lanuchtime=default
或
lanuchtime=2013-7-20 20:30:20

##配置delenium  server的地址及端口
lauchserver=localhost
lauchport = 4444

##配置控制脚本的执行时间
waitTimeShort = 1000
waitTimeMedium = 5000
waitTimeLong = 100000

这些都设置好，然后在使用的时候  可以直接导入使用，
这样就省去了没录制一个脚本然后在编译的时候还要每次做些重复的设置