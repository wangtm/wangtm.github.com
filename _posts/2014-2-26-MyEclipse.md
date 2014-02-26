---

layout : post

category : manage

tags : [MyEclipse]

title : 如何修改MyEclipse的默认工作路径Workplace

---

为了把现有的MyEclipse的工作目录（有众多工程）与新的项目分开。我需要重新开辟一个工作空间。但原有的Workplace已经被系统绑定，找了半天也不知道怎么设置回可提示选择工作区。
终于通过Google发现一个论坛中有一个回复，照着去做果然管用。
方法很简单，找到MyEclipse的安装目录后在其MyEclipse 6.5\eclipse\configuration\.settings\目录下，找到org.eclipse.ui.ide.prefs文件，编辑之：
原文件内容如下：
#Mon Aug 25 09:14:34 CST 2008
RECENT_WORKSPACES_PROTOCOL=3
MAX_RECENT_WORKSPACES=5
SHOW_WORKSPACE_SELECTION_DIALOG=false
eclipse.preferences.version=1
RECENT_WORKSPACES=D\:\\Myproject
将其中的SHOW_WORKSPACE_SELECTION_DIALOG=由false改成true。其他项都不要改，保存。
重新启动MyEclipse，哈哈，系统启动后提示你选择工作目录，这个时候就可以选择新的工作目录了。真是会者不难啊。
运行后的配置文件发生了变化：
#Mon Nov 10 13:40:40 CST 2008
RECENT_WORKSPACES_PROTOCOL=3
MAX_RECENT_WORKSPACES=5
SHOW_WORKSPACE_SELECTION_DIALOG=true
eclipse.preferences.version=1
RECENT_WORKSPACES=D\:\\springjob\nD\:\\Myproject
注：如果在myeclipse快捷方式启动中，设置了另一个工作空间，如"C:\Program Files\MyEclipse 5.5 GA\eclipse\eclipse.exe" -data "D:/workspace_sf" -clean -vm "C:\Program Files\MyEclipse 5.5 GA\jre\bin\javaw.exe"，
而你现在的项目是D:/workspace，则还是会以快捷方式中设置的空间来启动。