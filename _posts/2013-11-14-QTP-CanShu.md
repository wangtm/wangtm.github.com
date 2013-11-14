---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : 参数化测试脚本

---

参数化测试脚本

1  定义参数
1．首先，我们打开 Checkpoint 测试脚本，将脚本另存为“Parameter” ，然后选择要参
数化的文字：在视图树中展开“Action1>Welcome: Mercury Tours>Find  a Flight: Mercur y  ” 。
2．在视图树中选择“f romPort”右边的“V alue”字段，然后再点击参数化图标 ，开
“V alue Configuration Options”对话窗口：
![](http://charisma.u.qiniudn.com/QQ%E6%88%AA%E5%9B%BE20131114.png "检查点1")


3． 设要参数化的属性， 选择 “Parameter” 选择项， 这样就可以用参数值来取代 “New 
Y ork”这个常数了，在参数中选择“Data  Table”选项，这样这个参数就可以从 QuickT est
的 Data Table 中取得，将参数的名字改为“departure” 。
![](http://charisma.u.qiniudn.com/QQ%E6%88%AA%E5%9B%BE20131114160909.png "检查点1")


4．点击“OK”确认，QuickTest 会在 Data  Table 中新增 departure 参数字段，并且插入
了一行 New  Y ork 的值，New Y ork  会成为测试脚本执行使用的第一个值。
![](http://charisma.u.qiniudn.com/2013%E5%8F%82%E6%95%B0%E5%8C%96QQ%E6%88%AA%E5%9B%BE20131114160939.png "检查点1")


参 数化 以 后 可以 看 到 树视 图 中的 变化 ，在 参数 之 前 ， 这 个 测试步骤 显 示
“foomPost …Select… New Y ork” ，现在，这个步骤变成了“f oomPost …Select… Data Table
（＂departure＂，dt GlobalSheet） ” 。而且当点击 V alue 字段时，V alue 字段会显示如图所示：
，表示此测试步骤已经被参数化，而且其值从 Data  T able 中的 departure 字
段中获得。
5．在 departure  字段中加入出发点资料，使 QuickT est 可以使用这些资料执行脚本。
在 depart ure 字段的第二行，第三行分别输入：Portland、Seattle。
6．保存测试脚本。




2  修正受到参数化影响的步骤

修正文字检查点，首先在树视图中，展开“Action1>Welcome:  Mercur y   T ours>Fli ght 
Confirmati on: Mercury” 页面， 然后点击鼠标右键， 选择 “Checkpoint Properties” ， 打开 “T ext 
Checkpoint Properties”对话窗口：
![](http://charisma.u.qiniudn.com/20131114161046.png "检查点1")



在“Checked  Text”的 Constant 字段中显示为“New  Y ork” ，表示测试脚本在每次执行
时， 这个文字检查点的预期值都为 “New Y ork” 。 我们选择 Parameter， 点击旁边的 “Parameter 
Options”按钮 ，打开“Parameter Opti ons”对话窗口：
![](http://charisma.u.qiniudn.com/20131114161124.png "检查点1")



在参数类型选择框选择“Data  Table”选项，在名字选择框选择“departure”选项，指
明这个文字检查点使用 depart ure 字段中的值当成检查点的预期值。
点击“OK”关闭窗口，这样文字检查点也被参数化了

3  执行并分析使用参数的测试脚本
执行测试脚本： 点击工具栏上的 “Run” 按钮， 开启 Run 对话窗口， 选取 “New run results 
folder” ，其余为默认值，点击“OK”开始执行脚本。当脚本运行结束后，会开启测试结果
窗口。
在 树视 图 中 ， 展 开 “ Parameter  It eration2  >Action1  Summary  >Wel come  Mercury 
Tours>Fli ght Confirmation: Mercury ” ，选择“Checkpoint＂New  Y ork＂” ，显示如下图：
![](http://charisma.u.qiniudn.com/QQ20131114161344.png "检查点1")


在检查点“Details”窗口中，显示 Portland 为预期记过同时也是实际的值，所以文字检
查点为通过。同时也可以看到在下方的“Application”窗口中，显示机票的出发地点也是
Portland。