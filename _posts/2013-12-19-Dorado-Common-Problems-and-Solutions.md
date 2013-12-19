---

layout : post

category : Dorado

tags : [开发，Dorado,Java中间插件]

title : Dorado常见问题及解决方法

---

哎！从兴奋中走出来就是一堆的问题，都不知道怎么解决，我就是这样，折腾了一天才搞好，现在把我遇到的问题给记下来，免得下次碰到了 还是不知道怎么解决
1、更新dorado配置规则是遇到的几个问题，很是蛋疼，关键是搞好了这个，别的问题也出来了，而且用这个插件，在建相关的文件时，还非得要更新规则配置文件。
不然就不让你新建，这点我就纳闷了。
（1） Initializing dorado engine...
 * [vendor: www.BSTEK.com]
 * [dorado home: and]
 * Loading configure from [com/bstek/dorado/web/configure.properties]...
 * Loading configure from [home:configure.properties]...
Exception in thread "main" java.io.IOException: Can not found resource [home:configure.properties].
at com.bstek.dorado.idesupport.StandaloneRuleSetExporter.loadConfigureProperties(StandaloneRuleSetExporter.java:135)
at com.bstek.dorado.idesupport.StandaloneRuleSetExporter.exportRuleSet(StandaloneRuleSetExporter.java:196)
at com.bstek.dorado.idesupport.StandaloneRuleSetExporter.main(StandaloneRuleSetExporter.java:266)
搭好环境，点击更新规则配置，啪.....出现上面的一段代码，最后上网找资料啊，找啊找！找到了说是dorado的核心包出现版本问题
没什么好说的，果断上官网啦最新的核心包，把原先的同名包给替换掉，就OK拉 
（2）
还有就是 提示找不到HttpServletRequest类。这个问题很容易看出来，连我“英国联系”不是很懂的人都能看懂，相信大家都看的懂
规则文件更新的时候需要调用servlet-api.jar相关的类，如果您的系统环境下无法找到这个jar,就会报如上的错误。
解决的办法是在项目的Java Build Path中添加servlet-api.jar。
下面是直接将当前环境中的Tomcat7添加到Java Build Path中(由于Tomcat7环境中已经自动包含servlet-api,因此就无需再单独添加servlet-api.jar了):
在Java Build Path中添加Servlet-API相关的jar,例如本例打开工程的属性页，并找到Java Build Path:
把相关的包放进去，点击“finish”就OK拉 
（3）
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'dorado.idesupport.robotRegister$child#1' 
defined in class path resource [com/bstek/dorado/idesupport/context.xml]: 
Invocation of init method failed; nested exception is java.lang.IllegalArgumentException: Robot "datatype-reflection" already exists.
这个错误是说在这个以前有一个包，现在由于升级删掉了，在我的项目中依然用到了，要删除，才行，
好吧！无语加无语.....
没办法删把，谁让咱们要用人家的东西呢？是吧！直接删除项目中的dorado-idesupport-XXX.jar，再更新规则就可以成功执行
（4）
Exception in thread "main" java.lang.NoSuchMethodError: com.bstek.dorado.idesupport.template.PropertyTemplate.setHighlight(I)V
    at com.bstek.dorado.jdbc.ide.AbstractDbColumnRuleTemplateInitializer.initRuleTemplate(AbstractDbColumnRuleTemplateInitializer.java:59)
    at com.bstek.dorado.idesupport.RuleTemplateBuilder.processInitializer(RuleTemplateBuilder.java:216)
    at com.bstek.dorado.idesupport.RuleTemplateBuilder.initRuleTemplate(RuleTemplateBuilder.java:194)
    at com.bstek.dorado.idesupport.RuleTemplateBuilder.ruleTemplateAdded(RuleTemplateBuilder.java:240)
    at com.bstek.dorado.idesupport.RuleTemplateManager.addRuleTemplate(RuleTemplateManager.java:47)
这个不解释，听官网的解释说是由于IDE的升级重构导致：如果项目中包含dorado-jdbc-1.0.0版本以下的jar包，如：dorado-jdbc-0.1-BETA.jar，
执行规则文件更新的时候会出现如上的错误。
解决的办法是：删除dorado-jdbc-0.1-BETA.jar。再更新规则文件就可以成功执行。
（5）
在更新完规则配置之后，这下以为没事了把，O(∩_∩)O~，别高兴太早，问题来了，假设我建一个HelloWorld.touch.xml这个文件，一路“next”下去，好，问题来了
建好了，也可以打开视图界面，但是我想在vime里方一个button按钮是，在视图怎么找都找不到，这就奇了怪了啊，最后没办法只有上网找啊！
找到一条解释说，由于dorado的核心包dorado-core-7.2.0.jar这个包，需要升级到dorado-core-7.3.0.jar以及更高版本，二话不说，去吧，到官网下
了最新的dorado-core-7.3.0.jar，替换同名jar包，在刷新，OK，我们千年等一回的button回来了。

嘿嘿》。。这些问题或许对老鸟来说是不算什么，但是对于我们这些菜鸟来说，就是但问题啊，所以我把这些问题记录下来，以免下次在出现这样的问题不知道怎么解决

随着我的深入学习，其中遇到的问题肯定会很多，这个会继续更新



















