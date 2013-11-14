---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP学习记录--QTP入门篇之参数化

---



QTP-自动化测试.参数化
   使用  QuickT est  可以通过将固定值替换为参数，扩展基本测试或组件的范围。该过程
（称为参数化）大大提高了测试或组件的功能和灵活性。
   可在  QuickT est  中使用参数功能，通过参数化测试或组件所使用的值来增强测试或组
件。参数是一种从外部数据源或生成器赋值的变量。
QuickTest 可以参数化测试或组件中的步骤和检查点中的值。还可以参数化操作参数的
值。

1 参数化步骤和检查点中的值
    录制或编辑测试或组件时， 可以参数化步骤和检查点中的值。 可以参数化选定步骤的对
象属性的值。还可以参数化为该步骤定义的操作（方法或函数参数）的值。

1.1  参数化对象和检查点的属性值

可以在“对象属性”或 “对象库”对话框中参数化对象的一个或多个属性的值。可以在
“检查点属性”对话框中参数化检查点的一个或多个属性的值。
采用下列方式可以打开“对象属性”对话框或“检查点属性”对话框：
n  选择“步骤”  >  “对象属性” ，或者右键单击某个步骤并选择“对象属性” 。将打
开“对象属性”对话框。
n  选择“工具”  >  “对象库” ，单击“对象库”工具栏按钮，或者右键单击包含该
对象的操作或组件，然后选择“对象库” 。将打开“对象库”对话框。
n  选择“步骤”  >  “检查点属性” ，或者右键单击该检查点并选择“检查点属性” 。
然后在对话框的“配置值”区域中选择参数然后在对话框的“配置值”区域中选择参数
如图

![](http://charisma.u.qiniudn.com/201310-41.png "参数属性")

1.2  参数化操作的值
如果步骤中使用的方法或函数具有参数， 则可以根据需要参数化该参数值。 例如，如果
操作使用  Click方法，则可以参数化x参数、y 参数或这两者的值。
在关键字视图中选择已参数化的值时， 将显示该参数类型的图标。 例如， 在以下片段中，
已将Set  方法的值定义为随机数字参数。每次运行测试或组件时，QuickTest  都会在
creditnumber编辑框中输入一个随机数字值。
如图

![](http://charisma.u.qiniudn.com/201310-42.png "参数属性")

可以使用视图中的“值” 列中的参数化图标来参数化操作值。
单击参数化图标 ，打开“值配置选项”对话框，将显示当前定义的值
如图

![](http://charisma.u.qiniudn.com/201310-43.png "参数属性")

选择“参数” 。如果该值已经参数化，则“参数”部分将显示该值的当前参数定义。如
果该值尚未参数化，则“参数”部分将显示该值的默认参数定义。单击“确定”接受显示的
参数语句并关闭该对话框。



    
			
	