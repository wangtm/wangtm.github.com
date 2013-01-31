---

layout : post

category : manage

tags : [python   python  平板文件]

title : Python类的基础入门知识

---
# Python类的基础入门知识

关于类的定义
复制代码 代码如下:

class Account(object): 
"一个简单的类" 
account_type="Basic" 
def __init__(self,name,balance): 
"初始化一个新的Account实例" 
self.name=name 
self.balance=balance 
def deposit(self,amt): 
"存款" 
self.balance=self.balance+amt 
def withdraw(self,amt): 
"取款" 
self.balance=self.balance-amt 
def inquiry(self): 
"返回当前余额" 
return self.balance 

其中，__init__函数就是Python中的构造函数。另外，balance这个变量是类实例的变量。 
另外，在python中类中定义成员函数一般第一个参数总是self，表示自已的实例，与C++中的this指针差不多，不过C++中的this指针是隐函于其中并全局可见的，而在Python中却要作为参数传进去， 这是Python中定义类的另一个特点。 
还有一个特点，在类的成员函数中，使用类中的另一个成员函数，前面必须要指定类名，如下： 
复制代码 代码如下:

class Foo(object): 
def bar(self): 
print "bar!" 
def spam(self): 
bar(self) # 错误,引发NameError， 可以是：self.bar 
Foo.bar(self) # 合法的 

2.在类中声时静态方法并使用静态方法 
复制代码 代码如下:

class SimClass(): 
@staticmethod 
def ShareStr(): 
print "This is a static Method" 
SimClass.ShareStr() #使用静态函数

3.类方法： 
类方法与普通的成员函数和静态函数有不同之处，在接触的语言中好像也没见过这种语义，看它的定义： 
一个类方法就可以通过类或它的实例来调用的方法, 不管你是用类来调用这个方法还是类实例调用这个方法,该方法的第一个参数总是定义该方法的类对象。 
记住:方法的第一个参数都是类对象而不是实例对象. 
按照惯例,类方法的第一个形参被命名为 cls. 任何时候定义类方法都不是必须的（类方法能实现的功能都可以通过定义一个普通函数来实现,只要这个函数接受一个类对象做为参数就可以了）. 
定义类方法并使用类方法： 
复制代码 代码如下:

class ABase(object): 
@classmethod #类方法修饰符 
def aclassmet(cls): print 'a class method for', cls.__name__ 
class ADeriv(ABase): pass 
bInstance = ABase( ) 
dInstance = ADeriv( ) 
ABase.aclassmet( ) # prints: a class method for ABase 
bInstance.aclassmet( ) # prints: a class method for ABase 
ADeriv.aclassmet( ) # prints: a class method for ADeriv 
dInstance.aclassmet( ) # prints: a class method for ADeriv 

也就是说，类方法并不是必须的，使用普通函数也可以实现类方法的功能。 
4.类的继承 
在python中，继承一个类，就像这样： 
class A(object) #继承object类 
＃....... 
class B(A) #继承A类 
#........ 
另外，python中支持多继承，对于多继承，找某个对应的函数，其python有相应的方法，如： 
复制代码 代码如下:

class D(oject): pass #D继承自object 
class B(D): #B是D的子类 
varB = 42 
def method1(self): 
print "Class B : method1" 
class C(D): #C也是D的子类 
varC = 37 
def method1(self): 
print "Class C : method1" 
def method2(self): 
print "Class C : method2" 
class A(B,C): #A是B和C的子类 
varA = 3.3 
def method3(self): 
print "Class A : method3"

如果我要调用A.method1() ，会出现什么结果？答案是ClassB:method1. 书上是只样介绍的： 
当搜索在基类中定义的某个属性时，Python采用深度优先的原则、按照子类定义中的基类顺序进行搜索。**注意**（new-style类已经改变了这种行为）。上边例子中，如果访问 A.varB ,就会按照A-B-D-C-D这个顺序进行搜索，只要找到就停止搜索.若有多个基类定义同一属性的情况,则只使用第一个被找到属性值: 
5.数据隐藏 
在python中实现数据隐藏很简单，不需要在前面加什么关键字，只要把类变量名或成员函数前面加两个下划线即可实现数据隐藏的功能，这样，对于类的实例来说，其变量名和成员函数是不能使用的，对于其类的继承类来说，也是隐藏的，这样，其继承类可以定义其一模一样的变量名或成员函数名，而不会引起命名冲突。 
复制代码 代码如下:

class A: 
def __init__(self): 
self.__X = 3 # self._A__X 
class B(A): 
def __init__(self): 
A.__init__(self) 
self.__X = 37 # self._B__X





