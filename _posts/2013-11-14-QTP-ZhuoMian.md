---

layout : post

category : QTP

tags : [自动化测试，QTP]

title : QTP录制桌面托盘图标

---


   今天闲来没什么事，QTP号称能在Window下是什么都可以录制的，如是我就想那桌面下的通知图标能录制吗？
查了资料后才知答案是肯定，在没查资料的情况下，我的答案是否定的，因为我试了很多次，都没成功，于是不心甘的在网上查找资料
   还别说，真的找到了，按照网上的资料还真的可以，可以录制桌面下方的通知图标
首先，由于录制不了所以需要手工添加对象 点击Resouces->Object Repositry 在弹出窗体的菜单中选择add object to local
然后点击托盘位置，这样托盘对象就可以捕获了。
编辑代码如下
For i=1 to Window("Window").WinToolbar("通知区域").GetItemsCount
aa=Window("Window").WinToolbar("通知区域").GetItemProperty(i,"name")
print aa
     if aa = "1" Then
         Window("Window").WinToolbar("通知区域").Press i,micLeftBtn
        Window("Window_2").Click 162,33
        wait(3)
        
        Window("test(QQ:123456789)").Close
        Exit for
        End If
        
Next



