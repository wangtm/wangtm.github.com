---

layout : post

category : Dorado

tags : [开发，Dorado,Java中间插件]

title : Dorado入门之HelloWord

---

今天在网上找资料的时候 看到好久没用的Dorado啦，当时心中小小的兴奋了一下，因为这个跟eclipse结合起来用，开发就真的简单，就像开发.asp一样拖控件，图形界面的。
下面先来看看一下效果图（见证奇迹的时刻O(∩_∩)O~）

![](http://charisma.u.qiniudn.com/2013-12-17QQ%E6%88%AA%E5%9B%BE20131217160230.png "示例图")

图的基本功能：打开这个页面的时候显示一个按钮，按钮单击可以出现一个"Hello World!"的信息提示框

这一个范例非常简单，但是我们可以从中总结出5点知识点，可以看到Dorado的神奇之处。
(1)可以没有JSP--通过dorado的视图文件(View)我们不仅可以定义控件也可以定义布局;
(2)页面访问URL与视图文件View的对应关系
(3)视图中view节点的title属性的含义
(4)按钮对象的基本使用
(5)了解MessageBox的基本用法

我们注意看一下这个范例是没有JSP的,它的全部信息都定义在一个com/bstek/dorado/sample/basic/HelloWorld.view.xml的xml文件中，
在dorado开发中我们称它为视图配置文件，也叫View在dorado的视图配置文件中我们不仅可以定义页面中所包含的控件，也可以方便的
定义控件之间的布局(dorado提供了专门的布局管理器以及控件本身也可以是容器，控件之间可以有父子关系，因此较容易定义布局)。
下面我们来看一下源文件(HelloWorld.view.xml)
<?xml version="1.0" encoding="UTF-8"?>
<ViewConfig>
  <Arguments/>
  <Context/>
  <Model/>
  <View layout="padding:20">
    <Property name="title">HelloWorld</Property>
    <Button id="button1">
      <Property name="caption">Greeting from Dorado7 ...</Property>
    </Button>
  </View>
</ViewConfig>
可能这样直接看原始代码比较费劲，我们可以利用dorado的IDE查看和编辑这个XML文件,找到sample-center中com/bstek/dorado/sample/basic
目录下的HelloWorld.view.xml文件,并用Dorado7 View Editor模式打开,可以看到:
如图，上面一大推的代码，在下面的界面中之有一行代码(也就一个标题而已)。

![](http://charisma.u.qiniudn.com/2013-12-17QQ%E6%88%AA%E5%9B%BE20131217162340.png "示例图")


我们当前目录下的HelloWorld.js控制器，在其中可以看到button1绑定的onClick事件：代码非常简单：
// @Bind #button1.onClick
!function() {
    dorado.MessageBox.alert("Hello World!");
}
该处利用dorado的MessageBox弹出一个Hello World!的提示。
把这个能够做出来，那说明你已经入门了，恭喜...O(∩_∩)O哈哈~
























