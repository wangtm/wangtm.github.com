---

layout : post

category : manage

tags : [python 平板文件]

title : Python学习笔记之中文注释

---

# Python学习笔记之中文注释

    新手在刚开始写python的时候，都会碰到中文乱码问题
    通常，python源代码必须完全由ASCII集合组成，如果直接在python中添加中文注释的时候，python执行时会引发异常，告知非ASCII字符语法错误。  
    错误如下： SyntaxError: Non-ASCII character '/xd5' in file D:/Project/python/sort/quick_sort.py on line 9, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details  
     这个时候的解决方法，就是在告知python使用的编码方式，告知方法是在源文件的初始部分，也就是顶行加上这样一行注释，必须是这一行，否则不起作用！  
     必须在开头要加上这一行 # -*- coding: utf-8 -*


    这行注释的格式必须与这个保持严格一致，在coding和-*-之间，输入python已知的字符编码方式，比如utf-8或iso-8859-1.  
