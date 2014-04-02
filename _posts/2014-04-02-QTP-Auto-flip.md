---

layout : post

category : 测试

tags : [QTP   自动翻页]

title : 实例--利用QTP实现自动翻页测试源码

---


If Browser("---XXXXXXX系统----").Window("-- 网页对话框").Exist(2)    Then
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter( "name")).Image("alt:=后一页").Click  '翻到第二页
     wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=最后页").Click  '翻到最后页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=后一页").Click '最后一页再次后翻到达第一页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=后一页").Click  '翻到第二页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=前一页").Click  '翻到第一页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=前一页").Click  '第一页向前翻，翻到最后页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=最后页").Click ' 翻到最后一页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).WebList("class:=select0").Select"2"
    wait(1)
    Browser("---XXXXXXX系统----").Window("-- 网页对话框").Page("Page").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
    
     else if Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Exist(2) then
     
         Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click
         wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=最后页").Click  '翻到最后页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click '最后一页再次后翻到达第一页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click  '翻到第二页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=前一页").Click  '翻到第一页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=前一页").Click  '第一页向前翻，翻到最后页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=最后页").Click ' 翻到最后一页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).WebList("class:=select0").Select"2"
        wait(1)
        Browser("---XXXXXXX系统----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
       else if Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Exist(2)  then
                 Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click
                 wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=最后页").Click  '翻到最后页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click '最后一页再次后翻到达第一页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=后一页").Click  '翻到第二页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=前一页").Click  '翻到第一页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=前一页").Click  '第一页向前翻，翻到最后页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=最后页").Click ' 翻到最后一页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).WebList("class:=select0").Select"2"
                wait(1)
                Browser("---XXXXXXX人员----").Window("---XXXXXXX---- -- 网页对话框").Page("---XXXXXXX----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                    
             else
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=后一页").Click  '翻到第二页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=最后页").Click  '翻到最后页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=后一页").Click '最后一页再次后翻到达第一页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=后一页").Click  '翻到第二页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=前一页").Click  '翻到第一页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---电话1203456789-------XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=前一页").Click  '第一页向前翻，翻到最后页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=最后页").Click ' 翻到最后一页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---XXXXXXX系统----").Frame(Parameter("name")).WebList("class:=select0").Select"2"
                       wait(1)
                       Browser("---XXXXXXX系统----").Page("---XXXXXXX系统----").Frame(Parameter("name")).Image("alt:=第一页").Click  ' 翻到第一页
                              
End if
End if
End if
