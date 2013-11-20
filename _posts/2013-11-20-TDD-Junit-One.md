---

layout : post

category : 测试驱动开发

tags : [测试，测试驱动开发]

title : 测试驱动开发之Junit

---

    测试驱动开发(TDD)是极限编程(XP)的重要特点，它是以持续性的测试来推动代码的开发，即可以简化代码，又可以保证质量。它改变了先编写代码，后编写测试，而是先编写测试，然后在编写代码来满足测试的方法。这样使得测试工作不仅仅是单纯的测试，而成为了设计的一部分
    主要内容是介绍JUnit的使用
JUnit快速入门：         
    需求：需要一个工具类，可以实现2个数的加、减、乘、除四个功能。我们给这个类起名叫CalculateUtil。

    import iunit.framework.TestCase; //1
    public class CalculateUtilTest extent TestCase
    {
         public void testCreate()//2
         {
			new CalculateUtilTest();//3
         }
    }

注释：1行：导入JUnit必须的类
	  2行：任何一个测试类必须继承一个TestCase类。测试类的类名方法：被测试类类名+Test
	  3行：测试类的测试方法，所有的测试方法都必须以test单词开头，并且方法的返回类型是void

这里我们编写一个CalculateUtil类，为了使测试通过，我们下面就开始编写。
public class CalculateUtil
{
}

我们再次运行会发现这次就成功了。
下面我们对最上面的代码就行优化，你会发现会更神奇，O(∩_∩)O~

import junit.framework.TestCase;     
public class CalculateUtilTest extends TestCase     
{      
	public void testCreate()                    //1行     
	{       
	CalculateUtil ca=new CalculateUtil();           
    assertEquals(5, ca.add(3,2));             //2行        
    } 
}  
代码注释：
 1行：测试类的方法必须以单词test开头 
 2行：assertEquals()方法。以assert单词开头的方法就是JUnit测试框架中的断            言方法。比如assertEquals(5, ca.add(3,2)); 方法就是断言ca的add(3,2)方          法返回的结果等于5。如果add(3,2)返回5那么测试成功，否则测试失败。              运行测试类，这时测试失败。那么向CalculateUtil中添加代码来保证测试成功：

 这时再去运行的话会发现又出错了哇！

 我们在向CalculateUtil类中添加点代码：
public class CalculateUtil     
{     
	public int add(int numOne,int numTwo)     
	{      
	return numOne+numTwo;
	}
}
为了验证add方法是否是真的返回两个数的相加的结果，我们继续在添加一行测试代码： assertEquals(7, ca.add(4,2));

下面把后的除、乘、减给补充上去：
import junit.framework.TestCase;     
public class CalculateUtilTest extends TestCase    
{     
public void testCreate()    
{      
CalculateUtil ca=new CalculateUtil();    
assertEquals(5, ca.add(3,2));
}
public void testDivision()
{      
CalculateUtil ca=new CalculateUtil();  
assertEquals("两个数相除", 2,ca.division(4, 2));  //1行 
}
} 
代码解释：        
1行：assertEquals("两个数相除", 2,ca.division(4, 2));和前面assertEquals方法    
为了使测试通过，就要在CalculateUtil类中添加一个division方法。代码如下：

 public class CalculateUtil
 {      
	 public int add(int numOne,int numTwo)    
 		{    
 			return numOne+numTwo;     
 		} 
 	public int division(int numOne,int numTwo)   
  		{    
  		 return numOne/numTwo;  
  		 }    
} 



