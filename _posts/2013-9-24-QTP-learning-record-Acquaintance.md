---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP学习记录--录制/执行测试脚本

---


QTP学习记录--录制/执行测试脚本
    当浏览网站或使用应用程序时，
QuickT est 会纪录你的操作步骤，
并产生测试脚本。停止录制后，
会看到 QuickT est 在 Keyword View 
中以表格的方式显示测试脚本的操作步骤。
        录制前的准备
            在录制脚本前，首先要确认以下几项
            已经在 Mercur y Tours 示范网站上注册了一个新的使用者账号。
            在正式开始录制一个测试之前，关闭所有已经打开的 IE 窗口。这是为了能够正常 的进行录制，这一点要特别注意。
            关闭所有与测试不相关的程序窗口。
        录制测试脚本
            录制测试脚本
                1．执行 QuickT est 并开启一个全新的测试脚本
                    开启 QuickTest，在“Add-in Manager”窗口中选择“Web”选项，点击“OK”，关闭“Add-in Manager”窗口，进入 QuickTest Professional  主窗口
                    如 果 QuickTest  Professional  已经 启 动 ， 检查 “ Help>About  QuickT est  Professional”查看前加载了那些 add-ins。如果没有加载“W eb” ，那么必须 关闭并重新启动 QuickT est   Professional，然后在“Add-in  Manager”窗口中选 择“Web” 。
                    如果在执行 QuickT est  Professional 时没有开“Add-in  Manager ”则点击 “T ool>Opti ons” ，在“General”标签页勾选  “Display  Add-in  Manager  on  Startup” ，在下次执行 QuickTest Professi onal  时就会看到 “Add-in Manager” 窗 口

![](http://pic.yupoo.com/charisma999_v/DbzYkmeA/medium.jpg "20130924151228-配置1")

                2．开始录制测试脚本
                    选中 “T est>Record” 或者点选工具栏上的 “Record” 按钮。 打开 “Record and Run Settings”对话窗口：如图

![](http://pic.yupoo.com/charisma999_v/DbzYkCDh/medium.jpg "20130924151228-配置2")

                    在“Web”标签页选择“Open the followi ng browser when a record  or run session begins”
                    在 “Ty pe” 下拉列表中选择 “Microsoft Internet Expl orer” 为浏览器的类型； 在 “Address”
                    中添加 “http://newtours.mercuryinteracti ve.com/ （网站地址） ”   这样，在录制的时候， QuickT est <http://newtours.mercuryinteracti>
                    会自动打开 IE 浏览器并连接到 Mercur y Tours  范例网站上。现在我们在切换到“Windows Applicati on”  标签页，如图
                3．登录 Mercur y Tours  网站
                    在用户名和密码输入注册时使用的账号和密码，点击“Sign-in” ，进入“Flight Finder”网页。
                4．输入订票数据
                    输入以下订票数据：
                        Departing  From：New Y ork
                        On：May 14
                        Arriving In：San  Francisco
                        Returning：May 28
                        Service Class：Business class
                        其他字段保留默认值，点击“CONTINUE”按钮打开“Select Fli ght”页面。
                5．选择飞机航班
                    可以保存默认值，点击“CONTINUE”按钮打开“Booka  Fli ght”页面。
                6．输入必填字段（红色字段）
                    输入用户名和信用卡号码（信用卡可以输入虚构的号码，如 8888-123456） 。
                    点击网页下方的“SECURE PURCHASE”按钮，打开“Flight Confirmation”网页。
                7．完成定制流程
                    查看订票数据，并选择“BACK TO HOME”回到 Mercury Tours 网站首页。
                8．停止录制
                    在 QuickTest 工具列上点击“Stop”按钮，停止录制。
                9．保存脚本
                    选择“File>Save”或者电机工具栏上的“Save”按钮，开“Save”对话窗口。选择的路径，填写文件名，我们取名为 Fli ght。点击“保存”按钮进行保存
            分析录制的测试脚本
                QuickTest 会在测试脚本管理窗口 （也叫 Tree View 窗口） 中产生对每一个操作的相应记录。并在 Keyword  View 中以类似 Excel 工作表的方式显示所录制的测试脚本。当录制结束后，QuickTest 也就记录下了测试过程中的所有操作。测试脚本管理窗口显示的内容如下图所示：

![](http://pic.yupoo.com/charisma999_v/DbzYkVox/medium.jpg "20130924151228-配置3")

                每个字段的意思
                    Item：
                        以阶层式的图标表示这个操作步骤所作用的组件（测试对象、工具对象、函数呼叫或脚本） 。
                    Operation：
                        要在这个作用到的组件上执行的动作，如点击、选择等
                    V alue：
                        执行动作的参数，例如当鼠标点击一张图片时是用左键还是右键
                    Assignment：
                        使用到的变量
                    Comment：
                        你在测试脚本中加入的批注
                    Document ation：
                        自动产生用来描述此操作步骤的英文说明。
                针对一些常见的操作步骤作详细说明
                    如图：

![](http://pic.yupoo.com/charisma999_v/DbzXXURb/medium.jpg "20130924151228-配置4")

        执行测试脚本
            1．打开录制的 Flight 测试脚本
            2．设置运行选项。点击“T ool>Opti ons”打开设置选项对话框，选择“Run”标签页，如下图：

![](http://pic.yupoo.com/charisma999_v/DbzXYdcN/medium.jpg "20130924151228-配置5")

            3．在工具条上点击“Run”按钮，打开“Run”对话框：如图：

![](http://pic.yupoo.com/charisma999_v/DbzYm4Xy/medium.jpg "20130924151228-配置6")

            4.点击“OK”按钮开始执行测试。
        分析测试结果
            在测试执行完成后，QuickT est 会自动显示测试结果窗口，如下图所示

![](http://pic.yupoo.com/charisma999_v/DbzYmVxY/medium.jpg "20130924151228-配置7")

            测试结果窗口中分二个部分显示测试执行的结果
                左边显示 Test results tree，以阶层图标的方式显示测试脚本所执行的步骤。可以选择“+”检查每一个步骤，所有的执行步骤都会以图示的方式显示
                右边则是显示测试结果的详细信息
            在 树视 图 中 展 开 “ Flight  Iteration  1(Row  1)>Action1  Summary >Welcome  MercuryTours>Finda Flight:  Mercury>” ，选择“  ＂fromPost＂：Select  ＂New Y ork＂  ” 。

![](http://pic.yupoo.com/charisma999_v/DbzYjtME/medium.jpg "20130924151228-配置8")

            测试结果窗口中显示三个部分
                左边是 Test results tree： 展开树视图后， 显示了测试执行过程中的每一个操作步骤
                右上方是 Test  results  detail：对应当前选中的测试步骤
                右下方是 Active Screen： 对应当前选中的测试步骤， 显示该操作执行时应用程序的屏幕截图。
