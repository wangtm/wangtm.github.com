---

layout : post

category : manage

tags : [常用软件测试工具之比较和汇总]

title : 常用软件测试工具之比较和汇总

---

源文件下载：https://drive.google.com/?usp=chrome_app#my-drive

常用软件测试工具之比较和汇总
    压力测试工具
        LoadRunner
            下载地址：http://www8.hp.com/us/en/software/enterprise-software.html
            特点
                a，支持的协议多且个别协议支持的版本比较高
                b，负载压力测试方案设置灵活
                c，丰富的资源监控
                d，报告可以导出到Word、Excel以及HTML格式。
            缺点
                只能录制通过本机的通讯内容
                函数支持相对弱一些
                定制灵活性差一些
                采集数据含义不够明确和通用
                	运行脚本效率较差
                结果不易保存，处理速度较慢
        QALoad 
            官方下载地址：http://www.compuware.com/
            特点
                (1).测试接口多
                (2)可预测系统性能
                (3)通过重复测试寻找瓶颈问题；
                (4)从控制中心管理全局负载测试
                (5)可验证应用的扩展性；
                6)快速 创建仿真的负载测试；
                (7)性能价格比较高
            缺点
                1、购买成本高
                2、需要专门的技术人员
        Benchmark Factory
            下载地址：http://xiazai.zol.com.cn/detail/27/264123.shtml#down
            特点
                首先它可以测试服务器群集的性能
                以实施基准测试
                可以生成高级脚本
            缺点
                待补....
        JMeter
            下载地址：http://jmeter.cn.uptodown.com/
            特点
                是一个专门为运行和服务器负载测试而设计、100%的纯Java桌面运行程序
                原先它是为Web/HTTP测试而设计的，但是它已经扩展以支持各种各样的 测试模块
                它和HTTP和SQL(使用JDBC)的模块一起运行
                它可以用来测试静止或活动资料库中的服务器运行情况，可以用来模拟服务器或网络系统在重 负载下的运行情况
                它也提供了一个可替换的界面用来定制数据显示，测试同步及测试的创建和执行
            缺点
                使用Jmeter无法验证JS程序，也无法验证页面，所以需要手工去验证。  
                Jmeter的断言功能不是很强大  
                Jmeter脚本的维护需要保存为本地文件，而每个脚本文件只能保存一个测试用例，不利于脚本的维护。  
        WAS
            下载地址：http://download.csdn.net/detail/knowweb/2567457
            特点
                是Micro$oft提供的免费的Web负载压力测试工具，应用广泛
                WAS可以通过一台或者多台客户机模拟大量用户的活动
                WAS支持身份验证、加密和Cookies
                也能够模拟各种浏览器和Modem速度
                它的功能和性能可以与数万美元的产品媲美
            缺点
                根据先前的请求所传回的结果来修改 url 参数的功能 
                 执行或模拟用户端逻辑的功能  
                指定测试期间固定的测试週期数的功能  
                使用不同 ip 位址或网域名称同时执行多重 web 伺服器测试的功能
        OpenSTA
            下载地址：http://www.51testing.com/html/90/n-242990.html
            特点
                OpenST的特点是可以模拟很多用户来访问需要测试的网站，它是一个功能强大、自定义设置功能完备的软件
                这些设置大 部分需要通过Script来完成，因此在真正使用这个软件之前，必须学习好它的Script编写
                如果需要完成很复杂的功能，Script的要求还比较 高
                其较为丰富的图形化测试结果大大提高了测试报告的可阅读性。 
            缺点
                待补....
    测试管理工具
           TestDirector
            ：http://www.cntesting.com/bbs/read.php?tid=3961：下载地址
            特点
                B/S构架模式；Windows平台；.可以定制流程
                可以定制查询；可以定制功能域
                可以定制用户角色，可以定制角色权限
                可Email通知；可以生产各种报表；支持多种数据库；可以与其他MI公司测试工具集成；安装配置较为简单，有可优化的工作流
            缺点
                价格太贵
                除与微软的Aclearcase/" target="_blank" >ccess接口比较好，其他数据库接口不是太完善
                没有中文版（虽然有破解汉化版）
                缺少角色可视窗口配置，版本更新，但功能没有改进
        Mantis
            下载地址：http://www.duote.com/soft/31166.html
            特点
                不收费，B/S构架模式；Windows平台
                可邮件通知，操作较为灵活
            缺点
                安装配置复杂，不收费的东西，界面也不够美观
                有很多功能根本只是架子，没法真正使用
        Bugzero
            下载地址：http://www.cncrk.com/downinfo/41162.html
            特点
                国产软件
                B/s 版本
            缺点
                安装配置比较复杂，需要单独安装java和tomcat
                页面出现乱码，通过在线试用，流程不太清晰，界面不够客户
    功能测试工具
        WinRunner
            下载地址：http://down.51cto.com/tag-WinRunner.html
            特点
                企业级的功能测试工具，用于检测应用程序是否能够达到预期的功能及正常运行
                自动执行重复任务并优化测试工作，从而缩短测试时间
                通过自动录制、检测和回防用户的应用操作，从而提高测试效率。
            缺点
                WR的对象管理不如QTP那么有效 
                WR的语言主要是基于类C的TSL,是Mercury发明的语言, 在学习上会有一定难度 
                WR的稳定性不行,而且无意人为的干扰可能导致回放的失败 
                应用程序中控件的位置是固定的，不能随着窗口或分辨率的变化而变化； 一个窗口中不能有两个同类的控件位置相同;部分控件还是不能识别  
        Functional Tester
            下载地址：http://www.ibm.com/developerworks/cn/downloads/r/rft/
            特点
                 它是Robot的Java实现版本，在Rational被IBM收购后发布的
                在Java的浪潮下，Robot被移植到了Eclipse平台，并完全支持 Java和.net
                可以使用VB.net和Java进行脚本的编写，当然了录下脚本让后做做修改是最爽的事情了。
                由于支持Java，那么对测试脚本进行 测试也变成了可能
            缺点
                待补.......
        Rational Robot
            下载地址：http://ishare.iask.sina.com.cn/f/18242096.html
            特点
                对于Visual studio 6编写的程序支持的非常好
                同时还支持Java Applet、HTML、Oracle Forms、People Tools应用程序的支持
                要支持Delphi程序的测试还必须下载插件
                Rational Robot的语法使用Basic语法，它的语言使用SQABasic。
            缺点
                脚本的维护性
                效率问题
                界面识别问题
        selenium
            下载地址：http://docs.seleniumhq.org/download/
            特点
                测试脚本非常简单，可以用IDE录制脚本，然后转换为java语言。
                Selenium是基于js执行的，可以在脚本中执行JavaScript。所以在编写脚本时，有些Extjs特有的组件或dom对象不能定位时，可以在脚本中写js代码实现。比如设置ComboBox的值，选中Grid中的某一行等。
                用Selenium进行浏览器兼容性测试比较容易。只需要一套脚本，就可以在不同的浏览器中运行。
            缺点
                每次运行都要开启一个浏览器，运行效率比较低。尤其是做并发测试时，比较麻烦。跑50个用例，就要开启50个浏览器窗口。
                并发测试时，在同一个机器商运行多个测试用例会共享session。这是一个比较令人头疼的问题。比如我用不同的用户跑两个登录的测试，第一个测试用例还未结束，运行第二个测试用例，这时第二个用户的登录session会覆盖前面用户的session。
                不够健壮
    测试辅助工具
        SmartDraw 
            用于绘制UCML，进行负载压力测试需求分析。对压力测试测试前的工作很有帮助。
        SDemo
            可以将操作录成EXE文件，并回放出来。这样就避免了那些偶尔才出现的Bug！
