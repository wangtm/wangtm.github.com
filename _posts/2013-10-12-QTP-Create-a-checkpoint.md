---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP学习记录--QTP入门篇之创建检查点

---



QTP-自动化测试.建立检查点
    设置检查点的作用？
        “检查点” 是将指定属性的当前值与该属性的期望值进行比较的验证点， 这能够确定网 站或应用程序是否正常运行
    QuickT est 检查点种类
         QuickTest 支持检查点类型 
            类型：标准检查点 
                说明：检查对象的属性 
                    实例：检查某个按钮是否被选取
            类型：图片检查点 
                说明：检查图片的属性
                    实例：检查图片的来源文件是否是 正确的
            类型：表格检查点
                说明：检查表格的内容 
                    实例：检查表格内的内容是否是正 确对的
            类型：网页检查点
                说明：检查网页的属性 
                    实例：检查表格内的内容是否是正 确对的
            类型：文字/文字区域检查点
                说明：检查网页上或是窗口上出现 的文字是否正确
                    实例：检查登陆系统后时候出行登 陆成功的文字
            类型：图像检查点 
                说明：提取网页和窗口的画面检查 画面是否正确
                    实例：检查网页或者网页的一部分 是否如期显示
            类型：数据库检查点 
                说明：检查数据库的内容时候正确 
                    实例：检查数据库查询的值是否正 确
            类型：XML 检查点 
                说明：检查 XML 文件的内容 
                    实例：XML 检测点有两种—XML 文件检测点和 XML  应用检 测点。XML 文件检测点用于 检查一个 XML 文件；XML  应 用检 测 点用 于 检 查一 个 Web 页面的 XML 文档。
    创建检查点
        这里我们打开按照前面两章做的一个简单的测试脚本为例
        首先我们打开 Flight 测试脚本，将脚本另存为“Checkpoint”测试脚本
            然后我们在 Checkpoint 测试 脚本中创建 4 个检查点，分别是：对象检查、网页检查、文字检查以及表格检查。
         对测试 脚本创建 4 个检查点为例
            对象检查
                首先在 Checkpoint 测试脚本上添加一个标准检查点， 这个检查点用以检查旅客的姓氏。 创建标准检查点：
                    1、打开 Checkpoint 测试脚本
                    2、选择要建立检查点的网页
                        在 QuickTest 的 视 图 树 中 展 开 “ Action1>Welcome:  Mercury  Tours>Book  a  Flight:
                        Mercur y  ” ，由于输入使用者姓氏的测试步骤是  “passFirst0”这个步骤， 所以要选择这个步
                        骤的下一个测试步骤，以便建立检查点（如图所示1）
![](http://charisma.u.qiniudn.com/201310-12%E6%96%87%E5%AD%97%E6%A3%80%E6%9F%A51.png "检查点1")

                    3、建立标准检查点
                        对“Active Screen”中的 First Name  编辑框点击鼠标右键，显示插入选择点的类型。（如图所示2）
						
![](http://charisma.u.qiniudn.com/201310-12%E6%A3%80%E6%9F%A5%E7%82%B92.png "检查点2")
						
                        选择“Insert Standard Checkpoint”选型，显示“Object Selection-Checkpoint Properties”对话窗口：（如图所示3）
						
![](http://charisma.u.qiniudn.com/201310-12%E6%A3%80%E6%9F%A5%E7%82%B93.png "检查点3")		
						
                        确保当前的焦点定位在“W ebEdit: passFirst0”上，点击“OK”按钮，弹出如下的窗口：（如图所示4）
						
![](http://charisma.u.qiniudn.com/201310-12%E6%A3%80%E6%9F%A5%E7%82%B94.png "检查点4")	
					
                        我们对弹出框进行预设定值，点击“OK” 。QuickT est 会在选取的步骤之前建立一个标准检查点。（如图所示5）
						
![](http://charisma.u.qiniudn.com/201310-12%E6%A3%80%E6%9F%A5%E7%82%B95.png "检查点5")	
						
                    4、我们再在工具栏上点击“save”按钮，保存当前修改的脚本
            网页检查
                对于这一步的检查只能使用在网页上，主要作用是检查网页中的连接和图片连接是否和录制下来的是一样
                    1、选择要建立检查点的网页
                        展开 “Action1>W elcome: Mercury  Tours” 选择 “Booka  Fli ght: Mercury” 页面，在 “Acti veScreen”会显示相应的页面。
                    2、建立网页检查点
                        在“Active  Screen”上的任意地方点击鼠标右键，选取“Insert  Standard  Checkpoint” ，开“Object Selecti on-Checkpoint Properties”对话窗口（由于选择的位不同， 对话窗口显示被选取的对象可能不一样） 。（网页检查图1）

![](http://charisma.u.qiniudn.com/201310-12%E7%BD%91%E9%A1%B5%E6%A3%80%E6%9F%A51.png "网页检查")	
						
                        选择最上面的 “Page： Book a Flight: Mercury ” ，并点击 “OK” 按钮确认，将打开“PageCheckpoint Properties”对话框。（网页检查图2）
		
![](http://charisma.u.qiniudn.com/201310-12%E7%BD%91%E9%A1%B5%E6%A3%80%E6%9F%A52.png "网页检查")			
						
                    3、当执行该脚本时，该脚本会自动去检查该网页上的连接和图片链接
                    4、我们再在工具栏上点击“save”按钮，保存当前修改的脚本 
            文字检查
                这里我们还是那前面的那个测试购买飞机票的测试脚本为例
                    这里我们来检查一下在 “Flight Confirmation” 网页中是否出 现“New  York”？
                        1、确定要建立检查点的网页
                            展开“Action1>Welcome: Mercur y Tours”选择“Flight Confirmation: Mercury”页面，在“Active Screen”会显示相应的页面
                        2、建立文字检查点
                            在“Active Screen”中选择在“Departing”下方的“New Y ork” 。对选取的文字按下鼠标右键，并选取“Insert  T ext  Checkpoint”打开“Text  CheckpointProperties”对话窗口。（文字检查图1）
							
![](http://charisma.u.qiniudn.com/201310-12%E6%96%87%E5%AD%97%E6%A3%80%E6%9F%A51.png "文字检查")							
							
                            当 “Checked Text” 出现在下拉式清单中时，在 “Constant” 字段显示的就是选取的文字。这也就是 QuickTest 在执行测试脚本时所要检查的文字。
                        3、点击“OK”关闭窗口。
                            QuickTest 会在测试脚本上加上一个文字检查点，这个文字检查点会出现在“Fli ghtConfirmati on: Mercury”网页下方。
                        4、我们再在工具栏上点击“save”按钮，保存当前修改的脚本  
            表格检查
                我们还是以前面的测试脚本为了来做一个检查“Booka Fli ght: Mercury”网页上航班的价格的表格检查点
                这个检查的作用是检查表格中显示的内容，可以检查指定检查点中显示的指定内容
                    1、选取要建立检查点的网页
                        展开 “Action1>W elcome: Mercury  Tours” 选择 “Booka  Fli ght: Mercury” 页面，在 “Acti veScreen”会显示相应的页面。
                    2、建立表格检查点
                        在“Active  Screen”中，在第一个航班的价钱上“270”上点击鼠标右键，选择“InsertStandard Checkpoint”打开“Object Selecti on-Checkpoint Properties”对话窗口。（表格检查点1）
						
![](http://charisma.u.qiniudn.com/201310-12%E8%A1%A8%E6%A0%BC%E6%A3%80%E6%9F%A51.png "表格检查")						
						
                        刚打开时选取的是 “W ebElement:270” ， 这时要选择上一层的 W ebT able 对象，在这个例子中选择“W ebT able:  New  Y ork  to  San  Francisco” 。点击“OK”打开“Table  CheckpointProperties”对话窗口，显示整个表格的内容。（表格检查点2）
						
![](http://charisma.u.qiniudn.com/201310-12%E8%A1%A8%E6%A0%BC%E6%A3%80%E6%9F%A52.png "表格检查")						
						
                        预设每一个字段都会被选择， 表示所有字段都会检查， 可以对某个字段双击， 取消检查 字段，或者选择整个栏和列，执行选取或取消的动作。 在每个字段的列标题上双击，取消勾选的图标，然后再 270 字段处双击，这样执行时 QuickT est 只会对这个字段值作检查。（表格检查点3）
						
![](http://charisma.u.qiniudn.com/201310-12%E8%A1%A8%E6%A0%BC%E6%A3%80%E6%9F%A53.png "表格检查")						
						
                    3、点击“OK”关闭对话框。
                        QuickTest 会在测试脚本中， “Book a Fl ight: Mercury”页面下加上一个表格检查点
                    4、我们再在工具栏上点击“save”按钮，保存当前修改的脚本   
    上面我们一次建立了四个检查点，我们还没有执行该检测点，不知道能不能用，下面我们就来对这四个检查点一次执行并分析执行脚本后生产的结果
    执行并分析使用检查点的测试脚本
	
        1．在工具栏上点击“Run”按钮，弹出如下窗口：
![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C1.png "运行")

            这个页面是询问将本次测试结果保存在哪个录， 选择 “New run results  fol der” 单选按钮，接受默认设，点击“OK”按钮确认。
			
![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C2.png "运行")			
			
        2．当 QuickT est 执行王测试脚本后，测试执行结果窗口会自动开启。如果所有的检查点都通过了验证， 运行结果为 Passed。如果有一个或多个检查点没有同过验证， 这运行结果显示为 Failed，如下图所示：
        下面我们来验证一下四个检查点
            对象检查
                在 test  results  tree 中展开“Book  a  Flight:  Mercury   >passFirst0” ，并选择“Checkpoint＂passFirst0＂” 。在 “Details” 窗口可以看到标准检查点的详细结果

![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C%E5%AF%B9%E8%B1%A14.png "运行")				
				
            网页检查
                在 test results tree 中展开 “Checkpoint It eration 1  （Row1）   >  Action1 Summar y >Welcome:Mercur y Tours >Booka Flight: Mercury ” ，并选择“Checkpoint＂Booka Flight: Mercury ＂” 。在右边的“Details”窗口中，可以看到网页检查点的详细信息
![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C3.png "运行")
				
				文字检查
                在 test results tree 中展开 “Checkpoint It eration 1  （Row1）   >  Action1 Summar y >Welcome:Mercur y Tours >  Flight Confirmation: Mercury” ，并选择“Checkpoint＂New Y ork＂” 。显示如界面，因为文字检查点的实际值与预期值相同，所以检查点的结果为 Passed。
          			
![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C%E6%96%87%E5%AD%974.png "运行")
			
			  表格检查
                在 test results tree 中展开“Book a  Flight: Mercur y >New  York  to San Francisco  ” ，并选择“Checkpoint＂New  York t o San Francisco＂” 。在“Details”窗口可以看到表格的详细结果
				
![](http://charisma.u.qiniudn.com/201310-12%E8%BF%90%E8%A1%8C%E8%A1%A8%E6%A0%BC4.png "运行")				
				
    我们查看结果分析时可以看到执行通过的会在前面有一个小的“对勾”，没有执行成功的话则出现“红叉”，然后我们可以根据执行的情况来分析和检查我们的脚本
	
	
