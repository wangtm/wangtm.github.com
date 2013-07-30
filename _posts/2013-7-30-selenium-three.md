---

layout : post

category : manage

tags : [selenium]

title : selenium操作手册连载三

---


5. Selenium Client Drivers使用

Eclipse中建立java工程后，引用selenium-java-2.12.0.jar
6. JDK1.6
Jdk1.6我没有使用安装版本，直接拷贝后，设置环境变量：
我的电脑—属性—高级—环境变量—创建环境变量JAVA_HOME，修改PATH
例子：
PATH=$PATH;%JAVA_HOME%\bin
JAVA_HOME=C:\jdk1.6.0_18
测试环境变量设置是否生效：
任意路径下输入：java –version
返回：
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build1.6.0_15-b03)
Java HotSpot(TM) Client VM (build 14.1-b02,mixed mode, sharing)
7. eclipse
配置好JDK就可以了，绿色版本不用安装
8. JUNIT4
Eclipse中建立java工程后，还需要引用junit-4.10.jar
整个环境搭建好了，下一篇文章就讲讲如何完成一个selenium的测试回放流程。
