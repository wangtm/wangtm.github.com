---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP学习笔记

---



QTP学习笔记一


一.测试目的:在测试过程中，需要使用"模拟器"来产生测试需要的数据，因为需要统计软件的数据准确率，所以每次使用的数据都是相同的，这样会产生一定的重复工作量，并且手工产生数据会有一定出错的机率，所以使用自动化测试工具录制脚本，每次执行测试之前运行该脚本可使用保证测试速度和数据的准确程度。

二.录制模式和方法:因为暂时没有安装.net插件，所以脚本采用"analog模式"录制。测试需要用到的数据分为A1、A2两大类，每个大类的数据又分为16小类，A1采用action调用的方式进行录制，A2采用顺序录制方式。

三.Action调用的操作方法:
　　分别在多个脚本中完成子类数据的action录制，而后集成到action_A1中，在QTP界面insert call to copy of Action from test:脚本名称action:需要调用的action?location:After the current step
　　注:在涉及action调用的情况下进行action copy不能连同它所调用的action一块拷贝过来，它所调用的action需要另外添加。

四.总结
　　1.增加新action的时候，如果采用"After the current step"方式，可使脚本的步骤层次分明，但是这种录制方式在调用的action级数较多时，修改会非常的麻烦，删除其中的一个action会连同它的子action一起被删掉。
　　2.采用"At the end of the test"方式可避免上述问题，但是录次不是很分明。在软件达到一定规模的情况下，建议两种增加action的交替使用，增加脚本的可用性。
　　五.学习到的内容
　　1.插入等待时间
　　Wait 秒,毫秒
　　例如:wait 10 等待10秒
　　Wait 0,200 等待200毫秒
　　2.添加新action
　　Inserit?call to new action
　　3.在本脚本中实现action调用
　　Insert?call to existiong action
　　4.添加新步骤
　　Insert?new step
　　5.执行当前action
　　Automation?run current ation
　　6.从当前步骤执行
　　Automation run current step
　　7.逐步调试运行
　　Debug?step into
　　8.设置运行脚本的模式
　　Tools--options run选项卡
　　9.设置运营脚本时的各项数据
　　File settings run选项卡 超时等待，发生错误时是否退出执行并弹出提示，出错时是否保存image信息等。



















































































    
			
	
