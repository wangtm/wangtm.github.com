---

layout : post

category : manage

tags : [MyEclipse6.5下struts2+spring2+hibernate3 整合 ]

title : MyEclipse6.5下struts2+spring2+hibernate3 整合

---

ssh开发，想用ssh框架开发当然先的搭建开发平台，我用的相关软件版本如下：

1、MyEclipse6.5

2、struts2.0.11.2,现在官方网站上的最高版本为Struts2.1.6,我之所以没有用最新版本是因为最新版本在网上的资料少一些，万一出问题解决起来有难度，网上能够咨询的地方也不多。下面的版本没有用最新也是基于这个道理。下载地址:http://www.apache.org

3、spring2.5.5,最新版为2.5.6,下载地址为http://www.springsource.org/download

4、hibernate3.2 最新版为3.3.2,下载地址为https://www.hibernate.org

     软件准备好了就可以开始搭建环境了,由于是新学习,因此没有使用myeclipse提供的自动引入spring和hibernate支持。

1、在myeclipse6.5下新建一个web project项目

2、先来引入struts2的支持：把下载回来的struts2的压缩包解开，把解压目录下lib目录下的struts-core-2.0.11.2.jar,xwork-2.0.5.jar,freemarker-2.3.8.jar,ognl-2.6.11.jar,struts2-spring-plugin-2.0.11.2.jar五个jar文件拷贝到刚才新建项目的WebRoot\WEB-INF\lib目录下。

3、引入spring2支持：把spring解压目录下dist下的spring.jar拷贝到WebRoot\WEB-INF\lib目录下

4、hibernate3支持：把hibernate解压目录下的hibernate3.jar复制到WebRoot\WEB-INF\lib目录下。

5、一些基础支持的引入：如日志、数据库驱动（我用的是mysql数据库，所以引入的是mysql数据库支持包）、连接池、以及一些基础的公用的支持包，这些包都能在struts2、spring、hibernate解压目录下找到，有些包三个目录下都有，我一般找版本比较高的。具体的包名如下：c3p0-0.9.1.2.jar , dom4j-1.6.1.jar , commons-collection.jar , commons-dbcp.jar , commons-io.jar, commons-pool.jar, jta.jar , cglib-nodep-2.1.3.jar , mysql-connector-java-5.0.8.jar , commons-logging.jar.

注:以上只是必须基础的包,真正开发不会只有这些包,我的原则是需要了再加,而不是一开始把所有的包都放进去.

     接下来要做的是配置工作了

1、配置web.xml,web.xml文件内容如下：

<?xml version="1.0" encoding="UTF-8"?>
<web-app version="2.5"
xmlns="http://java.sun.com/xml/ns/javaee"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
<!-- 配置struts2的拦截器（过滤器） -->
  <filter>
       <filter-name>struts2</filter-name>
       <filter-class>org.apache.struts2.dispatcher.FilterDispatcher</filter-class>
  </filter>

<filter-mapping>
      <filter-name>struts2</filter-name>
       <url-pattern>/*</url-pattern>
</filter-mapping>


<!--配置spring的监听器-->
<listener>
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
</web-app>


2、在src目录下建立struts.xml，也可直接从其他地方复制一个。内容如下：

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE struts PUBLIC
    "-//Apache Software Foundation//DTD Struts Configuration 2.0//EN"
    "http://struts.apache.org/dtds/struts-2.0.dtd">

<struts>

<!--指定字符集-->

<constant name="struts.i18n.encoding" value="UTF-8"></constant>

<package name="struts2" extends="struts-default">



<!--这个action用于测试配置是否正确，没有实际用处-->
     <action name="testAction" class="testAction">

            <result name="success">/test.jsp</result>

     </action>

</package>
</struts>



3、配置applicationContext.xml,在WEB-INF下建立此文件,或从其他地方复制,内容如下

<?xml version="1.0" encoding="UTF-8"?>
<!--
  - Middle tier application context definition for the image database.
  -->
<beans xmlns="http://www.springframework.org/schema/beans"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xmlns:context="http://www.springframework.org/schema/context"
  xmlns:tx="http://www.springframework.org/schema/tx"
  xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-2.5.xsd
    http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context-2.5.xsd
    http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx-2.5.xsd">

<!-- Configurer that replaces ${...} placeholders with values from a properties file -->
<!-- (in this case, JDBC-related settings for the dataSource definition below) -->

<bean id="testAction" class="com.test.action.Test">

</bean>
</beans>



4、在scr目录下建立com.test.action包并在该包下建立Test.java,内容如下

package com.test.action;

import com.opensymphony.xwork2.ActionSupport;

public class Test extends ActionSupport {
@Override
public String execute() throws Exception {
  return SUCCESS;
}

}

5、在webroot目录下建立test.jsp文件,内容如下：

<%@ page language="java" import="java.util.*" pageEncoding="ISO-8859-1"%>
<%
String path = request.getContextPath();
String basePath = request.getScheme()+"://"+request.getServerName()+":"+request.getServerPort()+path+"/";
%>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
  <head>
    <base href="<%=basePath%>">
   
    <title>My JSP 'test.jsp' starting page</title>
<meta http-equiv="pragma" content="no-cache">
<meta http-equiv="cache-control" content="no-cache">
<meta http-equiv="expires" content="0">   
<meta http-equiv="keywords" content="keyword1,keyword2,keyword3">
<meta http-equiv="description" content="This is my page">
<!--
<link rel="stylesheet" type="text/css" href="styles.css">
-->
  </head>
 
  <body>
   这是一个测试 <br>
  </body>
</html>


5、配置tomcat在tomcat的server.xml的host标签内加入  <Context path="/test" docBase="D:\test\WebRoot"  reloadable="true" />



6、在myeclipse 中启动tomcat后在浏览器地址栏中输入http://localhost:8080/test/testAction.action　如果能够正确地显示“这是一个测试”就表示大功告成了，接下来就可以做一些实际的工作了。 


 
