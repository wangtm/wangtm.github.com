---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP学习笔记二

---



QTP学习笔记二



一.测试目的:

在软件系统联调的过程中，子系统B担当了提供核算数据的任务，所以对子系统B的操作很多是重复的步骤，并且B所提供的数据需要十分准确，所以采用自动化测试来解决这个问题。

二.处理方法:
　　1.采用顺序录制方式，不涉及其他调用
　　2.采用"Analog Recording"录制模式与常规录制模式结合的方法

三.总结:
　　1.缩短了执行时间，每个脚本平均运行时间为1分钟
　　2.减少数据录入错误

四.学习到的内容:
　　1.设置action的属性
　　将action的属性设置为"Reusable action"后，该action可被其他action或其他脚本调用
　　2.VBS脚本中"do… …until"循环的使用
　　例如循环两次
　　Dim m
　　M=0
　　Do until m=2
　　Runaction"01_01",oneIteraction
　　M=m+1
　　Loop
　　3.VBS脚本中"for nest"循环的使用
　　例如循环执行10次
　　Dim i
　　I=0
　　For i=0 to 9 step 1
　　… …
　　I=i+1
　　Next
















































































    
			
	
