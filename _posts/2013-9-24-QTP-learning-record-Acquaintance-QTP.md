---

layout : post

category : manage

tags : [自动化测试，QTP]

title : QTP学习记录--初识QTP

---

为什么选择自动化测试？
快速 
QuickTest 执行测试比人工测试速度快多了。
可靠
QuickTest 每一次的测试都可以正确的执行相同的动作， 可以避免 人工测试的错误。
可重复
QuickTest 可以重复执行相同的测试。
可程序化
QuickTest 可以以程序的方式， 撰写复杂的测试脚本， 以带出隐藏在应用程序中的信息。
广泛性
QuickTest 可以建立广泛的测试脚本，涵盖应用程序的所有功能
可再使用
QuickTest 可以重复使用测试脚本，即使应用程序的使用接口已经改变。
QTP的工原理
简要说明：获取hwnd，然后判断ui属性，逐个判断，然后逐层递归，最后获取每个对象的所有层面的属性，跟对象库里的属性进行比较，匹配则应用，不匹配则智能识别
详细说明：把对象从被测软件ui中读取出主要特征，存入对象库，回放时在被测试软件中寻找指定对象，赋予对象一些方法，方法为windows win32或者web上的一些activex控件的通用方法（或者javascrīpt应用于一些未支持的事件，比如link.click）， 微软控件对外的接口，把其中一些方法进行封装，成为qtp自己的方法，比如getroproperty=对象。object.value ，然后运用这些方法属性驱动被测试对象完成一些指定的动作。对于任何一个add-in都是先找到人家的对外接口，然后拿过来封装，需要的时候去调用接口事件，也就成为了QTP的动作。 
QTP的工作流程
录制测试脚本前的准备
在测试前需要确认你的应用程序及 QuickTest 是否符合测试需求?
确认你已经知道如何对应用程序进行测试， 如要测试哪些功能、 操作步骤、 预期结 果等
同时也要检查一下 QuickTest 的设定，如 Test Settings 以及 Options 对话窗口， 以确 保 QuickTest 会正确的录制并储存信息。确认 QuickTest 以何种模式储存信息。
录制测试脚本
操作应用程序或浏览网站时，QuickTest 会在 Key word  View  中以表格的方式显示 录制的操作步骤。每一个操作步骤都是使用者在录制时的操作， 如在网站上点击了链接， 或则在文本框中输入的信息。
加强测试脚本
在测试脚本中加入检查点，可以检查网页的链接、对象属性、或者字符串，以验证 应用程序的功能是否正确
将录制的固定值以参数取代， 使用多组的数据测试程序。 使用逻辑或者条件判断式， 可以进行更复杂的测试。
对测试脚本进行调试
修改过测试脚本后， 需要对测试脚本作调试， 以确保测试脚本能正常并且流畅的执 行。
在新版应用程序或者网站上执行测试脚本
通过执行测试脚本，QuickT est 会在新本的网站或者应用程序上执行测试，检查应 用程序的功能是否正确
分析测试结果
分析测试结果，找出问题所在。
测试报告
安装了 T estDirector （Qualit y  Center ） ，则 你可以将发现的问 题回报到 T estDirector（Qualit y  Center）数据库中。TestDirector（Qualit y Center）是 Mercury 测试 管理工具。
认识QTP操作界面
解一下 QuickT est 的主界面。下图是录制了一个操作后 QuickT est 的界面。

![](http://pic.yupoo.com/charisma999_v/Dbzp8Hpx/CE4Xz.png "QTP主界面")
   
QTP 界面包含标题栏、菜单栏、文件工具条等几个界面元素，下面简单解释各界面 元素的功能

![](http://pic.yupoo.com/charisma999_v/Dbzp8bv1/bNLfV.png "QTP标题栏")

标题栏，显示了当前打开的测试脚本的名称
菜单栏，包含了 QuickTest 的所有菜单命令项。
文件工具条，在工具条上包含了以下几个按钮：
调试工具条
测试工具条，包含了在创建、管理测试脚本是要使用的按钮

![](http://pic.yupoo.com/charisma999_v/Dbzp8bv1/bNLfV.png "QTP测试条")

调试工具条，包含在调试测试脚本时要使用的工具条

![](http://pic.yupoo.com/charisma999_v/Dbzp7PST/N9DRC.png "QTP测试条1")

测试脚本管理窗口，提供了两个可切换的窗口，分别通过图形化方式和 VBScript脚本方式来管理测试脚本
Data Table 窗口，用于参数化你的测试
状态栏，显示测试过程中的状态
