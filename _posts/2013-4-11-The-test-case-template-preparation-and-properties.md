---

layout : post

category : 测试

tags : [测试用例和性能模板编写 ]

title : 测试用例和性能模板编写

---


测试用例和性能模板编写
    功能测试用例
        用例的编写规则
            [用例编号：系统英文简称+功能模块的拼音缩写+编号，如“系统管理”：WMS-XTGL-01； 用例名称：采用“测试项-测试子项（或测试主题）”的方式] 
        测试用例的详细编写
            编写的目的
                测试XXX系统中XXXX模块在正常或异常情况下做某个业务所出现的或可能出现的情况或结果
            测试条件
                1、准备好相关可以参照的文档。2、准备好测试要用到的相关数据以及系统的基础数据。3、了解系统的业务逻辑及功能点。
            测试过程
                详细描述要测的某个系统中某个模块中的某个功能
                    例如：系统的登陆模块
                        1、正常情况：启动客户端软件，在用户登录界面输入正确的用户名，密码和数据库名，点击“登陆”。
                        2、异常情况：1.启动客户端软件，在用户登录界面输入不匹配的用户名和密码，输入正确的数据库名，点击“登陆”。 2.启动客户端软件，在用户登录界面输入正确的用户名和密码，输入不正确的数据库名，点击“登陆”。 
            期望结果
                1．	与测试过程要一一对应；  
                2 ．	期望的结果数据要描述清楚；
                3．	结果检查点要描述准确，并可以执行。
            测试结果
                通过或失败
            对测试结果的总结性或建议
                如：那个地方用户体验不是很友好，那个地方有XXXX需要改进
            日期时间
                2013-XX-XX
            测试人签字
                XXXX
            用例编号：用例名称
        项目概要
            项目名称：XXXXX
            项目版本：XXX0.1P
            项目负责人：XXXX
            测试负责人：XXXX
            测试工程师：XXXX
        项目简介
            [XXX项目的简要介绍，包括项目背景、系统架构、测试环境和测试注意事项等。]
    性能测试用例
        测试目的
            书写测试目的
            测试点1； 
            	测试点2； 
        测试场景设计：
            1．	写清测试条件；
            2．	涉及具体数据的测试条件，要描述清具体的数据；
            3．	测试条件中涉及的数据，它的操作由来不需要描述。
        测试工具：
            说明使用的测试工具信息。
        测试过程 : 
            详细描述测试执行过程；测试工具的使用过程不必细写。
        期望结果:
            期望结果描述清楚
        对测试结果的总结性或建议
            如：系统遇到的瓶颈问题，怎么解决，解决方法
        日期时间
            2013-XX-XX
        测试人签字
            XXXX
        用例编号：用例名称
