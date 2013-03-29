---

layout : post

category : manage

tags : [thinkphp中的方法 ]

title : thinkphp中的方法

---

#thinkphp中方法

C操作
操作(动态)配置: 主要用于Action方法里面
获取:
C('配置参数')
设置:
C('配置参数 ',新值)

A操作
快速创建Action对象:
$action = A('User');
等效于
$action = new UserAction();

D操作
快速创建模型数据对象:
$model = D('User');
等效于
$model = new UserModel();

S操作
快速操作缓存方法
获取:
S('name')
设置:
S('name','value');
删 除:
S('name',NULL);

F操作
快速文件数据保存方法
使用方法与S操作一样


L操作
快速操作语言变量
获取:
L('语言变量');
设置:
L('语言变量','值');
如: L('USER_INFO','用户信息'); //设置名称为USER_INFO的语言变量
批量赋值:
$arr['语言变量1'] = '值1';
$arr['语言变量2'] = '值2';
L($arr);